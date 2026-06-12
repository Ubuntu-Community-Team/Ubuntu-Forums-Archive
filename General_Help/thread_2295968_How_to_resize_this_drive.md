---
title: "How to resize this drive?"
date: 2015-09-22
forum: General Help
---

### Post by tom208 on 2015-09-22
I used a live cd to try and extend /dev/sdc1 with the unallocated space but it does not allow me to resize this partition. I can use the unallocated 84gb of space to extend /dev/sdc2 so I tried extending that partition then shrinking it hoping it would move the unallocated space up but it didn't, it just moved it back to the bottom.  How can I extend this partition?
[ATTACH=CONFIG]264593[/ATTACH]

---

### Post by elliott6 on 2015-09-22
You should be able to do it. It's most likely the order you are trying to do it in. 
First, you would need to "move" the "extended partition" of /dev/sdc2 to the unallocated space. One that partion is moved, you should then be able to "grow" the intended primary partition of /dev/sdc1.

To better explain, you have your disk currently carved into three pieces - sdc1, sdc2, and a blank. Within sdc2 you have your swap partion and a blank. So your steps are as follows - 

- Select sdc2 in gparted and then from the heading "Partition -> Resize/Move"
- Slide sdc2 far right (or wherever) to shift the blank space to before sdc2
- Then you should have sdc1, blank, sdc2 (and or another blank depending on how much of the 84GB you want for sdc1)
- Then you should be able to select sdc1 and choose from the heading "Partition -> Resize/Move"
- Slide the right line (or choose the numbers) as much as you would like
- Click "Apply"

You'll want to do the above from the live disk, and the hard disk itself should not be mounted for it to work.

Let us know how you make out.

Thanks!

elliott

---

### Post by deadflowr on 2015-09-22
You need to turn off swap.
Right click on the partition and hit "swap off".

All partitions with a lock next to them are un-editable.
To edit, the lock needs to be disabled.
For what it's worth

The key symbol = locked.

---

### Post by yancek on 2015-09-22
Why do you want to extend sdc1?  You already have over 28GB for the / of the filesystem.  If you want to use the 84GB, just create a logical partition and format it then create a mount point in the / of the filesystem and put an entry in the fstab file so it is available for data on boot.

---

### Post by tom208 on 2015-09-23
> **elliott6 said:**
> You should be able to do it. It's most likely the order you are trying to do it in. 
First, you would need to "move" the "extended partition" of /dev/sdc2 to  the unallocated space. One that partion is moved, you should then be  able to "grow" the intended primary partition of /dev/sdc1.

To better explain, you have your disk currently carved into three pieces  - sdc1, sdc2, and a blank. Within sdc2 you have your swap partion and a  blank. So your steps are as follows - 

- Select sdc2 in gparted and then from the heading "Partition -> Resize/Move"
- Slide sdc2 far right (or wherever) to shift the blank space to before sdc2
- Then you should have sdc1, blank, sdc2 (and or another blank depending on how much of the 84GB you want for sdc1)
- Then you should be able to select sdc1 and choose from the heading "Partition -> Resize/Move"
- Slide the right line (or choose the numbers) as much as you would like
- Click "Apply"

You'll want to do the above from the live disk, and the hard disk itself should not be mounted for it to work.

Let us know how you make out.

Thanks!

elliott


This worked great! Now I know what I was doing wrong- I didn't delete the swap the first time I tried it so I wasn't able to put the free space in front of partition. Thanks for your help!

---

