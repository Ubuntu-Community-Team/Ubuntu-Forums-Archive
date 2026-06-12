---
title: "Which JRE"
date: 2008-04-15
forum: General Help
---

### Post by JemW on 2008-04-15
Just to make sure I don't screw up (again!), can someone please confirm:

I have Ubuntu 7.10 32bit, with Swiftweasel 2.0.0.13. Flash is installed but I need:

1) The correct choice from Add/Remove to install the latest JRE and browser plugin, or a Terminal command to achieve this (sorry, I'm new to Linux)

2) Your best recommendation for viewing - WMP, Realplayer and Quicktime content.

Many Thanks!

---

### Post by kpkeerthi on 2008-04-15
Check [this]("http://ubuntuforums.org/showthread.php?t=661833") out

---

### Post by JemW on 2008-04-15
That has to be the most confusing page I've ever looked at. Thanks anyway...

---

### Post by myforumlogin on 2008-04-15
1) FOR JRE :

Follow this link [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)
Choose  Linux (self-extracting file)  filesize: 18.83 MB 
Follow instructions 

2) FOR VIEWING MEDIA :

I prefer Totem Movie Player, Kaffeine and VLC Media Player

Good Luck 
Seb.

---

### Post by JemW on 2008-04-15
> **myforumlogin said:**
> 1) FOR JRE :

Follow this link [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)
Choose  Linux (self-extracting file)  filesize: 18.83 MB 
Follow instructions 

2) FOR VIEWING MEDIA :

I prefer Totem Movie Player, Kaffeine and VLC Media Player

Good Luck 
Seb.

Where did you install Java? It says "For example /usr/java..." but Ubuntu won't  let me create that directory. Is there a recommended location from the Ubuntu developers?

---

### Post by myforumlogin on 2008-04-15
Open a terminal with root privileges. ( Use SUDO or SU & your password) then just type *mkdir /usr/local/java*

This will create the folder in an accessible location for all users and applications. 
Copy the zipped file you downloaded to this folder and unzip it there.
In order to copy the file manually go to the folder the file is downloaded to. 
For example if its on the desktop, type *cd /home/YOURUSERNAME/Desktop*
then *cp FILENAME /usr/local/java*

The rest is in the instructions. If stuck write back.

Seb.

---

### Post by forrestcupp on 2008-04-15
If you need the Java Runtime Environment, all you need to do is install it from the repos
```
sudo apt-get install sun-java6-plugin
```

You do need to have your universe and multiverse repos enabled, though.  Go to System->Administration->Software Sources and in the Ubuntu Software tab, make sure all the boxes are checked.

---

### Post by jespdj on 2008-04-15
> **myforumlogin said:**
> 1) FOR JRE :

Follow this link [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp)
Choose  Linux (self-extracting file)  filesize: 18.83 MB 
Follow instructions
**No!** Just install it from the Ubuntu repository as forrestcupp says:
```
sudo apt-get install sun-java6-plugin
```
You should always prefer software from the Ubuntu repository, because that's the officially tested version for Ubuntu, so you have a good chance that it works properly and is integrated into the system correctly, and it will be updated automatically if your computer checks for software updates.

If you manually download and install Java from Sun's website, you are circumventing Ubuntu's package management system, and you won't get automatic security updates.

---

### Post by JemW on 2008-04-15
> **forrestcupp said:**
> If you need the Java Runtime Environment, all you need to do is install it from the repos
```
sudo apt-get install sun-java6-plugin
```

You do need to have your universe and multiverse repos enabled, though.  Go to System->Administration->Software Sources and in the Ubuntu Software tab, make sure all the boxes are checked.
 
Including the Source Code box? (Currently has a horizontal line in it)

---

### Post by jespdj on 2008-04-15
> **JemW said:**
> Including the Source Code box? (Currently has a horizontal line in it)
No, you don't need the source code.

---

### Post by JemW on 2008-04-15
> **jespdj said:**
> No, you don't need the source code.

Thank you - that worked! Your views on the best media player for Real & WMP Streaming? (Quicktime occasionally for movie previews). More instructions on how to install the best for this would be very much appreciated!

(Swiftweasel on Ubuntu 32 bit)

---

### Post by wrecche on 2008-04-15
It wont work for me, I get this -

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate


*sigh* always HATED messing trying to get java to work with ubuntu.. argh.

---

### Post by oldos2er on 2008-04-15
Make sure all your repositories are enabled; System, Administration, Software Sources.

---

