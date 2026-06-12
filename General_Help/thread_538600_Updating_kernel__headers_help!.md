---
title: "Updating kernel / headers help!"
date: 2007-08-30
forum: General Help
---

### Post by RagingAardvark on 2007-08-30
I'm lost here! When trying to install vmware server (amongst other things) I get told that my headers don't match the kernel version. 

If I try:

sudo apt-get install linux-headers-`uname -r`

it returns:

E: Couldn't find package linux-headers--2.6.17-11-386

I tried following the instructions to recompile the latest kernel - which went pretty much without hitch. However, my grub menu gives me the following :

Ubuntu, Kernel 2.6.20-16-lowlatency
Ubuntu, Kenerl 2.6.20-16-lowlatency (recovery mode)
Ubuntu, Kernel 2.6.20-16-generic
Ubuntu, Kenerl 2.6.20-16-generic (recovery mode)
Ubuntu, Kernel 2.6.20-15-lowlatency
Ubuntu, Kenerl 2.6.20-15-lowlatency (recovery mode)
Ubuntu, Kernel 2.6.20-15-generic
Ubuntu, Kenerl 2.6.20-15-generic (recovery mode)
Ubuntu memtest x86t
Other Operating Systems:
Windows XP
Ubuntu Kernel 2.6.17-11-386 (on /dev/sdc1)
Ubuntu Kernel 2.6.17-11-386 recovery mode (on /dev/sdc1)
Ubuntu Kernel 2.6.15-26-386 (on /dev/sdc1)
Ubuntu Kernel 2.6.15-26-386 recovery mode (on /dev/sdc1)
Ubuntu memtest x86t

The first batch are Ubuntu Studio that I install on a whim - by the way, how the hell can I get rid of them?
The 2.6.17-11-386 is where I'm typing this from now, and the one that I'd like to become up to date. 

Ideally, I'd be left with this install (up to date), the recovery version, XP and the (single) memtest. 

Can anyone help me out of this tangle please?

txs

KJ

---

### Post by RagingAardvark on 2007-08-30
Sorry, the "following instructions" being;

[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

KJ

---

### Post by RagingAardvark on 2007-08-31
Well, I'm getting somewhere with this ........ more confused! :(

I can see the initrd.img-2.6.22.5 and vmlinuz-2.6.22.5 in /boot. And menu.lst in /boot/grub has the correct entries - including 2.6.22.5. 

I commented out all the unwanted versions (except this one that is working) and rebooted and was presented with the same (uncommented) grub menu. 

Using 'e' to look at the grub entries, I note that the first bunch of items are on hd2,2 and the following on hd2,0.

Could it be that the system is booting from grub on the Ubuntu Studio partition thus ignoring the menu.lst on the 2.6..... partition?

If so, how can I make the partition that I'm in now - and the one that's got the 2.6.22.5 kernel on it - the partition that the boot process picks up menu.lst from? 

Gparted shows sdc - which everything linux seems to reside on as ;

/dev/sdc1 (this partition)  - exclamation mark (unable to find mountpoint)
/dev/sdc3 -flag of boot (I'm guessing that must be the Ubuntu Studio partition - hd2,2)
/dev/sdc3 - extended split between sdc6 and sdc5 (two linux-swap partitions)

As far as my (limited) knowledge can tell, I need to move the "boot" from sdc3 to sdc1. 

All help, as ever, gratefully appreciated.

KJ

---

