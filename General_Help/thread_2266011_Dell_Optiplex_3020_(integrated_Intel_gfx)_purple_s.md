---
title: "Dell Optiplex 3020 (integrated Intel gfx) purple screen boot problem"
date: 2015-02-19
forum: General Help
---

### Post by Mark_Dart on 2015-02-19
Hi

I am a beginner to Ubuntu and have been tasked with resolving a regular issue in the office. I've done lots of searches for solutions but I apologise if this is something that has been dealt with before.

**Problem:  Whenever a PC reboots and no OS is selected on the Grub screen, we get  the blank purple screen. Sometimes it happens when an OS is selected,  but not always.**

When this happens, you cant do ctrl + alt f1,  press e or anything really. You just have to hard power off the PC then  reboot and hope it goes into the OS.


_The devices it occurs on are:_

Dell Optiplex 3020 (both SFF and normal PC versions) with Integrated Intel HD Graphics 4400.
Running Ubuntu LTS 14.04 and also some of them have a secondary OS: Windows 8.1. I did standard options on the install of the OS.
Fully updated Ubuntu software
Updated to the latest Intel driver according to the Intel Linux driver app they released
[U]
I've tried the following as well as undone them when they didnt work:[/U]

-setting default OS so it doesnt ask for it on grub screen
-adding "nomodeset" to boot options (and doing grub-update afterwards)
-adding/removing "quiet splash" in boot options  (and doing grub-update afterwards)
-Using/reinstalling the fglrx graphics driver
-trying the "acpi_osi="linux" option in grub boot options
-changing "no framebuffer=" to y in initframs tools conf.d splash

One thing I have observed when trying to recreate the issue is that the purple screen doesnt come back unless I edit something in Terminal or any configuration. i.e. if I just reboot and reboot it wont go purple, but if I edit the grub file and reboot it does go purple.

I've  gone back to a device that has none of the above done that I could test  your suggestions on, and am willing to post whatever logs are needed  but could really do with some more assistance if possible.

many thanks

---

### Post by Mark_Dart on 2015-02-23
anyone able to help with this? i can provide more detail where necessary

---

### Post by Mark_Dart on 2015-02-26
hi

---

### Post by mörgæs on 2015-02-26
If you don't get a response it's often better to ask for the thread to be moved (by using the report button) than bumping.

Moving to General Help to see if anyone here is able to help.

---

### Post by Mark_Dart on 2015-03-02
thanks Morgaes

---

### Post by Biel on 2015-08-14
Hi, i have the same problem. Anyone able to help us? Thx!

---

### Post by Biel on 2015-08-14
I have the same machine but my so is ubuntu 12.04.

When I start the computer, one in four or five times I get the purple screen CRT + F1 does nothing. I also tried to add nomodeset no results.

---

### Post by mörgæs on 2015-08-15
Do you have the same problem with 15.04?

---

