---
title: "Install Ubuntu on a software RAID array?"
date: 2006-07-18
forum: General Help
---

### Post by cleentrax on 2006-07-18
I have four 320gb drives ready to set up as a software RAID-5 array. I can figure out how to configure them in an array, but I can't figure out how to get Ubuntu installed on the array without using an additional boot drive. I can't add a fifth hard drive as the system may not handle the power/heat.

I've been trawling the blogosphere and the wiki/forum, but I can't find any definitive answer or tutorial.
 
Is this possible?

---

### Post by modernmystic on 2006-07-18
Okay, I'm gonna take a wack at this, but I should warn you, I'm nowhere near even a modest ubuntu user :D and this understanding only comes from using RAID0 so hopefully it'll still apply.

If you're using breezy and as you've said, you can setup the raid partitions and the swap (if you're gonna use any), then to really activate the raids, you have to simply go to the top of the menu in the partition manager and select "Configure software RAID", which will create a new RAID partition at the bottom of the list that should have the combined sizes of your other partitions. This is what you can set as root.

Hopefully this helps a little and I didn't just screw you up.
Good luck,
-Brad

---

### Post by zitch on 2006-07-18
The only software RAID that can boot is a RAID1, AFAIK.  If you wish to use all four drives in a RAID5 type setup, you will need to reserve some space (I'd recommend about 200 MB) on at least two of the drives to use as your /boot partition.  (Is it possible to run a mirror across all four drives?  If so, I'd actually recommend that).  The rest of the drives (after the initial 200 MBs) should be available to be freely used for your RAID5 setup.

Hope that helps some.

---

### Post by cleentrax on 2006-07-18
I don't think I can do a RAID 1 across four drives, but I suppose I could do two RAID 1's on two drives each, leaving identical partitions on all four for the RAID 5. That's what I'll try... Thanks!


> **zitch said:**
> The only software RAID that can boot is a RAID1, AFAIK.  If you wish to use all four drives in a RAID5 type setup, you will need to reserve some space (I'd recommend about 200 MB) on at least two of the drives to use as your /boot partition.  (Is it possible to run a mirror across all four drives?  If so, I'd actually recommend that).  The rest of the drives (after the initial 200 MBs) should be available to be freely used for your RAID5 setup.

Hope that helps some.

---

### Post by modernmystic on 2006-07-18
lol, thanks for catching that. Oddly enough, I had just made that mistake a few hours ago and it still didn't seem to update in my mind.
-Brad

---

### Post by RAOF on 2006-07-18
The wiki has this howto for installing and booting from software raid of all kinds (0, 1, 5, etc).

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

