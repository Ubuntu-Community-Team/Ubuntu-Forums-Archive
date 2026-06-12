---
title: "HOW TO: gvSIG (GIS) on Ubuntu 7.10"
date: 2007-12-26
forum: General Help
---

### Post by Go_Bucks on 2007-12-26
A number of users of gvSIG (a GIS program) have noted problems with using the program properly on Linux systems with Compiz installed (GUI won't resize and certain dialogue boxes won't work). I spent weeks trying to find a solution for this, however, I did discover a discussion group the developers were on where they cited Java as the issue but didn't know whether the conflict was with their program or between Java and Compiz. This gave me an idea for a quick attempt at a solution and --to my surprise as a Linux newbie--it worked.

The issue with the program IS Java, specifically, the Java that installs in your home directory with the program. This is located at:

/home/<name>/gvSIG/jre/1.5.0_12

What you need to do is replace all of the Java files in this directory with the Java files that work on your system. On my system I have Java 1.6. These files are located at:

/usr/lib/jvm/java-6-sun-1.6.0.03/jre

Simply select all files in the second directory (the working Java), copy them, and paste over the files in the first directory. Voila! Your gvSIG should now work. 

This may also work on other programs that install their own Java instances.

---

### Post by K.Mandla on 2007-12-26
Moved to General Help.

---

