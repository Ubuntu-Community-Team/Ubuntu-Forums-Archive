---
title: "Date files when copy to a USB external disk"
date: 2007-11-02
forum: General Help
---

### Post by ryke on 2007-11-02
Hi,

When I copy some files to any of my external USB drives, I've noticed that Ubuntu sets the date at the time that copy is done.

Is there any way to keep the original date of each file when they are copied to a external USB drive?

(I have partitions with FAT32 and LEXT3, and dates are changed in both cases)

Thanks for your help

---

### Post by dcstar on 2007-11-02
> **ryke said:**
> Hi,

When I copy some files to any of my external USB drives, I've noticed that Ubuntu sets the date at the time that copy is done.

Is there any way to keep the original date of each file when they are copied to a external USB drive?

(I have partitions with FAT32 and LEXT3, and dates are changed in both cases)

Thanks for your help

If I copy files (using Nautilus) to an external USB stick drive with a FAT32 partition on my Gutsy system, the date of the original file remains.

I don't recall seeing (or changing) any setting for this.

---

### Post by ryke on 2007-11-03
Hi... thanx for your answer.

I've just checked it.

Well, the thing is that when I copy to an USB stick dates are not changed, but when I copy to an external USB hard disk dates are changed (I have 2 external disks, one formated with FAT32 and another one with 3 partitions -NTFS, FAT32 and EXT3-, and in both happens the same).

So, could be something related to how are mounted the drives?

Regards

---

### Post by ryke on 2007-11-03
Well, I was checking in my pc where I still have ubuntu 7.04... I've checked now in the pc with u 7.10 and it works fine, dates are preserved :)

Thanx for your help ;)

---

### Post by john.nicholls on 2007-11-03
cp -p preserves attributes such as date.

---

