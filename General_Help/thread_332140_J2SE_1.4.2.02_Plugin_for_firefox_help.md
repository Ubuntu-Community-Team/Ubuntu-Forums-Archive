---
title: "J2SE 1.4.2.02 Plugin for firefox help"
date: 2007-01-05
forum: General Help
---

### Post by jxmccall on 2007-01-05
Hi Everyone,
 I am new to linux ( so If I sound stupid... well ) I have installed ubuntu 6.10. What I am attempting to do is run Oracle Applications with firefox 2.0. When I attempt to run the forms it needs to use java and I get the following message:

"In order to access this application, you must install the J2SE Plugin version 1.4.2_04 on your client and NPX_PLUGIN_PATH environment variable is set before starting Netscape"

when I do about:plugins in firefox I see 

Java(TM) Plug-in Blackdown-1.4.2-02

    File name: libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_08 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_08 	Java 		Yes


Any help would be welcomed.

Jeff

---

### Post by shivathreya on 2007-09-12
Why do you use blackdown java? Are you running AMD64?

If so install firefox 32BIT and then install j2re 6.0.

THen edit $HOME/.mozilla/firefox/pluginreg.dat

Under JAVA TM plugins increase the line count by 1. If it is "32" change to "33".

Then scroll down and in the last line after 31 add "32:application/x-java-applet;version=1.4.2_04:Java::$"

Then restart Firefox. It should work.

Shiva

---

### Post by blee1170 on 2008-01-23
I know this is kind of a old post, but I am having the same issue.  

I did edit the plugin.dat so it has the 1.4.2_04, but it still is not working for me.

Anyone have another idea to try?

---

### Post by johnap on 2008-02-23
> **blee1170 said:**
> I know this is kind of a old post, but I am having the same issue.  

I did edit the plugin.dat so it has the 1.4.2_04, but it still is not working for me.

Anyone have another idea to try?

I am also facing the same problem.

need solution

---

