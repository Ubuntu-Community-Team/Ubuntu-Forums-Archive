---
title: "Message: Java Runtime Environement 1.6 is required on your client..."
date: 2016-10-09
forum: General Help
---

### Post by yonnie on 2016-10-09
I get this error message and after checking with the package manager I'm coming up with blanks.  Is there something I can install to satisfy the problem?

---

### Post by QIII on 2016-10-09
Hello!

Could you give us a better explanation of what you are trying to do?

---

### Post by yonnie on 2016-10-09
trying to login to a piece of hardware via FireFox and I get the above message.  Client being my computer running Kubuntu.  Cannot get it to work, am thinking this is a windows(ms) issue, but maybe it's a java plugin I'm needing?

---

### Post by QIII on 2016-10-09
Hello!

I'm afraid that answer may have been more inscrutable than your first post.  It would be valid very helpful if you would provide solid details.

Why do you now suspect this is a Windows issue?

---

### Post by yonnie on 2016-10-09
Mostly, because openjdk-7-jre is installed and the device is posting an error!
where in the ubuntu repositories does it list a java runtime engine of 1.6 or greater?  or a just plain java runtime engine?  and don't most devices designed with java, run no-matter what, unless they have something specifically coded for a microsoft windows computer?  I can't remember how long it has been since I have seen an issue like this, not since MS got their pants sued off over 2 decades ago for writing their own java.  

I suspect this to be an MS issue because the message requests for something that would be normal for a windows machine.  And quite often, Linux has a work-around either builtin or handy to get at.  Here's the problem stated again: FireFox is attempting to run software on a device via ethernet and html connection to a remote device.  The remote device is responding with the above message: Java Runtime Environment 1.6 or greater is required on your client (client meaning this computer, my laptop).  The above message is pretty clear, I've seen it before using windows machines that were out of date.  Problem is, I'm not using a windows machine now, and I don't plan to ever again.

What we now know about the problem is: 1, it's a piece of hardware.  2, we talk to it via ethernet using FireFox.  3, the hardware complains about the FireFox because it needs Java Runtime Environment 1.6 running on my laptop.  4, we need something either through the FireFox as in a plugin, or we need something more from the world of JAVA running on the laptop.

I have tried Kubuntu 14.04 and Kubuntu 16.04 and Linux Mint 17.3 and Lubuntu 14.04.  All present this problem.  something is missing, what is it?

---

### Post by QIII on 2016-10-09
First, Java 6 is dead and its use is highly dangerous and not recommended.  It is vulnerable in dozens of ways.  If anything is demanding its use, you should not be using it.

Java 8 is the current recommended version.

You are still speaking in vague generalities without enough detail to begin to help.

---

### Post by The Cog on 2016-10-09
If you are talking to a piece of hardware that requires your browser to have java6 installed, and it checks that you have the java6 plugin and no other version, then you have no option other than to install the version 6 java plugin. That is, assuming you can find such an old version of that plugin somewhere. 

In my opinion, you should not use that browser to connect to anything other than the hardware that is forcing you this way, because of the security problems that come with java6. Either use a different browser for all your other browsing, or better still use a separate *buntu install inside a vm like virtualbox when you need to talk to this hardware. If the hardware is in warranty or under a support contract, perhaps you should have a moan at the manufacturers - I see no reason why it should disallow later versions of java.

We used to have some appliances like this where I work, but I am glad to say they have all been retired now.

---

### Post by QIII on 2016-10-09
Since you are giving general answers, the best I can do is give you general advice.

So.

Again:  If something is asking for Java 1.6, don't use it.  I feel obliged to be much more forceful than The Cog with reference to this.  A VM may protect *the system at your end* of the "conversation", but there is no guarantee that whatever you are doing is not exposed and exploited at one end or the other.

You can see what version of Java your machine is running by issuing:

```
java -version
```

Java is available in the repos as OpenJDK.  OpenJDK is the open source reference implementation for Oracle Java -- per Oracle's decision.  But before you get too excited, remember that the largest contributor to the OpenJDK project is Oracle.

You may also download and install Oracle Java.  The easiest way is to use the method [here]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html"). 

Oracle 6 (1.6) has been declared to be past its end of life and its use is dangerous.  Oracle 7 is still supported, but is a generation old.  Oracle 8 is the currently supported version.

---

### Post by yonnie on 2016-10-09
Thank you, 
I'm running Java version 1.7.0_111.  When I login to a device via FF and ask it to run a program from its own menu **it responds with :** "_Java Runtime Environment 1.6 (or above) is required on your client machine_"

 to start with I tried sudo apt-get install jre-7 blah blah and it came back with already installed.  Then I went into the package manager and installed a few more jre related stuff.  I've tried installing just about everything from synaptic package manager that seems to have anything to do with JRE and it's still not running. Since I'm using firefox, maybe it has something to do with that?  But what it is, I don't know.  I need someone who knows more about java and it's needs than I do (that would include most people who know what a keyboard is)

---

### Post by yonnie on 2016-10-09
sudo apt-get install icedtea-netx, seems to resolve the problem.  thank you

---

