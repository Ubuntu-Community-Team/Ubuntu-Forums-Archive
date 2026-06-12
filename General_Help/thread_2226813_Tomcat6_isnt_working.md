---
title: "Tomcat6 isnt working?"
date: 2014-05-29
forum: General Help
---

### Post by Danny_R on 2014-05-29
hello all

im messing about with Ubuntu 12.04 an have installed tomcat6, (i can reach the test/ default page "it works")

i have loaded an app onto tomcat, it worked, but i have since restarted ubuntu an now can access the app (can still access the test/ home page)

any ideas?

the log file - which i dont know has any bearing on the issue states

```
INFO: Starting Coyote HTTP/1.1 on http-8080
 
28-May-2014 13:56:17 org.apache.catalina.startup.Catalina start
INFO: Server startup 486 ms
 
28-May-2014 13:57:09 org.apache.coyote.http11.Http11Protocol pause
INFO: Pausing Coyote HTTP/1.1 on http-8080
 
28-May-2014 13:57:10 org.apache.catalina.core.StandardService stop
INFO: Stopping service Catalina
 
28-May-2014 13:57:10 org.apache.coyote.http11.Http11Protocol destroy
INFO: Stopping Coyote HTTP/1.1 on http-8080
 
28-May-2014 14:00:31 org.apache.catalina.startup.ClassLoaderFactory validateFile
WARNING: Problem with directory [/usr/share/tomcat6/server/classes], exists: [false], isDirectory: [false], canRead: [false]
 
28-May-2014 14:00:31 org.apache.catalina.startup.ClassLoaderFactory validateFile
WARNING: Problem with directory [/usr/share/tomcat6/server], exists: [false], isDirectory: [false], canRead: [false]
INFO: Starting Coyote HTTP/1.1 on http-8080
 
28-May-2014 13:56:17 org.apache.catalina.startup.Catalina start
INFO: Server startup 486 ms
 
28-May-2014 13:57:09 org.apache.coyote.http11.Http11Protocol pause
INFO: Pausing Coyote HTTP/1.1 on http-8080
 
28-May-2014 13:57:10 org.apache.catalina.core.StandardService stop
INFO: Stopping service Catalina
 
28-May-2014 13:57:10 org.apache.coyote.http11.Http11Protocol destroy
INFO: Stopping Coyote HTTP/1.1 on http-8080
 
28-May-2014 14:00:31 org.apache.catalina.startup.ClassLoaderFactory validateFile
WARNING: Problem with directory [/usr/share/tomcat6/server/classes], exists: [false], isDirectory: [false], canRead: [false]
 
28-May-2014 14:00:31 org.apache.catalina.startup.ClassLoaderFactory validateFile
WARNING: Problem with directory [/usr/share/tomcat6/server], exists: [false], isDirectory: [false], canRead: [false]

```

---

