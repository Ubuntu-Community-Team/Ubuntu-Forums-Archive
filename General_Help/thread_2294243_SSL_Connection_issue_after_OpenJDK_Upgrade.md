---
title: "SSL Connection issue after OpenJDK Upgrade"
date: 2015-09-10
forum: General Help
---

### Post by Peter_Thompson on 2015-09-10
Running Ubuntu 12.04.5 LTS on an Amazon EC2 instance

Dear all,

I'm running Tomcat on the above server and have just performed a package update for OpenJDK (see version information below). After the update, when one of my Tomcat webapps attempts an HTTPS connection I get the following error in the Tomcat log. The only thing that has changed is the OpenJDK update. Has anyone else experienced this issue and have a resolution?

Thanks,

Pete

Error:
Caused by: javax.net.ssl.SSLPeerUnverifiedException: peer not authenticated
        at sun.security.ssl.SSLSessionImpl.getPeerCertificates(SSLSessionImpl.java:421)
        at org.apache.http.conn.ssl.AbstractVerifier.verify(AbstractVerifier.java:126)
        at org.apache.http.conn.ssl.SSLSocketFactory.connectSocket(SSLSocketFactory.java:437)
        at org.apache.http.impl.conn.DefaultClientConnectionOperator.openConnection(DefaultClientConnectionOperator.java:180)
        at org.apache.http.impl.conn.ManagedClientConnectionImpl.open(ManagedClientConnectionImpl.java:294)
        at org.apache.http.impl.client.DefaultRequestDirector.tryConnect(DefaultRequestDirector.java:643)
        at org.apache.http.impl.client.DefaultRequestDirector.execute(DefaultRequestDirector.java:479)

Tomcat verison: 7.0.26

Java version before the upgrade:
java version "1.7.0_79"
OpenJDK Runtime Environment (IcedTea 2.5.5) (7u79-2.5.5-0ubuntu0.12.04.1)

Java verison after the upgrade:
java version "1.7.0_79"
OpenJDK Runtime Environment (IcedTea 2.5.6) (7u79-2.5.6-0ubuntu1.12.04.1)

---

