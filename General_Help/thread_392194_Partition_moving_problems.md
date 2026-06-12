---
title: "Partition moving problems"
date: 2007-03-24
forum: General Help
---

### Post by nick_karstedt on 2007-03-24
So I started off with a rather small ext3 partition for Ubuntu.  I recently resized the Fat32 partition before it, but I cannot resize the ext3 partition, it needs to be moved.  This there any way to do this?  GNOME Partition Editor apparently can't do that...

---

### Post by chewearn on 2007-03-24
You need to unmount a partition before you can move or resize it.  Therefore, you cannot do this while running ubuntu off the partition.

What you need to do is boot from the ubuntu LiveCD or another linux CD like GParted LiveCD.

---

### Post by raja on 2007-03-24
Depending on how much free space you now have before the ext partition, you can create a separate /home (if you dont have one already) or a partition for storing some data. Or you can change it to swap (if it is not too large), then use the space where the swap is currently located. Moving the root partition itself is going to be more complicated.

---

### Post by nick_karstedt on 2007-03-24
Ok so here's exactly how my system is:

128 gig NTFS (Windows installation & apps, mostly full)
15 gig Fat32 (Media used in both windows and linux, mostly music, almost full)
3 gig ext3 (Ubuntu, 50 megs from full :( )
3 gig unpartitioned (Before ext3)

I booted off the Ubuntu CD and ran GParted to attempt to resize the ext3 partition but it wouldn't support moving it (Since the unpartitioned space was before the partition and not after).  So I should partition the remaining space and use it as swap?  How would I go about doing this (I've only used linux once before, long ago).

---

### Post by chewearn on 2007-03-24
I have read somewhere about difficulty of resize/move to space before the partition, but personally I have no first hand knowledge (up to now I have only been cloning partitions and resizing the space after the partition).  

I can only suggest you might want to try newer version of GParted. There is the GParted LiveCD, which is a 50MB iso:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by jimbob on 2007-03-24
If I understand your layout correctly couldn't you shrink the Ubuntu partition as much as you can to reclaim the 50 MB, then format the 3GB partition before it as ext3 and copy/move the Ubuntu partition into it.

  If that is successful, then delete the old Ubuntu partition and resize the new one behind it to fill in all the remaining space resulting in an Ubuntu partition that is now 6GB in size.

Don't forget to change your fstab to reflect the changes.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by nick_karstedt on 2007-03-24
Sounds like it'll work, I'll give it a shot.  I don't get the "fstab" thing though...  fill me in? ;)

Nevermind, got it heh

---

### Post by jimbob on 2007-03-24
When you create the new partition(s) your existing /etc/fstab is going to change depending on the names your system assigns to them.

You will be able to see this in the Gparted display after all the copying/resizing is complete.

You can open a terminal in Gparted and mount your new partition and go in and modify the fstab accordingly.

If you are completely unfamiliar with fstab I don't know exactly where to tell you to go to read up on it.  Sorry.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by raja on 2007-03-24
> **jimbob said:**
> If I understand your layout correctly couldn't you shrink the Ubuntu partition as much as you can to reclaim the 50 MB, then format the 3GB partition before it as ext3 and copy/move the Ubuntu partition into it.

  If that is successful, then delete the old Ubuntu partition and resize the new one behind it to fill in all the remaining space resulting in an Ubuntu partition that is now 6GB in size.

Don't forget to change your fstab to reflect the changes.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

This may be the best approach. There would also be many advantages to making a separate home partition. You can have a look at [this page]("http://www.psychocats.net/ubuntu/separatehome") for help.

---

### Post by nick_karstedt on 2007-03-24
Jimbob's method worked great.  Only problem was GRUB, so I got a livecd version to put it back on the mbr and repair the list.  Thanks!

---

