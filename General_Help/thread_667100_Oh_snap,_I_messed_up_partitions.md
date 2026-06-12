---
title: "Oh snap, I messed up partitions?"
date: 2008-01-14
forum: General Help
---

### Post by ryuzaki on 2008-01-14
I made the lame mistake of putting linux on one partition and I have no clue how to split up that partition so I can play some games like drift city, yugioh online, and other 3D thingy based games. Yes, I don't know anything about partitions. 

SO i was hoping someone could help me install windows on a like 15 gig partition...or first off make that partition so I can do so :S Oh and a screeny of my partition thing is attached >_>   

All help appreciated

-L 

:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by logos34 on 2008-01-14
You have to use Gparted from the ubuntu live cd (root cannot be mounted when you resize).  Shrink it down, then create a new partition out of the freed space and format it ntfs.  Or leave it unallocated and let windows do it.  (the latter if you're installing vista)

---

### Post by ryuzaki on 2008-01-14
I burned a live CD on a dvd and rebooted but nothing happened... T.T

---

### Post by logos34 on 2008-01-14
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

And after you install windows (assuming you get that far) you'll have to[ restore the grub bootloader]("http://ubuntuforums.org/showthread.php?t=224351") because windows will overwrite the mbr

---

### Post by Sef on 2008-01-14
> I burned a live CD on a dvd and rebooted but nothing happened... T.T

1) Did you burn it as an iso? 

2) Is your computer set to boot the cd before the hard drive?

---

### Post by Ubuntized! on 2008-01-14
You said you did burn an iso image of ubuntu on a cd, is that right? 
Well then... reboot your PC and then, when you see some weird things on your monitor, like the manufaturer of your pc and things like primary master and secondary slave.......quickly hit 'Delete' (it is a key just above the cursor keys) until u get to a usually blue screen with some menus! Once there you should look for an entry like 'primary (or first it depends) boot device' and set that entry to CDROM (or smthg like that). Then set the second boot device to HD! Save to bios and exit! Now your pc will reboot. Make sure you have already inserted the live dvd into the reader. Then press 'Start or Install Ubuntu' when asked

Lemme know...:guitar:

---

