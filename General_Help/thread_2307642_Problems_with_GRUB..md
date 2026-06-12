---
title: "Problems with GRUB."
date: 2015-12-27
forum: General Help
---

### Post by doug32 on 2015-12-27
Not too long ago I upgraded from Win 8.1 to Win 10 w/ out any other OS installed. Within a couple days of using 10 I had some privacy concerns, so I decided to install and dual boot Ubuntu with Windows like I've done years before.

 My problem is GRUB wont boot Windows 10. The boot path (not to savy with computer lingo) is wrong. It says Windows 8 when it should say 10. I've tried a bunch of different solutions including downloading GRUB customizer, or trying to fix myself in terminal with instructions I've found online for people with similar problems. I've seen a lot of people have had there boot problems solved, but I believe mine is unique in that I upgraded to windows 10 via the 8.1 OS instead of doing a fresh install, and then installing Ubuntu.

Help would be much appreciated. Thanks!

---

### Post by Sina_RJ on 2015-12-27
Hi
Welcome to ubuntu world!!

We may need more information about this problem, can you boot into windows at all, or the windows option doesn't work anyway.
I mean, if you select windows 8.1 it goes into windows 10 or it just prints an error?
if it prints an error can you please post it here.

---

### Post by yancek on 2015-12-27
Go to the site below and download the boot repair iso and burn it as a bootable image to a CD.  Then reboot the computer with boot repair in the drive and the CD set to first boot priority.  When it boots select the "Create BootInfo Summary" option and post a link to the output here and someone should be able to help.  Do not try to make any repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2015-12-27
Grub2's os-prober parses Windows for a description match and uses that as entry. But it just has not been updated to look for Windows 10. It often go thru parse and if not found calls it Windows recovery. But perhaps an upgrade still has Windows 8 somewhere that it finds?
Or description should not be any issue and grub will eventually be updated.

But to know details we need the Summary report from Boot-Repair as yancek has suggested.

---

