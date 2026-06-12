---
title: "Error 21 after Rebooting"
date: 2008-04-24
forum: General Help
---

### Post by MichaelW. on 2008-04-24
Hi, after I installed Wubi 8.04 (501) I get an Error 21: Selected disk does not exist, when I'am trying to boot Ubuntu. Ubuntu was installed without a Problem, but after that it doesn't boot anymore, I can only selected different boot options in Grub but they all doesn't work.:( I've searched the forum but I didn't find a solution for this Problem.

Michael

---

### Post by ago on 2008-04-24
What is the first grub option that you see? And what exactly do you see on screen when you select it?

---

### Post by GrantsV on 2008-04-24
Me too.

NTFS Windows on SDA1 (sata), new partitions for / /home swap.  Install 8.04 i386 version.  When reboot Grub error 21.  Infact, I didnt get asked about Grub anytime during installation.  It just went to reboot page after installation.

7.10 worked fine.

---

### Post by MichaelW. on 2008-04-24
> **ago said:**
> What is the first grub option that you see? And what exactly do you see on screen when you select it?

The first Grub option is: Ubuntu 8.04,kernel 2.6.24-16-generic
When I'm trying to boot it it shows:
booting Ubuntu 8.04,kernel 2.6.24-16-generic
root (hd2,5)/ubuntu/disks
Error 21: Selected disk does not exist

Then I could press anykey to go back to the grup menu

---

### Post by ago on 2008-04-24
[https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230](https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230)

---

### Post by MichaelW. on 2008-04-24
Hi,
thank you, that solved it. :) I had to change it to hd1.

Michael

---

### Post by eyelessfade on 2008-04-24
please set subjet to [solved]

---

