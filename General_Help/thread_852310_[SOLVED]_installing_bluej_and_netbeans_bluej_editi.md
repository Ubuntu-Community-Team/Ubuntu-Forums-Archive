---
title: "[SOLVED] installing bluej and netbeans bluej edition"
date: 2008-07-07
forum: General Help
---

### Post by terry f on 2008-07-07
Hi can some one help me install bluej and netbeans bluej edition.  I do know how to install them but when I do they get installed to my desktop or where ever I download them to.  How do I get them to install to where programs usually install to, where ever that is as I don't really know.

---

### Post by terry f on 2008-07-08
bump

---

### Post by The Cog on 2008-07-08
I dont know netbeans so I can't help there.

The .jar installer for bluej asks for an install directory before installing. So if you do:
**sudo java -jar bluejSomeVersion.jar**
you should be able to tell it to install anywhere.

---

### Post by terry f on 2008-07-08
never mind I fell like a real like a real dummy, I for some reason did not even try to install these, I just saw the .bin extension and figured that they would act like the other .bin files I have tried to install.  The other ones just dumped them selfs to the same directory the the .bin file was in.  All I really need to know now is where are user installed application suppose to be installed to, I know that does not really matter but I would like to know any ways.

---

### Post by The Cog on 2008-07-09
User installed apps need to go in your home directoy somewhere - choose your own place really. 

If you install apps for all users, they should probably go in directories under /opt or /usr/local. You need root rights (use sudo) to put them there because it's outside your home directory.

---

