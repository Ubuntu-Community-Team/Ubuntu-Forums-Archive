---
title: "installing ubuntu makes a part of the disk unusable"
date: 2008-05-30
forum: General Help
---

### Post by chriskin on 2008-05-30
i recently installed ubuntu 8.04 on my laptop 
i had a 50gb partition free so i chose it
i took about 20gb for ext3, about 2 for swap and then the rest was marked as "unusable" and i could do nothing about it
i need it to be either ntfs or fat32, is there any way to do that?

i tried starting the installation from scratch, but every time i try, i am allowed to customize up to two partitions, yet i need three (ubuntu, swap and the one i need for putting the files into)

so how can i make three of them?

:confused:

---

### Post by Aearenda on 2008-05-30
You can only have 4 primary partitions altogether - to get any more than that, one of the 4 needs to be an extended partition, which contains the fourth and further data partitions.

It sounds like you already have 4 partitions, so the remaining space cannot be used.
Maybe there are hidden manufacturer's partitions? Dell does this.
You could turn the swap partition into an extended one occupying the rest of the space, and create a swap partition and the ntfs partition inside that.

---

### Post by chriskin on 2008-05-30
it is a fujitsu siemens amilo xi 2428 if i am not mistaken

while trying to make partition, i found one that is neither the one vista is in, neither the one ubuntu is in, is that the hidden on you said?

as for the primary and extended partitions , i have no idea :S
is there any way to change something so i can use the rest 15gb?


** i am not sure i know how to do that :S

---

### Post by Aearenda on 2008-05-30
Yep, that would be right. It's probably a recovery partition. I can tell you what to do, but let's not rush in. First, please post the output of ```
sudo fdisk -l
```Also, how much RAM has your system got? (It would be useful to be able to run without swap while we move things around).

EDIT: ALso, I notice you said you've tried reinstalling - are you willing to do that again? It might be easier to explain how to proceed that way.

---

### Post by chriskin on 2008-05-30
it has 2gb ram 

what does a recovery partition do? anyway...


the results were : 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x623f2f23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530       13567    96685056    7  HPFS/NTFS
/dev/sda3           13568       17214    29294527+  83  Linux
/dev/sda4           17215       17457     1951897+  82  Linux swap / Solaris

---

### Post by chriskin on 2008-05-30
yes , i am ready to reinstall if that is what is easier

i only put ubuntu on this pc the day before yesterday, it is not as customized as my desktop pc is

---

### Post by the yawner on 2008-05-30
I got into this same predicament with a laptop that has got 2 partitions occupied with the recovery partition and the installation of Vista (which I chose not to remove out of curiosity). Anyway, I was hoping to keep this 2 existing partitions and break up the remaining 100GB to 4 more partitions (root, home, swap, and data). Here's how I did this:
/ - 20GB primary partition
/home - 40GB logical partition
/data - 50+ logical partition
swap - 2GB logical partition

---

### Post by chriskin on 2008-05-30
so if i reinstall ubuntu doing the same thing i will have no problem eh?

---

### Post by Aearenda on 2008-05-30
[This post has been edited to reflect the final outcome of the process]

A recovery partition allows the system drive to be reformatted as it was delivered from the factory, without the use of CDs. It also ties up a lot of space on the drive, and a primary partition slot. It saves money for the manufacturer since they don't need to supply CDs, though some still do, and when the user calls them for help they can just say 'press key xx at boot time' and the system will magically rebuild itself, even if they have lost any CDs that came with it.

Since you have plenty of RAM, let's try to restructure the swap partition. 

Step 1: You will have to turn swap off temporarily. This means the system can't use the swap space to augment RAM, but you've got loads anyway.
```
sudo swapoff -av
```
It should respond with ```
swapoff on /dev/sda4
```

