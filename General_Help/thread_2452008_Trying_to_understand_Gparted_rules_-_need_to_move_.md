---
title: "Trying to understand Gparted rules - need to move and expand extended partition"
date: 2020-10-14
forum: General Help
---

### Post by DVD-R on 2020-10-14
Hi All,
I occasionally get stumped by Gparted - trying to move or enlarge a partition.
There must be some underlying business rules which I am unaware of.

Currently I have a drive divided into 4 parts.
[  A  ][ B ][ C ][ D ]

A = Windows NTFS partition
B = Un-allocated space
C & D reside within an extended space

C = Ubuntu system
D = Swap for Ubuntu

C - the Ubuntu system - is soon to run out of space - so I would like to move it to the left into B the Un-allocated space.
It seems to me that in order to accomplish that - I need to move the extended space into the Un-allocated space, and then use it to expand  where Ubuntu is located.

But Gparted will not facilitate moving extended partition to the left to utilize the B Un-allocated space.

What do I need to do in order to accomplish this?
Thanks!

---

### Post by ajgreeny on 2020-10-14
It's difficult to fully understand what you mean without either a more detailed explanation or a screenshot of the gparted window which will show all the partition sizes. You could also show us the output of ```
sudo fdisk -l
```.
Note, however, that you can not work on any partitions in use so you will need to boot to a USB live system using any up to date OS in the Ubuntu family; probably easiest to use the USB you used to install your system; live systems contain gparted as default so no need to install anything in order to do this.

---

### Post by TheFu on 2020-10-14
I understand.

You are stuck, because extended primary partitions cannot be resized while there are any logical partitions inside.  It really sucks when we get forced into using MSDOS partition tables rather than GPT. With GPT, this issue doesn't happen.

What can you do?  Backup the Ubuntu partition using something like fsarchiver to another disk, then delete both the swap and the Ubuntu partition and resize the extended partition as you like.  Or, if Windows allows it, you can convert the partition table from MSDOS ----> GPT.  I don't know whether this will work in Windows. Sorry.

Create a partition of the size you need, on the disk where you want it and restore the backed up partition using fsarchiver restore methods.  You aren't done.  If you can, place the swap partition at the far end of the disk and make it 4.1G in size.  That will leave storage between the Ubuntu and swap for other uses.
After the swap is created and the Ubuntu files are all back, we just need to fix the fstab file. Use the **blkid** command to see the UUID to current device name mapping. Edit the /etc/fstab on the HDD (it will not be mounted to /etc/fstab) and replace the old UUIDs for the new ones. Copy/paste is your friend here - I'd have 2 terminal windows open. 1 with **sudoedit /mnt/path/to/etc/fstab** and the other with the **blkid** output on the screen.

All of this has to be performed from a "Try Ubuntu" environment - booted from a install or emergency disk, not the OS on the drive today.  The drive has to be completely unused, unmounted, for all these processes.

There are other techniques that could be used if your storage had LVM. Assuming you don't. With LVM, you could add the unused disk areas to the VG thing use lvextend on the Ubuntu LV and Bob's your uncle. No down time needed. Plus, I think the fstab used the mapper names for logical volumes, so nothing need change there either.  Easy peasy, but only if LVM is already laid down on the disk. There isn't any way to retro-fit it. Sorry.

---

### Post by DVD-R on 2020-10-14
I should provide an update.
I found a solution!

I think the issue has to do with data that is located at the beginning of any partition.
That data is critical for operating system functionality.
So the reason I couldn't move or increase/decrease the extended space was because the Ubuntu OS was located at the very beginning of that extended partition.

The reason I think that is because - I was able to make the change by creating a little un-allocated space within the extended partition, and shuffling it over to the left so that it was located at the beginning of the extended partition.

First, I reduced the size of the swap partition.
Creating UN-allocated space to the right of the swap partition.
[ A ][ B ][ C ][D////] 

Then I shifted the swap partition over to the extreme right away from [ C ] the Ubuntu partition
The Un-allocated space is now located to the right of the Ubuntu System.
[ A ][ B ][ C ][////D] 

This allows me to shift [ C ] the ubuntu system over to the right into that un-allocated space.
[ A ][ B ][//// C ][ D ] 

So I'm essentially shuffling un-allocated space to the left inside the extended partition.
After shifting the Ubuntu system over to the right the Un-allocated space is now to the left of the Ubuntu system
And the Un-allocated space now resides at the beginning of the extended partition.

At this point the beginning of [ C ] Ubuntu partition is no longer located at the beginning of the extended partition - there is un-allocated space there.
This released Gparted - allowing me to shift the Ubuntu partition completely to the left into [ B ] the Un-allocated space.
[ A ][ C////// ][ D ] 

Then I was able to expand [ C ] the Ubuntu OS partition, and consume up the total un-allocated space in the drive.
[ A ][ C ][ D ]

I want to thank everyone for your informative posts!!!!
And this just goes to show how awesome Ubuntu is!!   :-]

---

### Post by ajgreeny on 2020-10-15
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by helen314 on 2020-10-15
Here is a little tidbit I learned today .

No more "extended / logical"  partitions-
just plain "partitions" - KISS.

The days of DOS should  be gone.
And many "technologies" associated with DOS, such as MBR, BIOS etc. 

 DOS  was "designed" and worked adequately with yesterday technology, but it  s**hould not be used today -WHENEVER  POSSIBLE**.
If one chooses UEFI  and GPT , live is much gooder.

---

