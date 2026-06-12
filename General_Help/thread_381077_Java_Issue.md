---
title: "Java Issue"
date: 2007-03-10
forum: General Help
---

### Post by ShareBuntu on 2007-03-10
Hey folks,

I noticed in my Internet menu (under the K menu) there are two entries for Java. Sun Java 5.0 Web Start and Sun Java 6 Web Start.

Is it possible that both versions 5 and 6 are somehow installed? I went for the jdk and the jre. Any ideas as to how I can rectify this dilemma?

---

### Post by azteech on 2007-03-10
I also have the same situation. Though I do know I 1st installed java 5 and the associated jre. I then upgraded to java 6.

From a terminal window, when I enter 

java -version 

I get the following output:

java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

In looking at the output, I believe I only have java 6 installed. But, i believe the applications menu entry for java 5 did not get removed.

Can anyone shed some light?

---

### Post by ShareBuntu on 2007-03-10
> **azteech said:**
> I also have the same situation. Though I do know I 1st installed java 5 and the associated jre. I then upgraded to java 6.

From a terminal window, when I enter 

java -version 

I get the following output:

java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

In looking at the output, I believe I only have java 6 installed. But, i believe the applications menu entry for java 5 did not get removed.

Can anyone shed some light?

Strange, my output is:

java version "1.5.0_11"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_11-b03)
Java HotSpot(TM) Client VM (build 1.5.0_11-b03, mixed mode, sharing)

I wonder where the 6 came from? Any ideas on upgrading?

---

### Post by phossal on 2007-03-10
You can have multiple JRE's and JDK's installed on your system. For example, not only can you have JRE 5.0 and JRE 6.0, or JRE 5.0 and JDK 6.0, but you can have JDK 6.0 (#1) and JDK 6.0 (#2). 

However, only *one* is typically setup to run at any time. To make the situation more confusing, if you have multiple JDK's installed, you might be *running* Java 5.0, and *Java Web Start 6.0*, because the invocations might access different JDK's. 

As you probably know, your system is typically configured to use the first available path when you invoke a command. The paths are typically managed by update-alternatives (almost always true if you install packages). 

How can you tell which java you're using? *java -version*
Which JDK? *javac -version*
Which Java Web Start? *javaws -version*

Are they always correct? No. But it's a start.

If you used a package manager to install multiple JDK's, you can use it to get *rid* of them. Then you can install the latest and greatest directly from SUN using their .bin file.

---

### Post by ShareBuntu on 2007-03-11
> **phossal said:**
> You can have multiple JRE's and JDK's installed on your system. For example, not only can you have JRE 5.0 and JRE 6.0, or JRE 5.0 and JDK 6.0, but you can have JDK 6.0 (#1) and JDK 6.0 (#2). 

However, only *one* is typically setup to run at any time. To make the situation more confusing, if you have multiple JDK's installed, you might be *running* Java 5.0, and *Java Web Start 6.0*, because the invocations might access different JDK's. 

As you probably know, your system is typically configured to use the first available path when you invoke a command. The paths are typically managed by update-alternatives (almost always true if you install packages). 

How can you tell which java you're using? *java -version*
Which JDK? *javac -version*
Which Java Web Start? *javaws -version*

Are they always correct? No. But it's a start.

If you used a package manager to install multiple JDK's, you can use it to get *rid* of them. Then you can install the latest and greatest directly from SUN using their .bin file.

Thanks for the response. I'll have to look into this a bit. It really is annoying trying to make one version standard across your system but it also makes sense from a development perspective to have multiple versions.

I'll post an update on my progress. :)

---

