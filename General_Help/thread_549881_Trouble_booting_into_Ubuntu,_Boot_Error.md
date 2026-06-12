---
title: "Trouble booting into Ubuntu, Boot Error"
date: 2007-09-13
forum: General Help
---

### Post by ishaq2007 on 2007-09-13
Hi

**Problem:**

I Just download and installed Ubuntu 7.04.  (first time user, first time install)

Ubuntu Installed successfully and then computer restarted. I then was prompted to download and install all the latest updates after logging in. So I downloaded and installed  all the new updates. 

I was prompted to restart the computer so I did. Computer restarted, while restarting, i think Ubuntu did some kind of check, and found some error on the hard drive or partition (not exactly sure) didn't have time to read it all. 

Then the computer restarted again and NOW does not boot up. I get the following error 

*“Reboot and select proper boot device or Insert boot media in selected boot device and press and key”*

I found a temporary fix, which is to put the Ubuntu installation CD in and when the boot menu appears choose *Boot from first hard drive*. Then it boots in OK!

**Questions:**

Is there any way to fix this problem, so that the computer boot normally without me having to put in the CD each time? Is it possible to re-install/re-create the boot files (if that makes any sense)?

Or will I have to re-install Ubuntu all over again, and hope it fixes it?

Cheers
Ishaq 
[email]ishaq2007@gmail.com[/email]

---

### Post by anaconda on 2007-09-13
hard to say exactly, because there isn't enough information, but
My guess would be that you installed a new kernel with the updates, and something went wrong with updating the bootloader (grub) to the mbr. 

Search these forums for "fixing mbr after installing windows" and you should find instructions how to reinstall bootloader to mbr.

I would explain better, but I am too bysy now.. sorry

---

