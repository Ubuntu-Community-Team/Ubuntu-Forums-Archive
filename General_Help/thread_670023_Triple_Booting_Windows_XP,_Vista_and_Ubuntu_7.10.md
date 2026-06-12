---
title: "Triple Booting Windows XP, Vista and Ubuntu 7.10"
date: 2008-01-17
forum: General Help
---

### Post by slackdog on 2008-01-17
Hi there
I am a real newbie

Have Windows XP on one hd with Vista on 2nd hd.  Installed Ubuntu 7.10 on free space (30GB) on 2nd hd. Installation seems OK.

Problem is when I get the Windows Boot Manager screen to include Ubuntu using Easy BCD 1.7.1 but when clicking on "Ubuntu 7.10 kernel 2.6.22-14-generic" get following

Booting 'Ubuntu 7.10 kernel 2.6.22-14-generic'
root (hd1,2)
Error 27: No such partition
Press any key to continue...

The screen reverts back to the Windows Boot Manager.  How do I get into Ubuntu? Is there another way to get GRUB to work without using EasyBCD?

---

### Post by cdaringe on 2008-01-17
so i remember when i booted from MY other hard drive, the GRUB hard drive associations changed.  when you go to boot ubuntu in GRUB, hit e at the boot screen to edit the commands. and try editing it to like (hd0,2) or something. switch up the number following hd.  likely 0 is what you are after. write back. see if that does the trick

---

### Post by slackdog on 2008-01-17
Thanks cdaringe
It did the trick...except
I edited the root  (hd1,2) to (hd0,2 and press the enter key.........saves it to the GRUB4DOS screen.
That's fine, but on pressing b for boot, it will load Ubuntu....bewdy mate.
However on restarting the computer, the root command reverts back to (hd1,2).
How do I permanently save the edit to (hd0,2).
Your help much appreciated.

---

### Post by cdaringe on 2008-01-18
you got it man.
GRUB4DOS huh? hmm.
well, i can tell you that standard GRUB gets all of its startup info from a file called menu.lst.
its located in /boot/grub .to edit it, you just open a console, then sudo gedit /boot/grub/menu.lst .
if not sure if GRUB4DOS accesses this or has its own config files. im assuming its a dos/windows app, so it probably has its own config.  youll probably have to browse to the install directory and hunt for it there. id install it myself and hunt it out for ya if i had some more time. good luck to ya man

---

### Post by Computer Guru on 2008-01-18
EasyBCD's NeoGrub (GRUB4DOS implementation) stores it's configuration in \NST\menu.lst.

However, it might be reading the configuration from Ubuntu's /boot/grub/menu.lst; so check both loactions.

---

### Post by slackdog on 2008-01-22
After talking to my son who has Kubuntu 7.10 decided to install it.  I got all tied up trying to get into ubuntu and for that matter, kubuntu in accessing the menu.lst file.
So after searching around in the ubuntu forums came across the advice on the way to go through grub to get into the windows boot manager.  After fixing the MBR and boot in both win oses and reformatting the linux partitions, started over.
End result is that I got into kubuntu and found the menu.lst file (had a hiccough in getting permission to save the edit) but finally saved root from (hd1,2) to (hd0,2).
Everything is sweet........can boot into Kubuntu, or Windows Vista, or Windows XP.
Would like to really thank all you guys for your patience and advice. 
Could not have done it without it!

---

### Post by Computer Guru on 2008-01-23
You're welcome... welcome to the wonderful world of dual-booting :)

---

