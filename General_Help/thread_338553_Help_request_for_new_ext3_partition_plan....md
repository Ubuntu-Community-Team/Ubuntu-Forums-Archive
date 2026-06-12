---
title: "Help request for new ext3 partition plan..."
date: 2007-01-14
forum: General Help
---

### Post by floke on 2007-01-14
I am planning to set up a separate ext3 partition on which to store my documents, and to keep my system files (ubuntu etc.) on a separate partition. The problem is that I am trying to set this up within an existing dual-boot system (actually it's dual boot in name only, since in reality its single-Ubuntu-always boot - Windows partition be warned, your days are numbered!).

Ok, here's the setup and the plan. My hard drive looks like this


hda 1 = NTFS (24.51G) (used 15.17G)
hda 2 = ext3 (12.2G) (used 4.32G)
hda 3 = extended partition 564.79 mb
 - hda5 linux swap 564.75 m

The plan is...

 (a) to use GParted to resize the NTFS partition down to 17G, and to use the rest as the ext3 partition (actually am considering shrinking the hda2 ext3 partition as well and merging it with the space robbed from NTFS - can I do this? It is tricky?)

(b) to use the new space as an ext3 partition to be mounted in ubuntu on which to keep my documents etc. (I might also need advice on mounting this but that can be sorted later)

The question, then, is ... if I do this will the new partition be named hda2, and my existing hda2 shifted to hda3 etc., - and, if so, will this mess up my GRUB file, which currently locates ubuntu on hda2 - i.e. will I need to edit this to tell it to boot from hda3? And if so, at what stage of the process to I edit GRUB?

Any help on this (or even a shove in the direction of a HowTo) will be very much appreciated

Thanks in advance

---

### Post by logos34 on 2007-01-14
there shouldn't be a problem since windows and / are contiguous...You can expand hda2 into the freed up space or create a new ext3 partition, in which case it'll probably be called hda4 or 6...If you shrink hda2, I think (not sure) you will end up with space on the other side between it and your extended partition.

---

### Post by floke on 2007-01-15
So I shouldn't have to edit GRUB?
(If it turns out that I do - how would I be able to do this after the event, given that I wouldn't be able to boot into Ubuntu - i.e. if the drive number it wants to boot from has changed? - Could I do this through Knoppix or the Live Edgy CD?)

Thanks for the advice

---

### Post by Rui Pais on 2007-01-15
hi,
as far as i know you got 2 possibilities. 
Either you mess with grub and /etc/fstab or you managed to get the disc with partition with a messed order. 

This last option seems to me the harder. 
You would need to make and format the partition by hand in a terminal. Even if you don't mind to do that if you later use a tool like gParted (that automaticaly reorder partitions) to make any change, like change a size, it will reorder you partition numbers and you eventually have to fix things...

The best and easy way would be do what you pretend with gParted from a liveCD, make the new partition, mount the new hda3 (old hda2) and edit (only 2 files):
<your_mount_point>/boot/menu.lst  
 -> changing all **(hd0,1) to (hd0,2)**

<your_mount_point>/etc/fstab   
  -> changing **hda2 to hd3**
  -> changing **hda5 to hd6**

In case you are using edgy or later you need only to check the hda UUIDs. 
type vol_id /dev/hda3 | grep UUID
and check if UUID is the same of the one on /etc/fstab (change to new if its different)
repeat to the new hda6.

Maybe it sounds hard, but it's quit easy (assuming you have only one Linux on hda2 as you post). 
Once i did that, recovering space from a Windows that i not used anymore and have to change 5 o 6 different Linuxs installations on the disc :lol:

---

### Post by Rui Pais on 2007-01-15
hi,
as far as i know i got 2 possibilities. 
Either you mess with grub and /etc/fstab or you managed to get the disc with partition with a messed order. 

This last option seems to me the harder. Requires that you manage to make and format the partition by hand in a terminal. Even if you don't mind to do that if you later use a tool like gParted (that automaticaly reorder partitions) to make any change, like change a size, it will reorder you partition numbers and you eventually have to fix things...

The best and easy way would be do what you pretend with gParted from a liveCD, make the new partition, mount the new hda3 (old hda2) and edit (only 2 files):
<your_mount_point>/boot/menu.lst  
 -> changing all (hd0,1) to (hd0,2)

<your_mount_point>/etc/fstab   
  -> changing hda2 to hd3
  -> changing hda5 to hd6

In case you are using edgy or later you need only to check the hda UUIDs. 
type vol_id /dev/hda3 | grep UUID
and check if UUID is the same of the one on /etc/fstab (change to new if its different)
repeat to the new hda6.

Maybe it sounds hard, but it's quit easy (assuming you have only one Linux on hda2 as you post). 
Once i did that, recovering space from a Windows that i not used anymore and have to change 5 o 6 different Linuxs installations on the disc :lol:



EDIT:
 you can only do this from a liveCD!! Not from your mounted OS!

---

### Post by floke on 2007-01-15
All sorted. 

I resized my Windows partition, and turned the extra space into an ext3 partition (to use as my new home directory). This did not change the /dev/hda number of my existing ubuntu partition so didn't need to edit GRUB.

i then followed the steps shown here... 

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

which gave me problems concerning the permissions to access my Home directory - meaning that I couldn't access it without messing around as root ](*,)
 
I then followed some of the steps shown in the forum to deal with this, and ended up being unable to log-in at all (all these chowns mucked things up!). Was then getting the 'less than 10 seconds' login error etc. ](*,) 

So, I logged in as safe terminal mode, ran nautilus as 'sudo', and deleted all my .kde, .gnome, .gconf filed as well as the .ICEauthority file for good luck. 

Restarted and :mrgreen:  all's good. I have ubuntu on my usual partition, with my home directory on a different partition. 

Vive la Linux!

---

