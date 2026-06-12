---
title: "pljava problem? or Linux problem?"
date: 2008-03-01
forum: General Help
---

### Post by yaloveda on 2008-03-01
Hi everybody,

I've have been struggling with this problem for close to 2 weeks now and can't figure out where to find the answer, I searched the forums and googled the internet for anything, but no result.

I'm trying to install PLjava with postgresql database, but each time I try to install it, it give me this error:

/opt/pljava# java -cp postgresql.jarljava.jar:deploy.jar org.postgresql.pljava.deploy.Deployer -database adempiere -user ***** -password ***** -install


org.postgresql.util.PSQLException: ERROR: could not load library "/opt/pljava/pljava.so": /opt/pljava/pljava.so: undefined symbol: SetUserId
at org.postgresql.core.v3.QueryExecutorImpl.receiveEr rorResponse(QueryExecutorImpl.java:154
at org.postgresql.core.v3.QueryExecutorImpl.processRe sults(QueryExecutorImpl.java:1316)
at org.postgresql.core.v3.QueryExecutorImpl.execute(Q ueryExecutorImpl.java:191)
at org.postgresql.jdbc2.AbstractJdbc2Statement.execut e(AbstractJdbc2Statement.java:452)
at org.postgresql.jdbc2.AbstractJdbc2Statement.execut eWithFlags(AbstractJdbc2Statement.java:337)
at org.postgresql.jdbc2.AbstractJdbc2Statement.execut e(AbstractJdbc2Statement.java:329)
at org.postgresql.pljava.deploy.Deployer.initJavaHand lers(Deployer.java:474)
at org.postgresql.pljava.deploy.Deployer.main(Deploye r.java:269)
--------------------------------------------------------------------------------------------------------------------

I've installed postgresql 8.2 , JDK 6 , (java 1.6) , on a Ubuntu 7.04 (no upgrades or anything like that)

I'm doing this to install Adempiere ERP, but so far this PLJAVA problem is preventing me from doing so.
I used the following page as my guide to install Adempiere:

[http://www.posterita.org/mediawiki/i..._for_ADempiere](http://www.posterita.org/mediawiki/i..._for_ADempiere)

I installed Adempiere on Windows with relatively less problems, I'm new with Ubuntu and so far I installed it like 10 times just to try to figure out how to make Adempiere work on it.

Anybody have a clue?
Thanks everybody

---

### Post by zazuge on 2008-05-11
I dunno i have the same proble
but seems somone found out what's wrong > Apparently I built this pljava release against a server compiled with
--enable-cassert with it althought he built pljava for postgres-8.1
[http://www.nabble.com/Problem-PL-Java-installation-td16900782.html](http://www.nabble.com/Problem-PL-Java-installation-td16900782.html)
maybe i'll downgrade to postgres8.1.

---

### Post by zazuge on 2008-05-11
ouf finaly it worked with pljava from this link
[http://pgfoundry.org/frs/download.php/1597/pljava-i686-pc-linux-gnu-pg8.2-1.4.0.tar.gz](http://pgfoundry.org/frs/download.php/1597/pljava-i686-pc-linux-gnu-pg8.2-1.4.0.tar.gz)
hope that helps (if you didn't find it yet)

---

