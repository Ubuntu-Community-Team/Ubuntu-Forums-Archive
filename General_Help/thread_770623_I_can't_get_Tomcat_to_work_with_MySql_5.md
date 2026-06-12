---
title: "I can't get Tomcat to work with MySql 5"
date: 2008-04-27
forum: General Help
---

### Post by scorpio2002 on 2008-04-27
Hi there! I'm experiencing issues with tomcat and mysql. I loaded an simple servlet that tries to connect to MySql and an exception is thrown. There's the stack trace:

com.mysql.jdbc.SQLError.createCommunicationsException(SQLError.java:1070)
com.mysql.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:2103)
com.mysql.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:718)
com.mysql.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:298)
com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:282)
java.sql.DriverManager.getConnection(DriverManager.java:525)
java.sql.DriverManager.getConnection(DriverManager.java:171)
Search.doGet(Search.java:21)
javax.servlet.http.HttpServlet.service(HttpServlet.java:689)
javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
java.lang.reflect.Method.invoke(Method.java:585)
org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:243)
java.security.AccessController.doPrivileged(Native Method)
javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:272)
org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:161)
org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFilterChain.java:245)
org.apache.catalina.core.ApplicationFilterChain.access$0(ApplicationFilterChain.java:177)
org.apache.catalina.core.ApplicationFilterChain$1.run(ApplicationFilterChain.java:156)
java.security.AccessController.doPrivileged(Native Method)
org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain.java:152)
org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java:214)
org.apache.catalina.core.StandardValveContext.invokeNext(StandardValveContext.java:104)
org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:520)
org.apache.catalina.core.StandardContextValve.invokeInternal(StandardContextValve.java:198)
org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java:152)
org.apache.catalina.core.StandardValveContext.invokeNext(StandardValveContext.java:104)
org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:520)
org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:137)
org.apache.catalina.core.StandardValveContext.invokeNext(StandardValveContext.java:104)
org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:118)
org.apache.catalina.core.StandardValveContext.invokeNext(StandardValveContext.java:102)
org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:520)
org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:109)
org.apache.catalina.core.StandardValveContext.invokeNext(StandardValveContext.java:104)
org.apache.catalina.core.StandardPipeline.invoke(StandardPipeline.java:520)
org.apache.catalina.core.ContainerBase.invoke(ContainerBase.java:929)
org.apache.coyote.tomcat5.CoyoteAdapter.service(CoyoteAdapter.java:160)
org.apache.coyote.http11.Http11Processor.process(Http11Processor.java:799)
org.apache.coyote.http11.Http11Protocol$Http11ConnectionHandler.processConnection(Http11Protocol.java:705)
org.apache.tomcat.util.net.TcpWorkerThread.runIt(PoolTcpEndpoint.java:577)
org.apache.tomcat.util.threads.ThreadPool$ControlRunnable.run(ThreadPool.java:684)
java.lang.Thread.run(Thread.java:595)

any clue?

---

### Post by Orion99 on 2008-04-27
Hello,

Are you using the JODBC connector for Java? If not you must download the file from [www.mysql.com](www.mysql.com), unpack and put the jar at common or share directory of tomcat.

Let me now if works...

---

### Post by scorpio2002 on 2008-04-27
Unfortunatelly that's not the problem. The mysql jconnect is available.. I put it everywhere... in commmon/lib, $JVM/lib/ext, $my_servlet_dir/WEB-INF/lib... that doesn't seem to be the problem.

I guess, the real problem is that he packages coming with ubuntu are configured in such a way that prevent mysql and tomcat servlets to communicate... I can't see any other reason...

---

