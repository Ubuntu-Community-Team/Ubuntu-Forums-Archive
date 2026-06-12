---
title: "USAA Deposit@Home on Linux"
date: 2017-11-28
forum: General Help
---

### Post by feartheterrapin on 2017-11-28
I know this has been a challenge before which we all worked through.  But it keeps getting tougher.  With the recent upgrades I am locked out once again.  It seems I can’t even get Oracle Java recognized in my Ubuntu anymore as well.  Any help is appreciated.  Thanks.

---

### Post by QIII on 2017-11-28
Hello!

How did you install Oracle Java?

(Also remember that we are all shareholders in USAA and we can make phone calls!  I'm a 40 year member, so I have no problem with that, personally.  ;) )

---

### Post by feartheterrapin on 2017-11-28
Oracle Java was installed via the WEBUPD8TEAM PPA back when I first installed 16.04LTS.  See below why I  think something is wrong with the Oracle install.

```
~$ sudo update-alternatives --config java
[sudo] password for : 
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                            Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-8-oracle/jre/bin/java          1081      auto mode
  1            /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java   1081      manual mode
* 2            /usr/lib/jvm/java-8-oracle/jre/bin/java          1081      manual mode

Press <enter> to keep the current choice
[*], or type selection number: 
~$ java -version
java version "1.8.0_151"
Java(TM) SE Runtime Environment (build 1.8.0_151-b12)
Java HotSpot(TM) 64-Bit Server VM (build 25.151-b12, mixed mode)
~$ 
```

Not sure I understand recommendation calling USAA,  They have never supported a Linux OS for USAA Deposit@Home.  But I never had an issue with USAA Deposit@Home until the recent updates.  The USAA error is that my Java is outdated.

---

### Post by QIII on 2017-11-28
I call them periodically to bug them about Linux.

The latest Java 8 minor version is 152, so that may be it.  Not sure what Andrei's script is updating to.  I'll take a look after work.

Java 9.0.1 has also been released.

---

### Post by Yellow Pasque on 2017-11-28
Are you using Firefox? Maybe the upgrade to FF 57 caused issues, though I thought the Java plugin was unsupported in FF 52 or 53.

---

### Post by feartheterrapin on 2017-11-28
> **Temüjin said:**
> Are you using Firefox? Maybe the upgrade to FF 57 caused issues, though I thought the Java plugin was unsupported in FF 52 or 53.

So no Java in Windows version of FireFox either?

 I am using FireFox 57.0 and Chrome Version 62.0.3202.94.   

I thought everything was OK with v.52 & 53.  I last successfully used the site early August.

---

### Post by Yellow Pasque on 2017-11-28
Sorry, I missed the part where you said, "The USAA error is that my Java is outdated."

---

### Post by feartheterrapin on 2017-11-29
> **QIII said:**
> The latest Java 8 minor version is 152, so that may be it.  Not sure what Andrei's script is updating to.  I'll take a look after work.

Java 9.0.1 has also been released.

I could update to one or the other to confirm.  It makes sense this could be the issue.  I am thinking v8 is more mainstream, should I be patient for 152 (which was released mid October) or find a way to force the update?

---

### Post by QIII on 2017-11-29
Have a look at [https://sites.google.com/site/easylinuxtipsproject/java#TOC-How-to-for-Oracle-Sun-Java-JRE](https://sites.google.com/site/easylinuxtipsproject/java#TOC-How-to-for-Oracle-Sun-Java-JRE)

Go to the section specifically for Mint and Ubuntu.  You will want to repace 144 (or whatever) to 152, so take care to be observant.

Don't worry.  If you reinstall from webupd8 later it will work out.

Let us know if that works.

---

### Post by Yellow Pasque on 2017-11-29
It looks like 152 is 151 with additional features, but Oracle still considers 151 to be the latest. If it's really the case that USAA is explicitly checking for 152, you should contact them, because it's not a Linux specific problem. Oracle's Java download page also offers 151 to Windows users: [https://www.java.com/en/download/manual.jsp](https://www.java.com/en/download/manual.jsp)

Actually, I'm confused why USAA is still using Java (and how you're still using it). From what I saw on their site, they ended support for their Java-based Secure Login a couple years ago.

---

### Post by QIII on 2017-11-29
I've gone rounds with them on this ever since the October of Java Exploits.  Sigh.

---

### Post by 1clue on 2017-11-29
> **feartheterrapin said:**
> So no Java in Windows version of FireFox either?

 I am using FireFox 57.0 and Chrome Version 62.0.3202.94.   

I thought everything was OK with v.52 & 53.  I last successfully used the site early August.

This was announced like a year and a half ago.

Firefox*** on every platform*** no longer supports nsapi, because there are too many stability and security problems with it.

Speaking as someone who has been programming code to run inside the java virtual machine for the last 20 years or so, it's a good thing that client-side java inside the browser is going away.

There is a version of firefox which supports java plugins until 2018 some time. I suspect that the final version of IE will continue to be used for the next 60 years or so, which means that some version of the java plugin may also work.

Other than that, I don't know of any mainstream browser which will continue to support the java plugin.

For more information, start reading at [https://java.com/en/download/installed8.jsp](https://java.com/en/download/installed8.jsp)

---

### Post by feartheterrapin on 2017-11-29
Alright, I think I got it, USAA rejects Linux.  I confirmed today that they no longer use Java.  I did not get a good answer why they still check for Java, but they promised an answer.  I installed a user agent plug in, configured as Windows Firefox, all went well.  Why they intentionally reject Linux I have no idea, but I know this is the wrong forum to go further.

---

### Post by QIII on 2017-11-29
Wonder if they realize they are using Linux servers ...

No.  Never mind.  They don't.  I've been through this with them.

---

