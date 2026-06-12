---
title: "GRUB &quot;Error 17&quot;.......totally lost...."
date: 2008-06-09
forum: General Help
---

### Post by rmaguir on 2008-06-09
So I turned on my computer this morning....rather I opened it, and somehow "Dell Media Source" (which I've never used before) or something like that was open.  I had thought I turned it off last night, but it was already on.  

Anyhow, when I tried to reboot the computer, it gave me the infamous error 17.  I've booted up using the LiveCD, but I haven't figured out how to fix this problem.  A lot of what people are saying is over my head.  I'll give you as much information as I can.  

First of all, I'm not using a dual boot system.  That said, I do have a virtualbox with Vista installed.  

Next, using GParted, I took a look at my partitions, which apparently don't exist.  All it says is /dev/sda (149.05 GiB) at the top and the only partition showing says "unallocated" on both sides.  

Here's the output from several commands I saw mentioned in other questions.  I have no idea what they mean really...

sudo fdisk -l

> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       19131       19458     2620416    c  W95 FAT32 (LBA)
/dev/sda2           18705       19457     6048472+   5  Extended
/dev/sda5           18705       19457     6048441   82  Linux swap / Solaris

Partition table entries are not in disk order


less etc/fstab

> unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
/etc/fstab (END) 


I would greatly appreciate some help getting this fixed....

---

### Post by VMC on 2008-06-09
Not sure where fstab is coming from. Maybe the cdrom.

The bootable partition is Windows type. How did you install this by the way? 
If your not using dual boot, did you have Windows installed at some point?
 I know you can install ubuntu inside a Windows partition as a file, but I'm sure you didn't do this.

Normally you would go into grub by typing grub inside a terminal. Then:

find /boot/grub/stage1

But I don't see a Linux partition. I do see a swap partition.

---

### Post by rmaguir on 2008-06-09
My computer (Dell 1420) originally came with VISTA, but I erased it and installed Ubuntu.  I just used the LiveCD to install it.

---

### Post by rmaguir on 2008-06-09
When I type "grub" then find /boot/grub/stage1, it says 
> Error 15: file not found

---

### Post by VMC on 2008-06-09
Can you investigate whats inside that Fat32 file system.

If you have Puppy livecd it can read the fat32 file system.
I haven't used ubuntu livecd for that purpose, but at any
rate look inside the fat32 file system and see what's in there.
Maybe its an old keepsake files that you don't want deleted.

You didn't have an exteranl hard drive installed when you installed ubuntu did you?

It doesn't appear that any Linux partition exists, according to your fidsk output.

---

### Post by rmaguir on 2008-06-09
> **VMC said:**
> Can you investigate whats inside that Fat32 file system.

If you have Puppy livecd it can read the fat32 file system.
I haven't used ubuntu livecd for that purpose, but at any
rate look inside the fat32 file system and see what's in there.
Maybe its an old keepsake files that you don't want deleted.

You didn't have an exteranl hard drive installed when you installed ubuntu did you?

It doesn't appear that any Linux partition exists, according to your fidsk output.

How do I investigate the Fat32 file system?  I'm a newbie, so I please give me command lines if you can.  

Thanks.  

Also, I do have an external harddrive, however, I didn't have it when I installed Ubuntu.

---

### Post by meierfra. on 2008-06-09
You might want to look at this [thread]("http://ubuntuforums.org/showthread.php?t=606345&highlight=grub"). I don't really know much about this problem. But have seen various threads on the subject. So google should turn up some more information.  

I recommend to not even touch your computer before you figured out what is going on. You should be looking into data recovery.  Generally I recommend  testdisk and photorec  for this (click on testdisk in my signature)


PS I'm not sure you have the same problem, so maybe your situation isn't as bad as I think.

---

### Post by VMC on 2008-06-09
I remember you mentioned about the "Dell Media Source", but didn't know anything about it.

meierfra, is right. That link leads to this link:
[http://www.goodells.net/dellrestore/mediadirect.htm](http://www.goodells.net/dellrestore/mediadirect.htm)

All I can say is thats a dangerous button. In meierfra's link someone has even suggested to go so far as to remove the contacts to that key. Sounds like a dumb idea coming from Dell.

I have an older Dell that fortunately doesn't have that key.

By the sound of it, it appears Dell did a number on your Ubuntu installation.
Just go and read up on those links.

---

### Post by bananatower on 2008-06-10
I had the same issue on my 1420 just a couple of days ago and I thought I was screwed. But I fixed it last night. :) 
You need to get a livecd of some sort and use a tool called **testdisk** to restore the harddrive. Mediadirect does some sort of rewrite of the partition table but it doesn't actually kill your data.  For me  I didn't have the ubuntu CD but I did have puppy linux 4.0 which includes drivers for running the wireless out of the box on those dells. Booting up in puppy I then went to the puppy forum and searched for a copy of testdisk to install in puppy (puppy uses their own packaging tool called 'pet' Its basically a double-click install process). 
Now unfortunately I didn't really write down my recipe for fixing this since I was in a state of panic but basically I opened a console and ran testdisk, selected  "Analyze Disk", then "Search". From what I can tell it scans your harddrive and tries to guess based on the structure of the filesystem, what was lost of corrupted. So it found my partitions and let me choose "Write" which effectively re-wrote my partition table. (I'm probably explaining this wrong but you get the idea -- in my mind there is an index of what the disc is supposed to look like and media direct screws it up -- you just need to fix it. 

On reboot ubuntu started fine again. 
If you need further help let me know.....

brian

---

