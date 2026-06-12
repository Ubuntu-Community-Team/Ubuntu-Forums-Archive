---
title: "[SOLVED] Grub and disk changes."
date: 2008-05-19
forum: General Help
---

### Post by Sak on 2008-05-19
Hey everybody,

I'm experiencing something of an unusual problem, and was hoping someone might have a suggestion or two.  

I have 3 hard disks in my system...

On the primary controller, the master is a 20G disk with WinXP, the Slave is a 40G disk that is just data (music, backup files, etc.)  The secondary controller master is a 40G disk for Ubuntu, and the slave is CD/DVD RW.

Okay, so what happened was this weekend I removed the data disk from the machine, because I wanted to put it into a USB enclosure to make it more portable.  Leaving the remaining disks in their original locations, rebooting, I Grub came up with an Error 21 message, that it couldn't find the disk.

I repaired Grub with [Supergrub]("http://supergrub.forjamari.linex.org/"), and was able to see the Grub menu that Ubuntu installs.  From this menu, I was able to boot into WinXP, but whenever I selected any of the Linux options, I'd get the Error 21 message again.  The only way I could figure out how to get Ubuntu to boot again, was to put the data disk back in as the slave on the primary channel, and all is well.

This confuses me, because there's nothing on that disk that has anything to do with either OS, or the bootloader, and so I'm not sure why Grub freaks out when it's removed from the machine.  It has no purpose in any of the operating systems, and I mount it separately.  

I also tried what suggestions were offered here:

[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html)
[http://www.mepis.org/node/7330](http://www.mepis.org/node/7330)
[http://www.linuxquestions.org/questions/linux-general-1/grub-error-21-338856/](http://www.linuxquestions.org/questions/linux-general-1/grub-error-21-338856/)

Ideally, I'd just like to remove the data disk without having to reinstall Ubuntu in order to get everything to work right again.  So I was hoping someone might have a suggestion or two that might help repair Grub so that it can find my Ubuntu install.

---

### Post by Patb on 2008-05-19
Sak, it's a long shot but have you checked the uuids for each disk partition?  I don't understand how the uuids are assigned but perhaps removing that disk changes the assignments.  I'm also not sure how you would check what the new ones are other than by booting from a live CD with the disk in its new usb position.  Then you could "sudo blkid" to show the uuids and then reboot and edit the grub entries to check whether they are still correct.  

I hope that's clear (or helps, even :)).  

Cheers, Pat.

---

### Post by Sak on 2008-05-19
Hey Pat,

Thanks for the suggestion.  I ran the blkid command before disconnecting the drive and got the following output...

/dev/sda1: UUID="6210AD8410AD6031" TYPE="ntfs" 
/dev/sdb1: LABEL="NARCISSUS" UUID="2F0C-09ED" TYPE="vfat" 
/dev/sdc5: TYPE="swap" UUID="89707526-f24f-43b2-a0ca-9b565ab99e86" 
/dev/sdc6: UUID="30ca8469-371e-4134-9888-64a2b60036a4" TYPE="ext3" 
/dev/sdc7: UUID="a5617421-2724-4dc4-9e9d-4009a4ec3548" TYPE="ext3" 

I then unplugged the drive, NARCISSUS, which is the data drive, and booted off the LiveCD and ran the command again...

/dev/sda1: UUID="6210AD8410AD6031" TYPE="ntfs" 
/dev/sdb5: UUID="89707526-f24f-43b2-a0ca-9b565ab99e86" TYPE="swap" 
/dev/sdb6: UUID="30ca8469-371e-4134-9888-64a2b60036a4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb7: UUID="a5617421-2724-4dc4-9e9d-4009a4ec3548" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

So it seems that the UUIDs are remaining the same.

Edit: This got me wondering if the problem might be with Grub?  I remember, when I was looking around in Supergrub, that the disk that Ubuntu was booting off of was (2,5) or something like that.  Is it possible that this is changing if I remove the data disk, making it so that Grub can't find the disk?  I'm not sure where or how to check for that though.

---

### Post by Patb on 2008-05-19
> **Sak said:**
> Is it possible that this is changing if I remove the data disk, making it so that Grub can't find the disk?  I'm not sure where or how to check for that though.
Sak, although the uuids are not changing the disk number/notation is: what was /dev/sdc is now /dev/sdb. Note that the disk for Windows, which you can boot, does not change. 

To check what Grub is doing, when you have the Grub menu visible, select your option and press "e".  Then press "e" again on any particular line to edit it.  Check carefully that the notation is correct for all lines, particularly "root..." and "kernel...".  Remember that the /dev/... numbering starts at 1 whereas Grub numbering starts at 0, so "/dev/sda1" probably refers to Grub's "root (hd0,0)" and so on.

Edit as necessary and try to boot.  One small trap: press "b" to boot your edited version. Don't escape back to the menu, that will use the original settings.  The original grub settings remain unchanged so, to make any changes permanent, you can edit your /boot/grub/menu.lst manually as root, or possibly reinstall grub.  I would just back up and edit the menu.lst file.  

Cheers, Pat.

---

### Post by Sak on 2008-05-19
Hey Pat,

You were right, removing the data disk changed the Ubuntu location from hd(2,5) in Grub, to hd(1,5)  Once I fixed that in the menu.lst file, everything is golden.  

Thanks so much for your time.

---

