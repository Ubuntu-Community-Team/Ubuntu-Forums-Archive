---
title: "GParted resizing NTFS partition: claims drive is &quot;busy&quot;"
date: 2006-07-29
forum: General Help
---

### Post by diamond on 2006-07-29
I'm trying to shrink down my NTFS partition. So I booted from the Live CD, made sure that *none* of the /dev/hda partitions are mounted, loaded GParted, selected /dev/hda1 (my NTFS partition) and told it to resize. It went through the process for a few minutes, then complained that it had tried to operate on a "busy" device.

What's going on here? How can the drive be busy if none of its partitions are mounted? Is this because /dev/hda1 is marked as a "boot" partition? If so, can I safely turn off that flag long enough to resize it, then turn it back on and still be able to boot XP?

---

### Post by jordilin on 2006-07-29
Try to use the Gparted Live Cd in:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
or DiskDrake. DiskDrake has more options and can be run from another Linux Live Cd. This Linux Live Cd is called PCLinuxOS and can be downloaded from:
[http://www.pclinuxos.com/page.php?7](http://www.pclinuxos.com/page.php?7)
I have never been lucky using Gparted from Ubuntu.

---

### Post by diamond on 2006-07-29
> **jordilin said:**
> Try to use the Gparted Live Cd in:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
or DiskDrake. DiskDrake has more options and can be run from another Linux Live Cd. This Linux Live Cd is called PCLinuxOS and can be downloaded from:
[http://www.pclinuxos.com/page.php?7](http://www.pclinuxos.com/page.php?7)
I have never been lucky using Gparted from Ubuntu.

You're right. That worked.

Now I have another problem. I managed to shrink the NTFS partition by 10GB, so I have 10GB (actually 9.77GB) of unallocated space on the drive. And I didn't hose Ubuntu or XP in the process. Great.

But there's a little 100MB partition, /dev/hda2, in between the unallocated space and the primary partition I want to expand (/dev/hda3). This partition is mounted in /media/hda2, and when I look at it I see that it contains my Linux kernel, System.map, and grub directory. In fact, it has most of what's contained in my /boot directory (although I don't think that /boot is actually /dev/hda2, because it contains a few files that hda2 doesn't, and "mount" only shows hda2 mounted at /media/hda2).

So what is this partition? Is it a backup of my /boot folder? Is it necessary? I don't see any way to move it (or my /dev/hda3 partition) to put the free space in a more convenient location, so the only way to expand hda3 is to wipe out hda2.

What should I do here?

---

### Post by jordilin on 2006-07-29
I'm not sure if I understand. In the ntfs partition you are housing the m$ win and you have shrinked it by 10Gb. With the available space you want to install Ubuntu, right? Then, you should partition the available space accordingly to install Ubuntu and if you already have it, I would redo the partitioning and install Ubuntu again. It seems you have mixed partitions and I'm not sure what's the best way to solve it without installing again.

---

### Post by diamond on 2006-07-29
> **jordilin said:**
> I'm not sure if I understand. In the ntfs partition you are housing the m$ win and you have shrinked it by 10Gb. With the available space you want to install Ubuntu, right?

No, I already have Ubuntu installed. I want to use the available space to expand my root partition.

> Then, you should partition the available space accordingly to install Ubuntu and if you already have it, I would redo the partitioning and install Ubuntu again. It seems you have mixed partitions and I'm not sure what's the best way to solve it without installing again.

Sorry if I wasn't clear enough. Here's the layout of my drive:

[IMG]http://www.swcp.com/~diamond/Screenshot.png[/IMG]

What I want to do is take that extra 9.77GB and use it to expand my main Linux partition (/dev/hda3). Unfortunately, GParted won't let me do that -- and I assume the reason is because /dev/hda2 is in the way.

/dev/hda2 contains my kernel, its associated System.map, initrd and config files, and the grub directory -- basically the same thing that I have in my /boot folder.

So my question is: what the heck is /dev/hda2? It's not something I created; it was created by the Ubuntu installer when I first set it up.

---

### Post by jordilin on 2006-07-29
Now, it's more clear :D . In order to see what your /dev/hda2 is, I would go into Ubuntu, open a Console and type:
```
df -k
```
In my case I get:
> /dev/hda1                97826     23043     69564  25% /boot
/dev/hda3             54648636   4297432  47575172   9% /home

and you'll get something more or less the same but with your partitions. As you see, each line tells us where the /dev/hdaX is mounted, so you'll get an idea what your /dev/hda2 is.

---

### Post by diamond on 2006-07-29
> **jordilin said:**
> Now, it's more clear :D . In order to see what your /dev/hda2 is, I would go into Ubuntu, open a Console and type:
```
df -k
```
In my case I get:

and you'll get something more or less the same but with your partitions. As you see, each line tells us where the /dev/hdaX is mounted, so you'll get an idea what your /dev/hda2 is.

I feel like an idiot. Turns out the /dev/hda2 partition had nothing at all to do with Ubuntu. I realized this when I looked more closely at the files it contained. It had a Linux kernel, but an older version than the one I'm running. Furthermore, the kernel name had "_FC4" on the end.

That's when I remembered: the first Linux distro I tried to install on this machine was Red Hat FC4. I couldn't get it to work, and I quickly gave up and switched to Ubuntu. Obviously that was the boot partition that FC4 created, and I just forgot that it was there. I just nuked it, and everything's fine.

Thank you for all of your help; sorry about the wild goose chase.

---

