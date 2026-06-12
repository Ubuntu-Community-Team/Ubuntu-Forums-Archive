---
title: "Where oh where has Frostwire gone?"
date: 2007-09-26
forum: General Help
---

### Post by kulturloseramerikaner on 2007-09-26
Last update caused my Frostwire install to go dead, launcher didn't do a thing.  I tried reinstalling, and now it's gone, and not showing up in the repositories any more.  Did I lose a repository; if so, how do I ound out which one and replace it?  If not, why was it removed?  I've tried using apt and Synaptic to get it back w/ no luck.

---

### Post by rsambuca on 2007-09-26
Just download the .deb from the website.

---

### Post by kulturloseramerikaner on 2007-09-26
Whoa, that makes WAY too much sense. :)

---

### Post by kulturloseramerikaner on 2007-09-26
Done; launcher STILL won't work.  What now?

---

### Post by rsambuca on 2007-09-26
Open a terminal and type 

frostwire

---

### Post by kulturloseramerikaner on 2007-09-26
Did that too, gave me an error.  
EDIT: 
OK, it's squawking about not finding JAVA runtime, but I have version 6 installed according to Synaptic
brian@HAL:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
brian@HAL:~$

Looks like the version updated. If I also reinstall 5, it'll create conflicts, won't it?

---

### Post by rsambuca on 2007-09-27
Just re-install java and you should be fine.

---

### Post by kulturloseramerikaner on 2007-09-27
Reinstalled both; no love.  It's kicking out the same error about JRE.

---

### Post by rainwalker on 2007-09-27
Check out [http://ubuntuforums.org/showthread.php?t=305337](http://ubuntuforums.org/showthread.php?t=305337)
That's what I followed when I had trouble with FW, you'll just have to change the commands to get the version you want

---

### Post by kulturloseramerikaner on 2007-09-28
Gave it a try; still spitting out that same error.

---

### Post by santiagoward2000 on 2007-09-28
Just to be sure, do you have these pakages installed?
java-common
sun-java6-bin
sun-java6-jdk
sun-java6-jre
sun-java6-plugin

---

### Post by kulturloseramerikaner on 2007-09-28
I went through them one-by-one with apt, and wouldn't you know it, I didn't have the jdk package.  The bummer is that installing it did not solve the problem; I get the same errors.](*,)

---

### Post by kulturloseramerikaner on 2007-10-02
Any other ideas folks?

---

### Post by kulturloseramerikaner on 2007-10-05
Evidently there is something wrong with the Java Runtime Environment that's in the repos; I got sick of it telling me that I didn't have a valid JRE and went to the Sun Java website to get the source.  I unpacked and installed it from there, and everything seems to be working now.  Just curious - is anyone else having that problem?

---

### Post by Dark Aspect on 2007-10-06
> **kulturloseramerikaner said:**
> Evidently there is something wrong with the Java Runtime Environment that's in the repos; I got sick of it telling me that I didn't have a valid JRE and went to the Sun Java website to get the source.  I unpacked and installed it from there, and everything seems to be working now.  Just curious - is anyone else having that problem?
I had the same error for a while but I did not use the package off Sun Java's website.I just ignored the problem and it fixed itself after a few updates:)

---

### Post by kulturloseramerikaner on 2007-10-06
Must've been nice! :) Mine never did after all the updates, but it's working now, so it's all good.

---

