---
title: "Resized partitions no bigger?"
date: 2006-07-31
forum: General Help
---

### Post by Lunar_Lamp on 2006-07-31
I needed more space on my linux install so decided to use some of the unallocated space on my hard drive.  I backed up my / and /home partitions using partimage, deleted them, recreated them using the space they used before and the extra space, loaded on the partition images (and fiddled with grub etc to make it boot).

However, it's not seeing the extra space.  The output of df does not agree with what my partitions say in gnome-partition-manager.  It also seems that there is no extra space.  I.e. my old / partition was ~5gb, and 96% full.  When I boot up I still get warned that my / partition is 96% full, despite it having increased from 5->10gb in size, but df doesn't notice this, it's like it's ignoring the new 5gb.  I also think that the /home partition may not have increased by as much as I think it should have done.

What's going on here?  Please help.

---

### Post by Lunar_Lamp on 2006-07-31
I found out how to fix this.  It is caused by partimage not being particularly amazing, though the fix is simple.  Boot up using a livecd (for example the ubuntu install cd) and do the following 2 commands on each partition that is being problematic (assumes /dev/hda3 is problematic partition):

sudo e2fsck -f /dev/hda3    #the -f option forces it to check 
sudo resize2fs -p /dev/hda3    #the -p option gives you an idea of % complete

---

### Post by az on 2006-07-31
Yes, The partition size and the size of the filesystem on it are two different things.

You copied the partition and the filesystem on it.  Restoring the image onto a bigger partition does not increase the filsystem unless you tell it to.

---

### Post by skatrek on 2006-08-09
Just FYI, I tried this after rebooting with SysRescueCD and everytime I tried resize2fs, it said "Please run 'e2fsck -f /dev/hda#' first" even though I had done it already. By mounting then unmounting the problematic partition, I could run e2fsck (which found non-contiguous sections) and resize2fs successfully.

---

