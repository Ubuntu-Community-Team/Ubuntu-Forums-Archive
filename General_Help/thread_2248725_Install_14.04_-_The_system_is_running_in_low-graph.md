---
title: "Install 14.04 - The system is running in low-graphics mode"
date: 2014-10-16
forum: General Help
---

### Post by Dmitry_Samokhin_Ic on 2014-10-16
Last night i tried to install Ubuntu and made a big mistake by formatting full HDD instead of C partition. I fixed all with testdisk. Somehow ubuntu on USB got corrupted and i had to install Windows again to make sure my files are really back and to make new Ubuntu USB Install. Now everything is fine except that i can not install ubuntu, it gives me error **The system is running in low-graphics mode.**

I tried to boot with nomode instead of quaite splash (or something like that) but no luck.

 The system is running in low-graphics mode is showing in both cases (Try ubuntu and Install ubuntu)
When i try to edit config or load generic drivers it has no effect at all and if i chose Run in low graphic mode for one session my screen just gets black and nothing happens.

Intel Dual Core E2500 (2.5Ghz)
Nvidia 8400GF 512mb
Flash drive has 16gb but only ~4gb for changes (Universal USB installer didnt allow more)
HDD Some WD 320gb

---

### Post by ajgreeny on 2014-10-16
I think the nomodeset boot option always gives you low graphics mode (I have never needed it, so I'm not certain about that) but it should allow you to install the appropriate driver using "Additional Drivers" from the dash.

---

### Post by Dmitry_Samokhin_Ic on 2014-10-17
No idea about nomode, searched and found that as some answers to same/similar problem, tried it and it does not help.
Problem is that even with nomode i dont see Additional drivers anywhere.

By the way, im not able to download drivers as im using 3g usb modem to connect to internet, and im not able to configure it and connect because of these error...

---

### Post by ponsaravanan on 2014-10-20
just login to the console by pressing ctrl+alt+f5 
*) login as root
*) check df -h
 if it shows 100 % 
then delete some files upto it becomes 60 %
that's it it works!!!!!

---

### Post by Rob Sayer on 2014-10-20
> **ponsaravanan said:**
> just login to the console by pressing ctrl+alt+f5 
*) login as root
*) check df -h
 if it shows 100 % 
then delete some files upto it becomes 60 %
that's it it works!!!!!

Do *not* do that again.  It doesn't have anything to do with the OP's question anyway.  Deleting files at random is a very good way to break your system.

In fact, do not *ever* log in as root again until you have some idea what you're doing.  I started learning unix almost 30 years ago and I've never even created a root password in ubuntu.  In large unix/linux systems typically the system administrator is the only person who has a root password.  For good reason.  The last thing noobs should be doing is doing CLI stuff at root level.

---