Step 2: We use fdisk to delete the swap partition and then to create the extended partition instead. Please don't rush ahead with anything - if the outcome is different from what I say it should be, stop and tell me! The survival of your Vista installation is dependent on this.
```
sudo fdisk /dev/sda
```
This will tell you...```
The number of cylinders for this disk is set to 7296.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): m
```
The number of cylinders will be different, that does not matter.

Now you need to tell it to delete partition 4, by pressing 'd' and then '4'. 

After this, you need to create a new extended partition: Press 'n' for a new partition; it should prompt for 'p for primary or e for extended' or something like that. Choose 'e' and then set the start cylinder to 17215, and the end cylinder to 19457. Note to later readers: we set the cylinder numbers as there is a small gap earlier on the disk that was confusing everything.

Then, use 'n' again to create the fifth partition, which will be the new swap partition. Accept the start cylinder which should be 17215 again, and for the end cylinder put +2048M so that it works it out by size.

Then use 't' to set partition 5 to type 82 (82 is the code for a Linux swap partition).

When this is done use 'p' to print the proposed partition table.

It should look something like this:
```

Device   Boot Start    End   Blocks  Id System
/dev/sda1         1   1530 12288000  27 Unknown
/dev/sda2 *    1530  13567 96685056   7 HPFS/NTFS
/dev/sda3     13568  17214 29294527+ 83 Linux
/dev/sda4     17215  19457 18016897+  5 Extended
/dev/sda5     17215  17464  2008093+ 82 Linux swap / Solaris
```

The new swap partition should become /dev/sda5, since /dev/sda4 will now be an extended partition occupying all the space, and sda5 is inside it along with empty space for your other ntfs partition.

When this is done, the next step is to commit the changes so far, by pressing 'w'. There may be a warning about not using the new partition table until the next reboot as shown below; if so, do step 3a, otherwise skip to 3b.
```
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
```

Step 3a: 
Note: Skip to 3b if we don't need to reboot to pick up the new partition table.

If we do need to reboot, we need to tell the system not to look for the swap partition yet - so do ```
gksudo gedit /etc/fstab
``` and look for the line with 'swap' in it. Put a # at the start of that line, so it is commented out - then save the file and reboot.

Step 3b: Assuming we don't need to reboot, or if we have already done so, the next thing to do is 
```
sudo mkswap /dev/sda5
```
This formats the new swap partition ready for use.

Step 4: Now we have to modify the system to know it has a new swap partition. We need to know the unique ID for the new partition, so run ```
sudo vol_id --uuid /dev/sda5
```

Next do ```
gksudo gedit /etc/fstab
```
Move down to the line with # /dev/sda4 and change sda4 to sda5.
On the very next line, which should be the actual swap entry, you should replace the UUID (the long string of numbers, like 6c826e62-f741-4702-a344-fea855f579e8 ) with your UUID discovered in step 4. Also remove the # from the beginning of the line if you added one in step 3a. That part of the file should now look like this:
```
# /dev/sda5
UUID=your-new-uuid-goes-here-xxxxxxxxxxxx none swap sw 0 0
```
Save the file.

Step 5: Bring the swap file into use.
```
sudo swapon /dev/sda5
```

Later: After the next reboot, check that the fstab entry has worked by doing ```
sudo swapon -s
```
The output should look something like ```
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	1028120	0	-2
```but the size will be different.
The reboot is necessary to pick up the UUID change for the partition - just doing 'sudo swapon -a' before a reboot will fail.


Now the process is complete - and you should now be able to create an extra NTFS partition in the free space, as you were trying to before!

---

### Post by the yawner on 2008-05-30
I got this setup done about a week ago and so far no hiccups. But of course, I did a bit research first. Let's have someone confirm first.

---

### Post by chriskin on 2008-05-30
yes that was what it responded

but i do not want to trouble you any longer
if i can do what the yawner said, i have no problem

---

### Post by Aearenda on 2008-05-30
See updated post above.

---

### Post by chriskin on 2008-05-30
cylinders were 19457 but the rest is the same

