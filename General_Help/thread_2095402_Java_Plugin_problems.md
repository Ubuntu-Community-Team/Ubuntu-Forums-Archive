---
title: "Java Plugin problems"
date: 2012-12-16
forum: General Help
---

### Post by kaushikgaurav on 2012-12-16
I am using ubuntu 12.10 on X61 tablet.

I installed Java on my computer so that I could use some of the websites that require it and its plugins.

specifically the following are the software packages i installed:

1)OpenJDK Java 7 runtime
2)OpenJDK Java 7 policy tools 
3)IcedTea Web control Paner
4)IcedTea Java Browser Plugin
5)OpenJDK Java 6 Runtime 
6)IcedTea Java plugin
7)OpenJDK Java 6Policy tool

Now the problem is that everytime I try using the website (requiring java) it gives me error:
icedtea was blocked because it is out of date.

My system is up to date with most current software installed. 

This is my chrome plugin details

IcedTea - Version: [COLOR="Red"]1.3[/COLOR] Download Critical Security Update
The IcedTea-Web Plugin executes Java applets.
Name:	IcedTea-Web Plugin (using IcedTea-Web 1.3 (1.3-1ubuntu1.1))
Description:	The IcedTea-Web Plugin executes Java applets.
Version:	1.3
Location:	/usr/lib/jvm/java-7-openjdk-i386/jre/lib/i386/IcedTeaPlugin.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-java-vm	IcedTea	
.class	.jar
application/x-java-applet	IcedTea	
.class	.jar
application/x-java-applet;version=1.1	IcedTea	
.class	.jar
application/x-java-applet;version=1.1.1	IcedTea	
.class	.jar
application/x-java-applet;version=1.1.2	IcedTea	
.class	.jar
application/x-java-applet;version=1.1.3	IcedTea	
.class	.jar
application/x-java-applet;version=1.2	IcedTea	
.class	.jar
application/x-java-applet;version=1.2.1	IcedTea	
.class	.jar
application/x-java-applet;version=1.2.2	IcedTea	
.class	.jar
application/x-java-applet;version=1.3	IcedTea	
.class	.jar
application/x-java-applet;version=1.3.1	IcedTea	
.class	.jar
application/x-java-applet;version=1.4	IcedTea	
.class	.jar
application/x-java-applet;version=1.4.1	IcedTea	
.class	.jar
application/x-java-applet;version=1.4.2	IcedTea	
.class	.jar
application/x-java-applet;version=1.5	IcedTea	
.class	.jar
application/x-java-applet;version=1.6	IcedTea	
.class	.jar
application/x-java-applet;version=1.7	IcedTea	
.class	.jar
application/x-java-applet;jpi-version=1.7.0_50	IcedTea	
.class	.jar
application/x-java-bean	IcedTea	
.class	.jar
application/x-java-bean;version=1.1	IcedTea	
.class	.jar
application/x-java-bean;version=1.1.1	IcedTea	
.class	.jar
application/x-java-bean;version=1.1.2	IcedTea	
.class	.jar
application/x-java-bean;version=1.1.3	IcedTea	
.class	.jar
application/x-java-bean;version=1.2	IcedTea	
.class	.jar
application/x-java-bean;version=1.2.1	IcedTea	
.class	.jar
application/x-java-bean;version=1.2.2	IcedTea	
.class	.jar
application/x-java-bean;version=1.3	IcedTea	
.class	.jar
application/x-java-bean;version=1.3.1	IcedTea	
.class	.jar
application/x-java-bean;version=1.4	IcedTea	
.class	.jar
application/x-java-bean;version=1.4.1	IcedTea	
.class	.jar
application/x-java-bean;version=1.4.2	IcedTea	
.class	.jar
application/x-java-bean;version=1.5	IcedTea	
.class	.jar
application/x-java-bean;version=1.6	IcedTea	
.class	.jar
application/x-java-bean;version=1.7	IcedTea	
.class	.jar
application/x-java-bean;jpi-version=1.7.0_50	IcedTea	
.class	.jar
application/x-java-vm-npruntime	IcedTea	

Can someone tell me what is going on here and how can I fix this.

Thanks
Gaurav

---

### Post by Mopar1973Man on 2012-12-16
Well I'm going to take a stab at it. What I see is you mixing 1.6 and 1.7 Java together. You got to pick either one or the other 1.6 or 1.7. But you can't have both.

Now as for those Java programs I'm not to fond of so I went back to the original source and download a Linux copy of true Java and installed it. The trick is getting the plugin installed in Firefox. But it should be all there on there web site.

[http://www.java.com/en/download/linux_manual.jsp?locale=en](http://www.java.com/en/download/linux_manual.jsp?locale=en)

---

### Post by kaushikgaurav on 2012-12-16
runtime 6 in installed if you install 7 automatically.
I tried installing java [http://www.java.com/en/download/linu....jsp?locale=en](http://www.java.com/en/download/linu....jsp?locale=en), did everything install, configure etc, it did not work, that was the reason i tried installing icedtea.
With Java from sun or oracle the webpage does not even show that java is installed, with icedtea it does but gives the error message as i pointed above...

---

### Post by polki@mac.com on 2012-12-17
I run google-chrome with this command:

/opt/google/chrome/google-chrome --allow-outdated-plugins %U

It stopped chrome nagging about the outdated java-plugin.
I hope it helps you too.

---

### Post by Pjotr123 on 2012-12-17
> **kaushikgaurav said:**
> runtime 6 in installed if you install 7 automatically.
I tried installing java [http://www.java.com/en/download/linu....jsp?locale=en](http://www.java.com/en/download/linu....jsp?locale=en), did everything install, configure etc, it did not work, that was the reason i tried installing icedtea.
With Java from sun or oracle the webpage does not even show that java is installed, with icedtea it does but gives the error message as i pointed above...
You can install Oracle Java easily, if you apply this how-to:
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

Takes about 5 minutes. :)

---

### Post by kaushikgaurav on 2012-12-18
Ok,
That was some help, it did get me past that error message.
The page loads now but it gets unresponsive and I have to kill the process to be able to get back my system.

I am trying to download some articles from a peer reviewed journal site. 
To get multiple items at one time.
Earlier, I could not load the page because it said that the Icedtea plugin was outdated, but now whenever I try to download the content the page just freezes.

---

