---
title: "Tragic HDD formating mistake"
date: 2014-09-02
forum: General Help
---

### Post by trekkiejonny on 2014-09-02
Is there a way to recover a NTFS partition that has been formatted over by Btrfs, not once but twice?

TestDisk deepsearch did not turn up any NTFS parts, is there an other way to find and restore the previous filesystem?

**_What happened:_**
Wanted to format the freespace on my testing desktop to a btrfs filesystem. 
&#65279;
```
lsblk
```

to find which partition the free space was and forgeting that it wouldn't show it and should have used another utility.

Can&#8217;t remember exactly what it looked like but this is very close.
```
sda      8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1   8:1    0   7.5G  0 part [SWAP]
&#9492;&#9472;sda2   8:2    0   9.2G  0 part /
sdb      8:16   0 931.5G  0 disk
&#9492;&#9472;sdb1   8:2    0 931.5G  0 part
```

Now I don&#8217;t know why but in my addled tired brain I thought the freespace was listed as the other HDD sdb1. Maybe because the size looked about right.

```
&#65279;sudo mkfs.btrfs -m single /dev/sdb1
```

that went fine and then for some reason I thought that I didn&#8217;t want it there so I did the disk instead of the part

```
&#65279;sudo mkfs.btrfs -m single /dev/sdb
```

Thinking everything is ok I make an entry in fstab, reboot, it mounts where I wanted it to, I made a simple test directory in it then a simple test file with nano.

Then it hits me, I had attached my external HDD to that computer because after I was done making the file system I was going to copy over my Ubuntu distribution mirror. Turns out that sdb was that hard drive and on there was also my backed up files and the backed up files for my parents.

A day and a small mental brake later I am here and need help.

This morning I took the HDD out of the external enclosure. Pluged it into my other testing computer and now I am using PhotoRec to recover files that where on that drive.

I learned a valuable life lesson, never do any formating when tired or lack of sleep. I just hope it didn't cost me years of family photos. Still a bit in shock from the scale of my mistake.

---

### Post by Mark Phelps on 2014-09-02
What MIGHT work is the following:
1) Use a working PC to download and burn a CD from the ISO file of the Minitool Partition Wizard Boot CD
2) Boot your PC from that CD
3) Try to use the Partition Recovery feature to see if that restores the partition

If that does not work, my suggestion is to then investigate hooking your drive up to a working Windows PC and using Windows data recovery apps to see if you can restore any files or folders.  A free one is Recuva  The paid ones are better, and the best of those is RecoveryMyFiles -- free to install and try out.

---

### Post by ThatBum on 2014-09-02
If you have another drive of equal size or larger, it would be safer to image the formatted drive to the blank one and work on the image.

See [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by trekkiejonny on 2014-09-03
Isn't there a way to roll back Btrfs to the previous filesystem? Or is that only if I have a snapshot?

I just burned Minitool Partition Wizard Boot CD and also got another hard drive of equal size to copy to whole drive to like sugested. Will do all this tomorrow, made the mistake of doing this when tired before. Not going to make that mistake again.

---

