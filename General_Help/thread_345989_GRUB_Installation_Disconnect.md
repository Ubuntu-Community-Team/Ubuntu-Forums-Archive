---
title: "GRUB Installation Disconnect"
date: 2007-01-25
forum: General Help
---

### Post by Mike-97470 on 2007-01-25
Well, I've searched the forum, read the "Recovering Ubuntu After Installing Windows" and tried everything except the "Super Disk"--it's kind of hard to burn one when my main system isn't working.

Here's the story:
I screwed up sudoer trying to get firestarter configured.   I can't get to the Restore mode to fix the sudoer, because I haven't been booting through the GRUB menu for a very loooong time since I nuked my primary WinXP NTFS disk to repartition a big ext2 partition (doing that was, by far, the hardest of the hard!).  Since then I've been booting to linux through Windows Boot.ini

from fstab--
hdb1 is /proc, there is no /root partition
hdb5 is /swap
hda1 is WinXP, yes FAT32
hda5 is ext2

From the Ubuntu 6.10 "Live" CD I've gone to the Terminal and to GRUB--
"Find" finds stage1 at hd(1,0) as one might suspect.

Doing root (hd1,0) and setup (hd0) doesn't work.  --System boots to black screen w/blinking: _

GRUB indicates that setup ran just fine, loading 16 sectors on hd0 and all of the stage stuff on hd1.  I think it should work too, but something is tricky--

Hopefully, someone can tell what to do to fix this!
Thanks . . .

---

### Post by Bigbluecat on 2007-01-25
Go back into the liveCD and try

```
find /vmlinuz
```This should indicate the partition that contains your Linux Kernel. 

It's possible that the entries in you menu.lst are pointing to the wrong places.

---

### Post by Mike-97470 on 2007-01-26
Ok, Here's the deal--

[use Super GRUB CD to fix 2 disk boot problem]

My system configuration is-

primary (boot) disk is Windows XP    (my BIOS can't boot from secondary)
secondary disk is Ubuntu (hdb)

When Ubuntu was originally installed 1-1/2 years ago, Windows was already installed on the primary disk so I choose to install Ubuntu on the secondary disk.  GRUB easily figured out how to put it's IBL on the primary disk's MBR.  GRUB's OS selection menu came up during the boot process like it's supposed to.

When I repartitioned the primary disk to free up a large ext2 partition for Linux I had to reinstall Windows and it took over the MBR.  I fiddled with boot.ini to dual-boot into Linux.

But recently when I needed to get to the Linux restore mode to fix the sudoers file that I screwed up, I tried to reinstall GRUB and that naturally messed up the Windows MBR--GRUB normally expects ONE disk and didn't continue on to hdb1.  ("halted" at Black screen with blinking _ underscore)  It's a little tricky booting from the MBR of one-disk to a loader on another disk.  So the "Live CD" comes in handy sometimes, a slow but convenient way to get to a Terminal!

I discovered this very excellent Windows/Linux dual-boot GRUB page--
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
But I was not able to fix-up the MBR or even boot at all--
trying to boot manually or executing the menu.lst I got "inconsistent file system structure" errors which was actually a little scary!  I'm thinking that this could be caused by having to kill power when things got hung up . . .      Trying the chainloader +1 method just "halted" with the black screen and blinking _ underscore.

Eventually, I downloaded and burned a CD of the "Super Grub CD" on another system.  This is a very good tool although a little confusing at times.  Although it's Auto "Fix GRUB Linux Boot" didn't work, it was able to easily find and boot into any version of Linux from menu.lst.  Using it's Manual "Fix Boot" mode it was easy to specify hdb1 for the GRUB files and hda for the MBR file(s).  I'm sure all of this could have been done from the command line (by someone who knew what there were doing!)

The "final" step is to edit menu.lst to add Windows.

---

