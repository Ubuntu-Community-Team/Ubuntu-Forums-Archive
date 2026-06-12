---
title: "Weirdest problem ever. anyone with experience, please help."
date: 2007-07-24
forum: General Help
---

### Post by psyk0ninja on 2007-07-24
ok, let me start by saying ive only been on ubuntu for a few months now and that i have no idea what caused this problem. so i get on my computer today (i leave it running 24hrs a day) and i go into amarok to play some music. i click what i want and it says "some media not playable". thats weird, ive never had it before. so i go to the folder where i keep my music and all but 3 or 4 songs are DELETED. not in the trash, but deleted. it also deleted all my superkaramba themes. i have yet to find out what else it may have deleted, but unless someone came into my house while i was out today (which i doubt, considering i have security) they deleted themselves or were deleted by a program. i just installed frostwire. could i have gotten a virus from there? i thought linux was near immune to these things.

---

### Post by rbmorse on 2007-07-25
The first thing that comes to my mind is a hard drive problem...either with the file structure or perhaps a physical problem with the drive itself. 

It would be a good idea to back up your hard driver RIGHT NOW if you have not done so already. 

Because Linux can't repair the filesystem of a drive (if that is the problem) while it is mounted (loaded) onto the operating system, the easiest way I can think of to effectively check the drive is to boot from the K/Ubuntu live cd, open a terminal window and do the following:

sudo fdisk -l     (< the "l" is a lower case letter "L") to verify how the live CD enumerates your partitions 

From the list presented by fdisk, identify the partition that has/had the problem audio files on it. For a default Ubuntu installation onto a computer with only one hard drive that would normally be 

/dev/sda1 

but if you also have Windows installed or created a separate partition for /home the partition we want to check maybe something else.  Look for partitions of system type Linux. If you need help with this. please do the following:

open a terminal window and run:

```
sudo fdisk -l > /home/*yourusername*/Desktop/partition.txt
```

then cut and paste the content of that file into the body of a reply here. Mine looks like this (just verifying the instructions)

> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8360    67151668+   7  HPFS/NTFS
/dev/sda2            8361       16519    65537167+  83  Linux
/dev/sda3           16520       38913   179879805    f  W95 Ext'd (LBA)
/dev/sda5           16520       26269    78316843+  83  Linux
/dev/sda6           26270       26755     3903763+  82  Linux swap / Solaris
/dev/sda7           26756       38913    97659103+  83  Linux

Once you know which parition you want to check, from a terminal window run the following command:
```
sudo e2fsck -n /dev/*some-partition*
```

That will have the system run a filesystem integrity check, but not make any actual changes to the drive, yet.  Sort of like running the old DOS "chkdsk" command without the "/f" option. 

Does this command report any errors? Or lots and lots of errors? 

Alternatively, if you have the gParted liveCD available you can boot from that, select the drive in question and then the "check" function from the menu.  The gParted LiveCD is a very handy tool to have in any case, and you can download the .iso file from [http://sourceforge.net/project/downloading.php?group_id=115843&use_mirror=umn&filename=gparted-livecd-0.3.4-8.iso&72910426](http://sourceforge.net/project/downloading.php?group_id=115843&use_mirror=umn&filename=gparted-livecd-0.3.4-8.iso&72910426)

---

### Post by rbmorse on 2007-07-25
One other thing...if your file browser isn't set to view hidden files and folders, enable that and see if the missing files show up.  Longshot, but I've seen stranger things.

---

### Post by psyk0ninja on 2007-08-23
i ended up having to format/reinstall as i screwed some stuff up on that computer but i told a friend and he asked if i had left 8mb free space when i partitioned the drive (i partitioned it manually so i could have the /home seperate). i said no and he said thats probably what caused it. i havent had problems since i reinstalled and got the 8mb free.

---

