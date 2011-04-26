# New ports collection makefile for:	pwgrp
# Date created:	28 April 2010
# Whom:		Stefan Miklosovic <miklosovic@gmail.com>
#
# $FreeBSD$
#

PORTNAME=	pwgrp
PORTVERSION=	1.0
CATEGORIES=	sysutils
MASTER_SITES=   http://devio.us/~stewe/projects/pwgrp/

MAINTAINER=	miklosovic@gmail.com
COMMENT=	Utility used to create users en mass

NO_BUILD=	yes
WRKSRC=		${WRKDIR}/${PORTNAME}

MAN8=		pwgrp.8

OPTIONS=        APG "Include support for password generation" On \
		SETQUOTA "Include support for quotas" On

.include <bsd.port.pre.mk>

RUN_DEPENDS=

.if defined(WITH_APG)
RUN_DEPENDS=	apg:${PORTSDIR}/security/apg
.endif

.if defined(WITH_SETQUOTA)
RUN_DEPENDS+=	setquota:${PORTSDIR}/sysutils/setquota
.endif

do-install:
	${INSTALL_SCRIPT} ${WRKSRC}/pwgrp ${PREFIX}/sbin

post-install:
	${MKDIR} ${DATADIR}
	${INSTALL_DATA} ${WRKSRC}/common.subr ${DATADIR}
	${INSTALL_DATA} ${WRKSRC}/LICENCE ${DATADIR} && \
	(cd ${WRKSRC} && ${COPYTREE_BIN} templates ${DATADIR})

	${INSTALL_MAN} ${WRKSRC}/doc/pwgrp.8 ${MANPREFIX}/man/man8

.include <bsd.port.post.mk>
