---
title: "Ubuntu Crash"
date: 2008-01-15
forum: General Help
---

### Post by MarcosDurrant on 2008-01-15
I have an older Dell Inspiron laptop that I have been running 7.10 on for a while now and I haven't had any real problems.  Last night the screen went all black and frooze.  So I rebooted and it won't boot now.  I have gotten a grub #18 error (I think that is it) and if I can actually get past the grub it just won't finish loading - it will just hang.  I have tried to boot off my 7.10 live CD and it won't do it - I even tried to do the OEM install and it keeps getting stuck.  I just loaded Puppy on a CD and that loaded up.  Any suggestions as to what to do?  I want to get Ubuntu back and up and running, I am going to try to boot off of a Hardy Heron Alpha 3 Live CD...  Is there a way to save everything I had and just do a "repair" install??

---

### Post by sumguy231 on 2008-01-15
Oddly enough, Error 18 apparently has to do with the BIOS not being able to access the part of the hard drive needed to boot. This shouldn't affect the LiveCD so I guess that problem is unrelated. 

You could rescue the data on the system using another LiveCD (like the Puppy one) and then use the alternate install CD to install a fresh system. Get it from the download page by checking the little checkbox towards the bottom:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

In the future, you might consider putting /home on a separate partition so if something weird happens again you can install the system without wiping all the data.

---

