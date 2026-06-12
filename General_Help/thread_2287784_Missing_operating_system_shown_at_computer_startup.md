---
title: "Missing operating system shown at computer startup"
date: 2015-07-22
forum: General Help
---

### Post by WaiMy on 2015-07-22
Hi,

I have been using ubuntu for a while and first time encountered this issue.

The screen said missing operating system. I tried to press and hold shift key to go in recovery mode but it just doesn't show the recovery menu. 

FYI,  I don't habe any startup disk for recovery and this is the only desktop I got.

Can anyone tell me how can I launch the recovery menu, please!

---

### Post by CitadelUniversal on 2015-07-22
If you can't enter recovery mode - have you looked at this documentation [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by grahammechanical on 2015-07-22
How did you install Ubuntu on that machine? Unless we purchase a machine with Ubuntu pre-installed then it is usual to download the Ubuntu ISO image and burn it to a DVD disc or a USB memory stick and then install by running Ubuntu in a live session from the DVD disc or USB stick.

If you still have your Ubuntu install media then you can use that to make backups of your data and to examine the file system of the hard disk. You will even be able to run certain tests of the hard disk.

_Reasons for the Motherboard not detecting an OS_

1) No OS installed
2) Hard disk disconnected
3) Hard disk broken
4) Operating system deleted - see number 1
5) Boot loader (Grub) deleted - see number 1
6) Motherboard looking for an OS in the wrong place. BIOS boot system pointing the motherboard to the wrong hard disk or boot media that do not have an OS on them

Those are some of the reasons that I can think of. Others may have more reasons to add. In Ubuntu we access Recovery mode from the Grub boot menu. If the motherboard is not loading the Grub boot menu then you will not be able to access the recovery mode.

Regards.

---

### Post by oldos2er on 2015-07-22
Moved to General Help.

---

### Post by Topsiho on 2015-07-23
Once in a while (very rarely, once in a few years or so) I have this problem too, that while booting no OS can be found. When I try again all things are normal again.
The hard disk is Okay, there is an OS on it, and it's not disconnected.
A possibility is that there exists a not so reliable connection somewhere between the hard disk and the processor, but I never was inclined to investigate that, the problem is no problem enough for me to do so. But maybe you could try and eventually correct the connections and the cables of your hard drive ...

I am sure that this kind of problems are always hardware connected.

Topsiho

---

### Post by oldfred on 2015-07-23
The error is from UEFI or BIOS, or before either grub or Ubuntu can start.

One more to add to list is you changed boot mode from UEFI to BIOS or vice versa. Then it cannot see any bootable device as it is in the other boot mode.

---

### Post by Buhweat on 2016-04-10
I just resolved this same problem for myself [suddenly "Missing Operating System" after years of booting 14.04 LTS w/o incident] after reading a (closed) thread here gave me some terms to hunt for on the web.

Try this: follow this link:
[http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/?PageSpeed=noscript](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/?PageSpeed=noscript)
found on:
[http://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/?PageSpeed=noscript](http://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/?PageSpeed=noscript)

I booted the LiveCD and used the manual commands; in my case:
% sudo mkdir /tmp/sda1
% sudo mount /dev/sda1 /tmp/sda1
% sudo grub-install --boot-directory=/tmp/sda1/boot /dev/sda

Note the "/boot" suffix added to the mount point and the final argument is the device, not the partition.

---

### Post by oldos2er on 2016-04-10
Old thread closed.

---

