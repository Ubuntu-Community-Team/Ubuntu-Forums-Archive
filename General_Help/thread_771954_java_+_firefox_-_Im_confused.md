---
title: "java + firefox - Im confused"
date: 2008-04-28
forum: General Help
---

### Post by jvels on 2008-04-28
Hi

I have just install a new clean Ubuntu 8.04, but I can't use my homebank (use applet tol logon). In Ubuntu 7.10 there where no problems.
I have read alot about java+firefox+hardy

What is the recipe to have java in a version of firefox(I do not care if it is version 2 or 3) ,and also can use Netbeans?

/Jesper

---

### Post by arm-c on 2008-04-28
Check out my link and my experiences with getting back to functioning FireFox with Java.

[http://ubuntuforums.org/showthread.php?t=770089](http://ubuntuforums.org/showthread.php?t=770089)

---

### Post by jvels on 2008-04-28
Hi

Yesterday I tryed to remoce openjdk (I also have netbeans installed), but netbeans need openjdk.

How du i use netbeans with sun jdk?

/Jesper

---

### Post by Mr Frosti on 2008-04-28
Netbeans has an installation option that lets you specify which JDK environment to use. I pointed this to the default path of the Sun JDK (version 1.6). 

I do not see this option anywhere in the Netbeans options, so I tried uninstalling the program to see if it prompted me for a new location. To my amazement, it started as normal, even without the JDK. Worst case scenario, Netbeans has an "uninstall.sh" script inside its root directory (if you downloaded the source)

---

### Post by jvels on 2008-04-28
I installed netbeans for add/remove software (or was it from synaptic...)

But there in the install there where no option for chooceing witch jdk to use....?

/Jesper

---

### Post by arm-c on 2008-04-28
I am sorry.  I have to bump.  You may want to start new threat with question about netbeans so it is seen.  Presently your issue is hidden under Java and Firefox.

---

### Post by kavon89 on 2008-04-28
> **jvels said:**
> Hi

I have just install a new clean Ubuntu 8.04, but I can't use my homebank (use applet tol logon). In Ubuntu 7.10 there where no problems.
I have read alot about java+firefox+hardy

What is the recipe to have java in a version of firefox(I do not care if it is version 2 or 3) ,and also can use Netbeans?

/Jesper

Head for the Synaptic Package Manager and Update/Refresh it. Then search for sun-java6 and install the JRE/JDK. Also remember to pick up sun-java6-plugin for firefox support.

Then head for the NetBeans website and download the latest stable, which should be 6.0.1, and install it. It should automatically choose to use the latest JDK verison you have installed, but I remember it allowing me to point it to another JDK folder during install. I'm not sure how you change it to another version after it's installed though.

---

