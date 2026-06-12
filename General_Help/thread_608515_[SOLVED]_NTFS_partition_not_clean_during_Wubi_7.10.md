---
title: "[SOLVED] NTFS partition not clean during Wubi 7.10 rev385 install"
date: 2007-11-10
forum: General Help
---

### Post by Kinetic-Echo on 2007-11-10
Yesterday evening i tried installing Ubuntu 7.10 with the Wubi Installer rev385. All seemed to work fine until the "Partitioning Software" window showed up, the progress bar reachs the 100% and then the program returns an error message saying that the NTFS partition is not clean and I must run chkdsk /r under windows.

I have done a chkdsk /f in both regular and safe mode and no problems were found, in fact i'm able to install Feisty with the appropriate version of Wubi.

I would give further informations if i could, but i'm quite a novice and don't know how to help.


p.s. sorry for my bad english :P

---

### Post by anon2243 on 2007-11-10
I got the same error and in order to fix the problem I went under windows...right-clicked the drive in question, selected properties, selected tools and clicked 'check now' under the error checking box...then I said fix file system errors and rebooted...when no problems were found I reselected the Ubuntu menu item and the install went perfectly.

---

### Post by Kinetic-Echo on 2007-11-10
Misteries of Information Technology? :D

I'll try as soon as i get back home from office (yep, working on saturday is a pain ;))

---

### Post by Kinetic-Echo on 2007-11-10
Negative.

Tried AGAIN to do HD checks,  in windows and in safe mode, same problem, when the ubuntu installer starts it says the "NTFS Partition is not clean" although it contains no error.

Wubi 7.04 Installer works fine instead, and i can install, boot and run Feisty Fawn without problems.:confused:

---

### Post by anon2243 on 2007-11-10
did the disk error checker ask if u wanted to schedule the disk check on next boot? It might matter if the error checker ran before the os is loaded.

---

### Post by Kinetic-Echo on 2007-11-10
I did both, before and after OS was loaded.

---

### Post by anon2243 on 2007-11-10
sorry I can't help you any further...doing the above fixed it for me :(

---

### Post by doubleblack on 2007-11-11
I have this problem too, have tried countless times and my Windows Partition is fine <_<

I've also tried running chkdsk /f numerous times, to no prevail...

---

### Post by ago on 2007-11-11
Wubi uses ntfsresize --info, and that may fail if NTFS is flagged as dirty, even though most errors there can be ignored without much consequence. I have disabled the error warning for now (rev386). I am not too convinced about it, but we'll see how it goes.

---

### Post by doubleblack on 2007-11-12
I am typing this from WITHIN Ubuntu 7.10 installed using Wubi :)

Build 386 worked like a charm, no error messages.  I did receive a little notification saying SWAP file was not going to be created, but I have 4GB of RAM anyway so it wasn't a huge concern...

Anyway, not sure about the SWAP file and if that's intended or anything - but it said I could create one manually, but I just clicked SKIP and everything worked great.  I've restarted twice, goes to my install every time.

This is the SECOND problem I've had where it's been reported and relatively quickly fixed, thanks so much guys!  This is the FIRST time I've been able to install Wubi and it's AMAZING!

---

### Post by ago on 2007-11-12
> **doubleblack said:**
> 
Build 386 worked like a charm, no error messages.  I did receive a little notification saying SWAP file was not going to be created, but I have 4GB of RAM anyway so it wasn't a huge concern...


Send me /var/log/syslog if that happens again

---

### Post by doubleblack on 2007-11-12
Can I still send that to you now, or do I need to install again in order to get it?

(Sorry, I'm a n00b)

---

### Post by ago on 2007-11-12
it should be under /var/log/installer (if memory serves me well)

---

### Post by adromidon on 2007-11-12
Swap partitions are generaly a good idea to have it is like a page file on a windows system. However unlike Windows a Linux system can run without one but the performance may degrade if you run it for a long period of time and use programs that use excessive memory such as Gimp.

If you use Ubuntu occationaly and not all the time you may be able to get away with no swap file

---

### Post by doubleblack on 2007-11-12
Okay, here's my /installer/

:)

---

### Post by Kinetic-Echo on 2007-11-12
inally i'm posting on an Ubuntu 7.10 based system... running through Wubi on my PC :D

Installation completed, got a working system in no time and without errors.

Thanks for prompt support Ago :wink:

---

