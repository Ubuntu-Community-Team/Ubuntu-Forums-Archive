---
title: "Tomcat: error when starting applications"
date: 2007-10-23
forum: General Help
---

### Post by jfisbein on 2007-10-23
Since I upgraded from Feisty to Gutsy none of my application deployed on Tomcat works anymore.
When I try to start the applications they generate an error.

here is the catalina log:
-- begin log --
[FONT="Courier New"]Oct 23, 2007 3:05:01 PM org.apache.catalina.core.AprLifecycleListener lifecycleEvent
INFO: The Apache Tomcat Native library which allows optimal performance in production environments was not found on the java.library.path: 
Oct 23, 2007 3:05:01 PM org.apache.coyote.http11.Http11BaseProtocol init
INFO: Initializing Coyote HTTP/1.1 on http-8180
Oct 23, 2007 3:05:01 PM org.apache.catalina.startup.Catalina load
INFO: Initialization processed in 742 ms
Oct 23, 2007 3:05:01 PM org.apache.catalina.core.StandardService start
INFO: Starting service Catalina
Oct 23, 2007 3:05:01 PM org.apache.catalina.core.StandardEngine start
INFO: Starting Servlet Engine: Apache Tomcat/5.5
Oct 23, 2007 3:05:01 PM org.apache.catalina.core.StandardHost start
INFO: XML validation disabled
Oct 23, 2007 3:05:02 PM org.apache.catalina.startup.HostConfig deployWAR
INFO: Deploying web application archive APPMaruja.war
Oct 23, 2007 3:05:02 PM org.apache.catalina.loader.WebappClassLoader validateJarFile
INFO: validateJarFile(/var/lib/tomcat5.5/webapps/APPMaruja/WEB-INF/lib/servlet-api.jar) - jar not loaded. See Servlet Spec 2.3, section 9.7.2. Offending class: javax/servlet/Servlet.class
Oct 23, 2007 3:05:02 PM org.apache.catalina.core.StandardContext start
SEVERE: Error listenerStart
Oct 23, 2007 3:05:02 PM org.apache.catalina.core.StandardContext start
SEVERE: Context [/APPMaruja] startup failed due to previous errors
Oct 23, 2007 3:05:02 PM org.apache.coyote.http11.Http11BaseProtocol start
INFO: Starting Coyote HTTP/1.1 on http-8180
Oct 23, 2007 3:05:02 PM org.apache.jk.common.ChannelSocket init
INFO: JK: ajp13 listening on /0.0.0.0:8009
Oct 23, 2007 3:05:02 PM org.apache.jk.server.JkMain start
INFO: Jk running ID=0 time=0/25  config=null
Oct 23, 2007 3:05:02 PM org.apache.catalina.storeconfig.StoreLoader load
INFO: Find registry server-registry.xml at classpath resource
Oct 23, 2007 3:05:03 PM org.apache.catalina.startup.Catalina start
INFO: Server startup in 1681 ms
Oct 23, 2007 3:05:56 PM org.apache.catalina.loader.WebappClassLoader validateJarFile
INFO: validateJarFile(/var/lib/tomcat5.5/webapps/APPMaruja/WEB-INF/lib/servlet-api.jar) - jar not loaded. See Servlet Spec 2.3, section 9.7.2. Offending class: javax/servlet/Servlet.class
Oct 23, 2007 3:05:56 PM org.apache.catalina.core.StandardContext start
SEVERE: Error listenerStart
Oct 23, 2007 3:05:56 PM org.apache.catalina.core.StandardContext start
SEVERE: Context [/APPMaruja] startup failed due to previous errors
[/FONT]-- end log ---

as you can see tomcat starts correctly but when I try to deploy any of the aplicactions (APPMaruja) I get an error.
I didn't see more information in any other log file.


All is comented in my /etc/default/tomcat5.5

[FONT="Courier New"]$java -version
java version "1.5.0_13"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_13-b05)
Java HotSpot(TM) Server VM (build 1.5.0_13-b05, mixed mode)
[/FONT]

[FONT="Courier New"]$ javac -version
javac 1.5.0_13
[/FONT]

If you need more info don't hesitate in asking me.


P.S: sorry for my english but i'm not a native speaker.

---

### Post by sgordon on 2007-10-26
Not sure if the upgrade has added some more .jars into your classpath, or the upgrade in tomcat has caused this issue to surface, but:

servlet-api.jar should **not** be deployed with your webapps (within the .war) file. This .jar will already be available in the tomcat/common/lib folder.

It could be that the servlet-api.jar you are supplying is out of date, or the new tomcat deployed (upgraded to 5.5?) is checking for the .jar being supplied in the webapp.

Anyhow, upshot is, remove servlet-api.jar from your webapps and try a redeploy. Let me know how it goes!

  Si

---

