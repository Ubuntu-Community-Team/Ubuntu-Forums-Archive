---
title: "Making Ubuntu the only os....."
date: 2007-04-10
forum: General Help
---

### Post by ginnie6 on 2007-04-10
here's my setup.... 2 hard drives, windows XP on primary disk and  Ubuntu on the slave. I'm getting to the point that I no longer need/use XP so I'd like to remove it from that disk to free up the space. What's the best way to do this?

---

### Post by xDCx on 2007-04-10
Format the XP drive.

---

### Post by cisforcojo on 2007-04-10
This shouldn't be too difficult. My understanding is that you want to remove windows and replace it with a linux partition. 
First install Gnome Partition Editor GParted:

sudo apt-get install gparted

you can remove your windows partition and replace it with an ext3 partition or whatever you desire.
I believe this should format the new drive as well. 

Next you'll want to edit /etc/fstab  to add the new partition
Finally, edit your /boot/grub/menu.lst    and remove the XP entry.


If you need more specific detail on any step just ask!

---

