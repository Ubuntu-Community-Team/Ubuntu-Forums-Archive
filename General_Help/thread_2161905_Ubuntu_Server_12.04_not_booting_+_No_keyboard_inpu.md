---
title: "Ubuntu Server 12.04 not booting + No keyboard input possible"
date: 2013-07-12
forum: General Help
---

### Post by anXieTyPB on 2013-07-12
Hello there!

I have a server running 12.04 x64 ubuntu server edition. It suspends automatically when it is not used and gets woken up when a computer needs it. 
This worked pretty well until today. I tried booting but i just saw a black screen, CTRL-ALT-Fx didnt help. So i tried to reboot into recovery mode, and I get a timeout saying "Gave up waiting for root device".

Sadly, I cannot use the command prompt to invesitage further. It recognizes my keyboards properly but I can not use them. They work properly at GRUB-Selection and in BIOS.

My system is running on a raid 1 with 2*1 TB Harddrives. See the following paste for further information about grub and disc configuration:

[http://paste.ubuntu.com/5868053/](http://paste.ubuntu.com/5868053/)

Any suggestions? I already tried to repair Grub with Boot-Repair and i was able to successfully mount the software-raid using a live CD environment.

---

### Post by anXieTyPB on 2013-07-13
The following error is shown when using recovery boot:

Gave up waiting for root device. Dropping to a shell.

Any help?

---

### Post by anXieTyPB on 2013-09-11
I found the solution a while ago. 

Problem was that the initramfs configuration went completely wrong. It used module paths that do not exist so I had to manually recreate it by using an older kernel and using the correct module paths. 

Everything worked as expected afterwards.

---

