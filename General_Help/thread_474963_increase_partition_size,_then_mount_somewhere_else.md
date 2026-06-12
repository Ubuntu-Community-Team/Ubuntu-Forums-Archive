---
title: "increase partition size, then mount somewhere else"
date: 2007-06-15
forum: General Help
---

### Post by nbv4 on 2007-06-15
I have a 400 GB drive that was split up into two partitions. One was a 200 GB NTFS, the other was a 200 GB etx3. The NTFS partition had files from when I used windows.

Earlier today I moved all the files I wanted to keep from the NTFS partition, onto the ext3 partition. Then I deleted the NTFS partition.

Now I have the first 200GB of that drive unallocated, then the last 200GB formatted to ext3 and mounted to /media/disk-1

What I want to do is make that ext3 partition the full 400GB, then have it mounted to /home.

How do I go about doing this? I'm using gparted.

---

### Post by jimbob on 2007-06-15
Use Gparted to move the partition all the way to the left (beginning of the disk).

You may have to shrink it slightly first if it is slightly over 200GB  and the space it is going to is slightly less than that.

Then after that is done simply grow it to fill the entire disk.

Don't forget to adjust /etc/fstab and /boot/grub/menu.lst in case the partition numbers change.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by nbv4 on 2007-06-15
[http://img366.imageshack.us/img366/8263/screenshottb3.png](http://img366.imageshack.us/img366/8263/screenshottb3.png)

any idea why it won't let me resize? the partition is unmounted, and I already tried rebooting...

---

### Post by jimbob on 2007-06-16
Are you using a stand-alone live Gparted disk?  The background looks like Ubuntu is running.

I see no reason at all that you could not resize with the live CD.  Can't you put your cursor on the right side of the sda3 rectangle and drag it to the left?  What does it say?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by nbv4 on 2007-06-16
I'm using my regular install of ubuntu to run gparted. I never thought of using the live CD for this...

And when I try to drag the sides with the curser, but it won't budge.

Whats weird is that I can load up my FAT32 partition (on another physical disc) into GFarted and I can move it all around, resize it to my hearts content. There is something preventing me from modifying this disk...

---

### Post by jimbob on 2007-06-16
It only takes a couple of minutes to download and burn the stand-alone Gparted disk.

[http://sourceforge.net/project/downloading.php?group_id=115843&use_mirror=umn&filename=gparted-livecd-0.3.4-7.iso&39546595](http://sourceforge.net/project/downloading.php?group_id=115843&use_mirror=umn&filename=gparted-livecd-0.3.4-7.iso&39546595)

Give that a try and see if you have any better luck.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by nbv4 on 2007-06-17
I figured out what the problem was. The ext3 partition was I think too large for GParted to move. So I created another ext3 partition where the empty space was, moved all the files into the new ext3 partition (all 77 gigs of them), deleted the old ext3 partition, then extended the new partition to the very end. I had to use the ununtu live CD to get it to work, because doing it with my regular install kept causing permissions issues.

---