as you said, number of cylinders doesn't matter

so...what next ? :D

should i delete number 4 now?

---

### Post by chriskin on 2008-05-30
Command (m for help): d
Partition number (1-4): 4

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
e
Selected partition 4
First cylinder (13567-19457, default 13567): 


i says this thing
what am i doing now?
i write 2000 or something for the size?

---

### Post by Aearenda on 2008-05-30
Yes, accept 13567 for the start cylinder, and I think you can say +2Gb for the size (or maybe +2048Mb). Main post above updated. <<<This was the wrong first cylinder - there's a small gap in there.

---

### Post by chriskin on 2008-05-30
i do not know if i made them correctly
is this thing right?
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530       13567    96685056    7  HPFS/NTFS
/dev/sda3           13568       17214    29294527+  83  Linux
/dev/sda4           13567       13567        2847+   5  Extended
/dev/sda5           13567       13567        2816   83  Linux


no i did not do it right
i will try once more
where do i put size and type? i am not asked :S

---

### Post by Aearenda on 2008-05-30
Wait a minute, let me get a livecd started in virtual box so I can see what you are seeing...

---

### Post by Aearenda on 2008-05-30
Ok, my mistake - let's 'd' partition 5 and 'd' partition 4, so that we are left with only three partitions again. Then look out for another edit to the main post.

---

### Post by chriskin on 2008-05-30
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x623f2f23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530       13567    96685056    7  HPFS/NTFS
/dev/sda3           13568       17214    29294527+  83  Linux
/dev/sda4           13567       13567        2847+   5  Extended
/dev/sda5           13567       13567        2816   82  Linux swap / Solaris

Partition table entries are not in disk order


this is what came out

---

### Post by Aearenda on 2008-05-30
Hmm, there must be a small gap between the NTFS partition and the Linux partition!

Sorry, 'd' 5 and 'd' 4 again to go back to three partitions.
Then 'n' 'e' and set the start cylinder to 17215, and the end cylinder to 19457.
Then 'p' and post the output again.

---

### Post by chriskin on 2008-05-30
is this any better?


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x623f2f23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530       13567    96685056    7  HPFS/NTFS
/dev/sda3           13568       17214    29294527+  83  Linux
/dev/sda4           17215       19457    18016897+   5  Extended
/dev/sda5           17215       19457    18016866   82  Linux swap / Solaris

---

### Post by Aearenda on 2008-05-30
Well, yes and no - yes because the extended partition is now right; no because the swap partition entirely fills the extended partition! Did you put +2048M for the end of the swap partition?

---

### Post by chriskin on 2008-05-30
what about now?
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530       13567    96685056    7  HPFS/NTFS
/dev/sda3           13568       17214    29294527+  83  Linux
/dev/sda4           17215       19457    18016897+   5  Extended
/dev/sda5           17215       17464     2008093+  82  Linux swap / Solaris


sorry for the trouble mate, this is my first time around serious things with the terminal :P

---

### Post by Aearenda on 2008-05-30
Don't worry, best way to learn. 

This looks good. Time to commit the change using 'w' and see what it says. Please post what it says next!

---

### Post by chriskin on 2008-05-30
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

---

### Post by Aearenda on 2008-05-30
Ok, so we do need a reboot. First, you need to do step 3a that has now appeared in the original post!

---

### Post by chriskin on 2008-05-30
this are the contents of the file of step 4 (i think)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=e8610d58-2573-4a31-9eda-25cc69737a5a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
#UUID=091a7d9f-a7b4-464d-b9fb-c617a0c4f158 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Aearenda on 2008-05-30
Great! Go ahead and change it as in step 4, so that ```
# /dev/sda4
#UUID=091a7d9f-a7b4-464d-b9fb-c617a0c4f158 none swap sw 0 0
``` becomes ```
# /dev/sda5
UUID=your-new-uuid-goes-here-xxxxxxxxxxxx none swap sw 0 0
```
And post the result - nearly done.

