---
title: "Need to reinstall my GRUB on 6.06.1"
date: 2007-03-08
forum: General Help
---

### Post by Support the 2nd on 2007-03-08
I thought I got it right this last time, but I didn't.  The grub file is on my 1st HD and not the one with Ubuntu.

Is there a Walkthrough or can someone give me a linux noob instruction on how to redo this?  I want to pull the other drive, but I can't because I can't boot this one then.

---

### Post by Azakus on 2007-03-08
Try this guide first
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Support the 2nd on 2007-03-09
> **Azakus said:**
> Try this guide first
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

> 2. Open a Terminal. Open a root terminal (that is, type "su" in a non-Ubuntu distro, or "sudo -i" in Ubuntu). Enter root passwords as necessary.

so I would type "sudo -i", then hit enter?

Is the root password my login password?

Is a root terminal just the same as the terminal I can open in the main menu?

---

### Post by Support the 2nd on 2007-03-09
Okay, that didn't fix it.  

Here is more of a detailed explaination of what I am trying to do....

I have two hard drives.  Drive A has Windows XP and the MBR and I guess GRUB....or something....because I need that drive hooked up to boot Drive B, which has Ubuntu 6.06.1.  I want to remove Drive A from my computer and leave only Dribe B, and be able to boot from Drive B.  Then later I can remove Drive B and put Drive A back in deal with my F'd up XP I screwed up and won't finishing starting.

I did the terminal thing while running the live OS CD, and it said found grub on (hd1,5), so I did the command and it said it failed on two things (but not fatal) and completed the third...which was something about a Stage1.5 or something like that.

So I need an MBR on Drive B is what I think I am saying, since I guess that GRUB wasn't why it won't boot when Drive B is by itself.

---

### Post by confused57 on 2007-03-09
You might want to try restoring the Windows code to your mbr on your Drive A.  Another way you could restore your Windows mbr is with the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's only a 500kb download, and I'd recommend that you burn a copy of SGD, while you're able to boot Ubuntu with your current setup...SGD can boot Windows or Linux and restore Windows code to mbr or Linux grub...it'll be an indispensible utility to have if you have problems booting either Windows or Ubuntu.

When you're able to boot your Windows drive independent of grub, you might want to consider setting your system up this way:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by Support the 2nd on 2007-03-09
> **confused57 said:**
> You might want to try restoring the Windows code to your mbr on your Drive A.  Another way you could restore your Windows mbr is with the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's only a 500kb download, and I'd recommend that you burn a copy of SGD, while you're able to boot Ubuntu with your current setup...SGD can boot Windows or Linux and restore Windows code to mbr or Linux grub...it'll be an indispensible utility to have if you have problems booting either Windows or Ubuntu.

When you're able to boot your Windows drive independent of grub, you might want to consider setting your system up this way:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

At the moment, I am not interested in restoring the Windows system.  I just would like to get the second hard drive to boot on its own.  I want to take the first drive out of my computer.

---

### Post by Support the 2nd on 2007-03-09
Anyone else?

---

### Post by confused57 on 2007-03-09
> **Support the 2nd said:**
> Anyone else?
You can wait on someone else, but you'll need to first install grub to your Ubuntu drive, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
Basically you'll be doing this:
```
sudo grub
find /boot/grub/stage1
```
this should return something like:
```
root (hd1,0)
```
to install grub to your Ubuntu drive mbr:
```
root (hd1,0)
setup (hd1)
quit
```

Once you have grub installed to your Ubuntu drive, set your Ubuntu drive in bios to boot before your Windows drive.  In the grub menu at startup, highlight your Ubuntu entry, press "e" to edit, then change root from (hd1,0) to (hd0,0), then press "b" to boot.  This change is temporary, but it can be made permanent in your /boot/grub/menu.lst, if it works:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
menu.lst is short for menu.list
change your root entries to (hd0,0)

you'll also need to change the line in your menu.lst:
```
# groot=(hd1,0)
```
to
```
# groot=(hd0,0)
```

This all assumes that your root is on the first partition of your Ubuntu drive.  If you want to make sure, you can use the following command, either from your install or a live cd:
```
sudo fdisk -l
```
the -l is a small "L"

You might want to wait if someone else has a better suggestion, I can't guarantee it'll work.

---

### Post by Support the 2nd on 2007-03-09
Thanks.  My grub if I recall was found on (hd1,5).

I think the very first partition I made on this drive is my Windows backup that I was planning.  Then I made a few other partitions for the stuff to install Ubuntu.

Hell, I might just pull the first drive, boot from the CD, and reinstall the whole thing.  I have only had it running two days.  Not a whole lot of stuff to lose at the moment.  Besides, I think I botched the partitioning because I got a message at startup saying my "/" drive is 95% full.  I made it 2.5 gigs.  Thought that was enough.  Also, that drive on my desktop, sda7 in my case, I cannot write to it.  Whats that for, because I made it 47 gigs thinking that is where I save files.

---

### Post by confused57 on 2007-03-09
> **Support the 2nd said:**
> Thanks.  My grub if I recall was found on (hd1,5).

I think the very first partition I made on this drive is my Windows backup that I was planning.  Then I made a few other partitions for the stuff to install Ubuntu.

Hell, I might just pull the first drive, boot from the CD, and reinstall the whole thing.  I have only had it running two days.  Not a whole lot of stuff to lose at the moment.  Besides, I think I botched the partitioning because I got a message at startup saying my "/" drive is 95% full.  I made it 2.5 gigs.  Thought that was enough.  Also, that drive on my desktop, sda7 in my case, I cannot write to it.  Whats that for, because I made it 47 gigs thinking that is where I save files.
Since you don't have any important data or configurations to lose, reinstalling would probably be easiest...you could set your system up a couple of ways:
1.) You could move your current slave drive to the primary IDE master, make sure to set bios to boot the master before the slave...see the link I gave you in my first reply.
or
2.)Leave the drive as slave, but set your bios to boot the slave drive before the master drive before installing Ubuntu...you'd need to leave your system set up this way.

You can set up your Ubuntu partitions something like 7-10 Gb for root, 1-1.5 Gb swap, and you can make another partition for home or a separate ext3 data partition(if you make a separate data partition, I'd make the root at least 10 Gb.

I suppose you probably initially made your swap 47 Gb, which is why you can't write to it.

You might want to read over this for setting up partitions:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

