---
title: "Open Office 2.4 and Java"
date: 2008-06-28
forum: General Help
---

### Post by Rog-Mahal on 2008-06-28
First things first, I'm running Hardy 64 bit with the 2.6.24-19 kernel. 

I'm not sure if there was an update that messed something up or what, but open office does not register that I have a jre. I've tried to do some searching and manually enter the correct path to it, but so far I haven't found something that it will accept. Has anyone had a similar problem or know what path I should enter? Right now open office just randomly tanks sometimes, especially if I copy certain things from the internet. Any help would be greatly appreciated.

---

### Post by scouser73 on 2008-06-29
Hardy comes with 'OpenJava' and not Sun Microsystems JRE as one would like. The Sun Microsystems version of Java is in the repos; sun-java6-jre.

This should help sort the problem out.

---

### Post by Rog-Mahal on 2008-06-29
Thanks for the info, do you know if installing the sun java will conflict with open jdk?

---

### Post by scouser73 on 2008-06-30
If you have both of the Java versions installed there will be no conflict between the two, I know this from my own experiences when I became aware of Openjava that wouldn't work properly with openoffice and websites that required Sun Microsystems Java

---

### Post by jamesstansell on 2008-06-30
> **scouser73 said:**
> Hardy comes with 'OpenJava' and not Sun Microsystems JRE as one would like. The Sun Microsystems version of Java is in the repos; sun-java6-jre.

This should help sort the problem out.

Just for the record, it is called OpenJDK, and it _is_ Sun's Java released as Free Software.  The bits that are different are where Sun didn't have the right to re-license parts and they've been replaced with parts from the Classpath project.  It continues to improve - Fedora just released a slightly newer version than Hardy has, which passes all of the Java compatibility tests.

The main difference is that Sun didn't release the browser plugin or Java Webstart code, and I have looked in vain for where they might release them in the future.  I guess the compatibility tests don't include those parts.

Of course those parts aren't used by OpenOffice.org either so shouldn't be causing the problem in this thread.  There have been crashing reports for Java on x86_64 but I thought those were mostly sun-java6.  Perhaps OpenOffice.org doesn't trigger them?

---

### Post by Anzan on 2008-06-30
Just to note that I find that turning the Java runtime environment off helps OO.o run much faster.

---