---

### Post by chriskin on 2008-05-30
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=e8610d58-2573-4a31-9eda-25cc69737a5a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=84b8094d-4c38-44a8-ab90-15ca88a126da none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Aearenda on 2008-05-30
Well done - save it and go on to step 5!

---

### Post by chriskin on 2008-05-30
swapon: cannot canonicalize /dev/disk/by-uuid/84b8094d-4c38-44a8-ab90-15ca88a126da: No such file or directory
swapon: cannot stat /dev/disk/by-uuid/84b8094d-4c38-44a8-ab90-15ca88a126da: No such file or directory
kalampokis@CNB:~$ 


:S

did i write something wrong?

---

### Post by danwood76 on 2008-05-30
Remove the UUID in the fstab and just use /dev/sda5.

So the line will be:
```

/dev/sda5 none swap sw 0 0

```

---

### Post by Aearenda on 2008-05-30
No, I don't think so - so long as the vol_id output matches the UUID, it's more likely that the system needs another reboot to pick up the new UUID following the mkswap stage. For now, ```
sudo swapon /dev/sda5
``` should pick it up.

After you do reboot, do ```
sudo swapon -s
``` to make sure the swap file is in use. It should say something like ```
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	1028120	0	-2
```

PS: Don't do what danwood76 says. If the drives ever change order, which is more common these days, the system will fail to find the partition using /dev/sda5. Drives change order particularly on mixed IDE/SATA systems, or when external drives are added, and the newer kernels use UUIDs to avoid this confusion.

---

### Post by chriskin on 2008-05-30
oops
wait just a moment

---

### Post by chriskin on 2008-05-30
it showed this :  
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	2008084	0	-1


is it ok?

---

### Post by Aearenda on 2008-05-30
Yes, that's good! I think we're done, you now should have space to add your NTFS partition (it will be sda6), all that's left to do is restart (when you're ready) to prove the modified fstab entry is right. I added a comment on the original post to show how to do this. You have so much RAM that your system probably never uses the swap partition anyway! (Maybe you already restarted - I'm not sure)

---

### Post by chriskin on 2008-05-30
i really owe you a big favor :D
yet all i can give you is some :popcorn: :S


anyway
thank you :D

---

### Post by Aearenda on 2008-05-30
You're welcome - the forum equivalent of thanks is to click on the little medal icon at the bottom right of a post - but only if you want to :-)
Good luck!

---

### Post by chriskin on 2008-05-30
i have already done that :D

thanks again

---

### Post by Aearenda on 2008-05-30
I didn't notice. Thanks for your thanks! Again! 
And now for something completely different...

---

### Post by chriskin on 2008-05-30
actually i still have a small problem here
i now can make the ntfs partition with the rest of the space
but i do not know how

using the terminal? or the ubuntu disk? :S

---

### Post by Aearenda on 2008-05-30
Ah! Easiest way would be to do it by rebooting into Vista, if it is anything like XP. But I've never used Vista to do this myself.

In XP, working from memory, I would right-click on 'My Computer', choose 'Manage' and then select the disk manager from the console that comes up. Find the free space in the display of the drive and right-click on it, choose to create a partition, and follow on from there. I expect Vista is similar.

I don't know how to create an NTFS partition in Ubuntu!
Looks like you have to install ntfsprogs using Synaptic and then use fdisk to create the partition, mkntfs to format it.

---

### Post by Aearenda on 2008-05-30
Here's my guess for the steps to get you started if you choose the Ubuntu way.
```
sudo apt-get install ntfsprogs
sudo fdisk /dev/sda
```
n=new partition
Accept the proposed start and end cylinders
t for type
partition 6
type code is 7
w to save
reboot
```
sudo mkntfs /dev/sda6
```

Next you need to add it into /etc/fstab. There are several threads around for how to do that, so I'll leave it to you to find them as it is now late here! 
:-)

---

