---
title: "Java Dev using AppFuse"
date: 2006-08-15
forum: General Help
---

### Post by quyne on 2006-08-15
I'm having some problems to develop a Struts Site using AppFuse.

When trying to run tests (via Appfuse's ant test-all ) I get the following error :


Bootstrap: Class loader creation threw exception
java.lang.NoClassDefFoundError: org/apache/commons/logging/LogFactory
        at org.apache.tomcat.util.compat.JdkCompat.<clinit>(JdkCompat.java:55)
        at org.apache.catalina.startup.ClassLoaderFactory.<clinit>(ClassLoaderFactory.java:63)
        at org.apache.catalina.startup.Bootstrap.initClassLoaders(Bootstrap.java:103)
        at org.apache.catalina.startup.Bootstrap.init(Bootstrap.java:196)
        at org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:402)

This error occurrs during test-jsp target, while starting tomcat.

I know that it isn't a tomcat problem, since it runs perfectly (via /etc/init.d/tomcat5).  However, if I use another tomcat (installed in /opt), the script works.

The most obvious solution would be to use the /opt tomcat, but I haven't been able to figure how to set it to start as a service on boot.  That's why I use the tomcat found in the repositories.



Is there anyway to solve this ?

Thanks

---

