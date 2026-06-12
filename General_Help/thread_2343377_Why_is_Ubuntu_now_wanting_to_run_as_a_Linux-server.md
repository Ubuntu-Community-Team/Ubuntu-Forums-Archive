---
title: "Why is Ubuntu now wanting to run as a Linux-server?"
date: 2016-11-15
forum: General Help
---

### Post by patrickdug on 2016-11-15
You can ignore this post.  I am following the other posts that deal with the same issue: Can't Log In.

First, I have little to no knowledge of Linux, I just run it on a spare desktop so I can run the Boinc and SETI software.  Until recently it was running just fine.  Every few days I turn on the screen, log in and check to see if it's running ok or if there are updates to run.  Today when I logged in the BOINC software would not run.  I exited and relaunched it to no avail.  Therefore I decided to reboot the computer.  When it booted up it wanted a 'Linux Server Login' at the command prompt.  Since I don't have that I did nothing, after 30 seconds it booted to the log-in screen displaying 'Linux-Server' in the upper left corner, something it had never done before.  When I try to log in using my user password, it reboots the login screen.  I am running the 16.04 LTS.

Trying to read through a bunch of tech speak posts makes my head hurt.  Is there a fix for this or do I run over it with the truck a few times?

---

### Post by patrickdug on 2016-11-15
Well update to this.  I have read several other posts that describe the same problem, can't log in.  After reading the posts very carefully, I tried to follow the indicated process to no avail.  Also, during this process I realized the 'Linux-Server' is the name of my computer! D'oh!

I tried holding down the Shift key during boot up, but it did nothing.  Using Cntl-Alt-F1 I was able to get to the command prompt where I worked through the process as described.  On re-boot it still asks for the login and password in the command prompt but it goes to fast for me to type in my password.  Is there a way to pause the process?

P.S.  I used to be an advanced computer programmer/user but after a severe concussion I am no longer able to program or concentrate on complex constructs.  I have a hard time playing solitaire now! :(

---

### Post by patrickdug on 2016-11-16
The solution turns out to be a purge of the nVidia drivers and rebooting the computer.  It will install the 'nouveau disply' driver which gets rid of the issues caused by the 304 nVidia driver.

---

