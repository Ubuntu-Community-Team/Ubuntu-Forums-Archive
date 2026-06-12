---
title: "Argh! HD problems! Please help!"
date: 2006-08-04
forum: General Help
---

### Post by jamesoz91 on 2006-08-04
Hello.
I have done something I regret. What happened was that I used GParted to manually edit the partition table, and took some free space away from my 74GB  NTFS drive, to make a Linux-swap and a ext3 partition inside an Extended partition. But, now, it's all been stuffed up, because after the partitioning was done, the thing told me it didn't recognise the Linux-swap and ext3 partitions, and also, now nothing can recognise my NTFS drive! I can't even boot into windows, it just sits there saying "Error loading operating system".
Ogh! Dammit! Has anyone ever had such experience with this? I was hoping to create a dual-boot WinXP and DD computer, but now it seems to be all ruined.

---

### Post by orb9220 on 2006-08-04
Boot up with windows xp cd and enter into recovery mode.

at the prompt type  fixmbr that will reinstall your xp mbr and allow your xp to boot if it is still a valid partition.

---

### Post by jamesoz91 on 2006-08-05
Well after I did that, and every other possible fixing utility on the Recovery Console, I get an error message when I turn on the computer:
Cant find autochk program.
Next it goes to the famous blue screen with the error "Fatal Error c000021a".
EDIT: The HD is now readable, and it's back in its NTFS file system.

And I have another problem in addition to my many others. When I try to read from my HD in Live Ubuntu (from which I am typing this post), it gives me an error saying "Unable to mount the selected volume" and underneath,

error: device /dev/hda2 is not removable
error: could not execute pmount

So I have absolutely no idea what is wrong with the computer now. I would at least like to get the data of the HD and onto an external storage device. Is there some way to fix this error?

---

### Post by njzillest on 2006-08-05
> 
Next it goes to the famous blue screen with the error "Fatal Error c000021a".


That means it cant read from your HD, i had the same problem, because my RAM wasnt installed properly. You may have an NTFS partition (thats what is showing up on Ubuntu) but nothing on it. I think you may have reformated the NTFS parition. You shouldnt have a problem. 

You can try in the terminal:
```

mount (harddrive location) 

```
normally it will be /media/hda1 or /dev/hda1

if your still having problems, do chmod (hda1)

^ normally you shouldnt have to do this, but its worth a try.


I suggest you use a ghost disk and just re do everything. Try to use partition magic on a seperate disk, thatway no drives are mounted, and you can easily resize them.


I hope this helps. I wish i could help you more, but i dont know enough of the nature for your problem.

---

### Post by cliveo on 2006-08-05
A thought... I've just mounted my other hdd using the bash terminal as root. I reckon if your're trying to mount a drive, you need to create a folder for it to mount in, and it's a folder per partition. If you create a directory (in RAM as you're booting from the cd) called /mnt (mkdir /mnt) with subdirectories for the partitions, and then mount the partitions to there by "mount -t ntfs /dev/hdda1 /mnt/hda1" it should mount your ntfs partition. For FAT32 it's "vfat". I did this from outside the OS in the repair mode, so I don't know if you can do it if you're in the GUI.

Clive

---

### Post by jamesoz91 on 2006-08-06
OK... the nature of my problem has changed. Now, I want to be able to access a Removable HD that I bought. It's 100GB and uses NTFS. However, it says in Properties of the device that it is read-only.
I want to have read, write, and execute privileges on this device. I have no idea what to do. chmod? But how?
If you answer, please do it simply, because I am a noobie to Linux in general, and have next to no clue of what the previous two posts meant.

---

