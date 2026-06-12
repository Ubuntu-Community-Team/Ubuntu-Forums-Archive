---
title: "USB Card Reader not showing (14.10)"
date: 2014-12-14
forum: General Help
---

### Post by Robbyx on 2014-12-14
A friend asked me to help her access her card reader. Lusb shows it is plugged in. It is not appearing as a device in nautilus or pcmanfm. How can i force it to be treated as a device that can be accessed like any other drive? Should i put a reference into fstab? If so what?

---

### Post by Jonor on 2014-12-15
Hi Robbyx, was it not showing even with storage media inserted ?
I think only drives with some suitably formatted storage space show in nautilus.
Fstab requires a declaration of that formatting even if it is none.

---

### Post by Robbyx on 2014-12-15
I very muddled about what is happening. I tried the advice at [http://is.gd/IhH5Ca](http://is.gd/IhH5Ca)

I ran the following:

ls -la /dev/sd* 
This showed the card reader as sdb

fdisk -l 
only showed sda partitions. Not sdb.

Mount -t vfat /dev/sdb
Can not read superblock

sudo mount /dev/sdb
Can not read superblock

I also had a second card reader put into the usb and had the same results. 
The card readers have  formatted cards in them. My friend will not accept that the 
cards are unformatted as she has used them in the past.

If I was putting an entry in fstab for a card reader what would it look like?

---

### Post by Jonor on 2014-12-16
A pair of card readers and cards; that should make it a lot easier to identify any problems.
Although fstab uses a fairly straightforward series of entries of the form :
<file system> <mount point>   <type>  <options>       <dump>  <pass>
i would not recommend starting with this as the fdisk -l already shows there is a problem.
What size are the cards in GB ?
Is there backup of the data on the cards so that they can be reformatted ?
Suggest you install usbmount which often makes MMCs better behaved.
Have a look both at the disk utility and Gparted (or similar) to see what shows for sdb.
The more information provided the better.
CLI mounting for FAT filesystems would normally be in the form :
sudo mount -tvfat -osync,noexec,nodev,noatime,nodiratime /dev/sdb1 /media/usb5
The device name will finish with a number, most likely 1 in this situation.

---

### Post by Robbyx on 2014-12-16
I have noticed a problem, not only is the sdb drive not going away when the SD reader is removed but I do not know what the sdb entry is and it is described as having not media. I think it is some left over from an earlier installation but it does not appear in fstab. It is showing in disk utility.

I begining to think that the sd reader is not being recognised.  My friend says this is a known glitch in 14.04. Do you know a solution?

---

### Post by Jonor on 2014-12-16
I use 14.04 now and yes it is a bit glitchy, certainly without using usbmount, did you install usbmount incidentally ?
I doubt this is a new bug, unique to 14.10.
Would you give the size of both of the cards in Gigabytes, this can make a difference ?
On the disk utility for the card would you either take 2 screenshots, one of what the disk utility shows and one of what shows when firstly the black square is clicked for the card space, to unmount it and then secondly the small gears symbol is clicked and the Edit Mount Options is selected - may look a bit grey if Automatic Mount Options is on. 
Or this information could be written down line by line. Providing all this information will go a long way to solving the problem.
Remember to remount the card afterwards by cancelling Edit Mount Options and clicking the black triangle for the card space.

---

