---
title: "Wubi is not working"
date: 2007-11-20
forum: General Help
---

### Post by hydraconsole on 2007-11-20
I'm trying on a different way to install edubuntu on my system and was excited to hear that i can do it even while i'm on Windows.

The wubi installation worked perfectly.
i rebooted the computer.
i found the dual-boot selection.
but when i choose Ubuntu, it justs installs it again.
then it tries to find the installation iso (which wubi already downloaded).
I used the option to automatically search for the iso file but it can't seem to find anything even though i know that it is in my 2nd partition of my hard drive.

help me!

---

### Post by ago on 2007-11-20
It might be the wrong ISO
What version of Wubi/ISO are you using?

---

### Post by hydraconsole on 2007-11-20
i downloaded wubi 7.04.04 from wubi-installer.org.
I wanted to try out Edubuntu 7.04 which was the only version on the drop down menu of wubi. Wubi downloaded the edubuntu-7.04-alternate-i386.iso. This is the only version available from wubi.

---

### Post by ago on 2007-11-20
Those are correct.
Do you have any error message? Where exactly does it stop.

---

### Post by hydraconsole on 2007-11-21
installing additional components. it seems to be looking for the installer from a cd. but i didn't use the live cd or alternate download. i used wubi.
i know that wubi completed the iso download and i even did a hash check with the md5sum and it was ok.

---

### Post by ago on 2007-11-21
> **hydraconsole said:**
> installing additional components. it seems to be looking for the installer from a cd. but i didn't use the live cd or alternate download. i used wubi.
i know that wubi completed the iso download and i even did a hash check with the md5sum and it was ok.

You can press alt+f4 for additional info

---

### Post by hydraconsole on 2007-11-21
> **ago said:**
> You can press alt+f4 for additional info

alt+f4 when i get the error message? 

is there a log file that records this error? how do i access it?

---

### Post by ago on 2007-11-22
the log is in /var/log/syslog

You access it by using alt+f2 then using the cat, less or nano commands to read it

---

### Post by hydraconsole on 2007-11-22
i'm now using gutsy gibbon. i got tired of trying to solve this wubi installation and just went ahead and bought a cd-rom, downloaded the alternate cd iso, burned the iso using my neighbor's cd writer, installed ubuntu, cooked supper, and voila, i'm using it right now.
i'm so new at this that i'm still trying to figure how to use it. boy do i have a lot to learn. more questions coming up soon.

thanks for the help though. i really appreciate it.

---

