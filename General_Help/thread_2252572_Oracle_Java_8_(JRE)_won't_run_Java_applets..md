---
title: "Oracle Java 8 (JRE) won't run Java applets."
date: 2014-11-12
forum: General Help
---

### Post by omelette on 2014-11-12
Hi.  Working with Ubuntu 10.04 (don't ask!) I have successfully installed Oracle's Java 8 after following [this]("https://sites.google.com/site/easylinuxtipsproject/java") tutorial.  Running Oracle's java test via Firefox, I am informed that the latest & greatest Java has been successfully installed.

However, when I double-click a Java applet, 'javaws' fails to run the applet, throwing up the error **"unable to launch the application"**, adding in 'Details' the error **"Error: Could not parse launch file.  Error at line 0"**.  Further detail is available under the 'Wrapped Exception' tab, which shows the following;

> Failed to find the '<' charater that marks the end of a CDATA element. Exception parsing xml at line 0
	at com.sun.deploy.xml.XMLParser.skipPCData(Unknown Source)
	at com.sun.deploy.xml.XMLParser.nextToken(Unknown Source)
	at com.sun.deploy.xml.XMLParser.parse(Unknown Source)
	at com.sun.javaws.jnl.XMLFormat.parse(Unknown Source)
	at com.sun.javaws.jnl.XMLFormat.parse(Unknown Source)
	at com.sun.javaws.jnl.LaunchDescFactory.buildDescriptor(Unknown Source)
	at com.sun.javaws.jnl.LaunchDescFactory.buildDescriptor(Unknown Source)
	at com.sun.javaws.Main.launchApp(Unknown Source)
	at com.sun.javaws.Main.continueInSecureThread(Unknown Source)
	at com.sun.javaws.Main.access$000(Unknown Source)
	at com.sun.javaws.Main$1.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:745)


Like I said, Java appears to work perfectly in Firefox, but not at all when trying to run applets directly. Has anyone come across this before?

---

### Post by omelette on 2014-11-16
Figured it out.  'javaws' won't run local Java applications, you need to use the form** 'java -jar myjava_app.jar'**.  The included '-jar' option is essential.

---

