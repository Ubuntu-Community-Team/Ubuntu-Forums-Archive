---
title: "GRUB question"
date: 2007-02-25
forum: General Help
---

### Post by keithk50 on 2007-02-25
Hi,    I have successfully installed Ubuntu 6.06 (dapper) onto my laptop which still has Windows XP on the hard drive.   Everything is working fine (apart from no sound but thats another issue!), and I can boot into either OS from the Master Boot Screen.   Linux will always boot automatically unless I choose XP from the boot menu.
Recently bought my first copy of Linux Format magazine with a free DVD.   In order to see Fedora 6 Live I rebooted with the DVD in the drive as the mag suggested.   My laptop rebooted and finished up with the Grub command prompt staring at me.   I was lost!   Finally I took the DVD out of the drive and typed in reboot (guess)
It rebooted straight into Linux as normal with no obvious problems.   I then booted up into XP and tried the same process again.   Once again the grub prompt  ended up in front of me.
Do I type something at the Grub prompt in order to get the DVD (or any other) to load at reboot?   Please bear with me as I am brand new to Linux and would appreciate any help or guidance.   Thanks for reading.     Keith:(

---

### Post by disturbedite on 2007-02-25
check the order of your boot up devices in your bios.  set the drive you're gonna put the disc in to the first device, and then try it again.

---

### Post by n8bounds on 2007-02-25
if you install ubuntu, you know how to boot from optical (cd/dvd), such things are handled in BIOS before GRUB.  So if you see grub at all, your dvd is either A> not really bootable, or B> not being attempted to being boot From by your BIOS settings

---

### Post by keithk50 on 2007-02-25
Thanks for the replies and advice.    I shall try the suggestions.    Great forum by the way.

---

### Post by keithk50 on 2007-02-25
Checked the order of Boot-up devices in my BIOS and changed the order as follows:

CD ROm
Hard Disk
Floppy

DVD will still not boot from CD Drive and grub command line still appears.   Its not the end of the world but it never happened before installation.   Any other suggestions.

---

