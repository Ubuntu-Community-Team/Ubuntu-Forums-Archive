---
title: "How do I change name of hard disk"
date: 2021-09-18
forum: General Help
---

### Post by saulspatz on 2021-09-18
This is probably really simple, but I'm a newbie.
 
I recently installed Xubuntu on my old Mac Mini.  (This is not a dual boot system; OSX is no longer installed.)  I installed the OS on an SSD, but the machine also has a 2 TB hard drive that I haven't been using.  Today, I partitioned and formatted the hard drive with gparted.  I see the disk in terminal as /media/saul/4784d60c-be91-4966-9a94-c942712c3dfa, and in order to write to it, I had to use sudo.  

I made a top-level directory called myStuff and made myself the owner so now I can write to it, and the disk seems usable, except it still has this horrible long name that I see in terminal.  Is there a way to substitute a short name?  For example, when I'm in the directories on the rotary disk, I can refer to my stuff on the SSD by starting from ~.  Is there a way to accomplish a similar thing the other way round?  I've thought of putting a soft link in my path, but perhaps there's a better way.

Finally, is there a way to rename the disk so that I don't have that awful name in the terminal prompt?  Or can I perhaps give it an alias that I'll see in the prompt?  I had a thought that it might be possible to mount it as something else, but I haven't been able to figure that out.

---

### Post by &amp;KyT$0P# on 2021-09-18
> **saulspatz said:**
> is there a way to rename the disk so that I don't have that awful name in the terminal prompt?  Or can I perhaps give it an alias that I'll see in the prompt? 

Just to be clear: you have Thunar automatically mounting this partition, and you don't like that it names the mount point by UUID?  Try this -

1) Unmount the drive (don't eject it, just unmount the partition)

2) In GParted, right-click the now-unmounted partition, choose "Label file system".

Does it do what you're looking for?

---

### Post by Impavidus on 2021-09-19
As this is an internal drive (i.e., it's always present), the best way would be to put it in your fstab. Basically, create an empty directory that will serve as a mountpoint. It doesn't matter what you call it or where you create it, as long as the name isn't already taken by something else. Then add a line to your /etc/fstab that will cause the filesystem on that hard drive to be mounted at that directory automatically at boot time. The file manager will no longer mention it, but it will be mounted at the directory you created for it. There's no need to give it a label, but you could, if you wish. More details in [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab).

BTW, ~/ is just short for your home directory.

---

### Post by saulspatz on 2021-09-23
Yes, thanks a lot.

---

