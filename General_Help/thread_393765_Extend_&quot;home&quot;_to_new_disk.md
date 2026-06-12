---
title: "Extend &quot;home&quot; to new disk"
date: 2007-03-26
forum: General Help
---

### Post by Mirtma on 2007-03-26
Hello! I've installed Ubuntu file server (only terminal access) with help from this great guide: [http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10) . I've added new HDD. Because "home" from first disk is network share, I wonder is it possible, to add all free space from second disk to "home" quotta?

---

### Post by kidders on 2007-03-26
Hi there and welcome,

Adding the space on a local hard disk to a network share on another computer is doable, but may or may not be safe, depending on how you want to do it. What do you have in mind?

---

### Post by Rui Pais on 2007-03-26
> **Mirtma said:**
> Hello! I've installed Ubuntu file server (only terminal access) with help from this great guide: [http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10) . I've added new HDD. Because "home" from first disk is network share, I wonder is it possible, to add all free space from second disk to "home" quotta?

you can make a partition with the free space on new hdd, and a folder in home partition with some meaningful name and mount the partition there and use it. 

As an example, a folder named Documents could be used as mount point and could be used as a store to docs you made, keep them in one place, without crowd your home folder, and that can be easily access by other linux installations with eventually made. Files named Documents appears on the desktop too (if you use gnome) as a special folder, like home folder, Computer or trash.

---

### Post by kidders on 2007-03-26
> **Rui Pais said:**
> As an example, a folder named Documents could be used to mount point and could be used as a store to docs you made, keepe them in one place, without crude your home folder, and that can be easily access by other linux installations with eventually made. Files named Documents appers on the desktop too (if you use gnome) as a special folder, like home folder, Computer or trash.Unfortunately, I'm not sure that's likely to be workable. :-( The poster presumably needs to share the space between multiple (ie possibly hundreds of) users. Also, the quota requirement seems to suggest a RAID-based solution. On top of that (and assuming I'm reading the o/p correctly), the two hard disks are in different computers, which complicates things.

---

### Post by Mirtma on 2007-03-26
I have domain with Windows 2003 server and 10 XP computers . I need file server, so I install Ubuntu server on one PC to made one. Everything works perfect. I have one map that I share on net and all users can access it. Because I need a lot of space in that map, I want to add another HDD and (if possible) extend existing map to new hdd. And both hdd's are in same computer.

---

### Post by Rui Pais on 2007-03-26
> **kidders said:**
> Unfortunately, I'm not sure that's likely to be workable. :-( The poster presumably needs to share the space between multiple (ie possibly hundreds of) users. Also, the quota requirement seems to suggest a RAID-based solution. On top of that (and assuming I'm reading the o/p correctly), the two hard disks are in different computers, which complicates things.

I was just give a suggestion for use the free space without change home :) 

Well one can always mount partition from several points on a network... the only problem that can be raised is that OP don't have access as administrator to that machines. 
Quota shouldn't be a problem since the extra space came from another partitions... or am i'm wrong here? (don't have much experience on that, sorry :() 
please ignore my suggestion if it looks not much practicable.

---

### Post by kidders on 2007-03-26
Hey again,

Just to clarify...> **Mirtma said:**
> Because "home" from first disk is network share, I wonder is it possible, to add all free space from second disk to "home" quotta?Do you mean to say that the you want to add space to a *remote* filesystem?

Also...> **Mirtma said:**
> I want to add another HDD and (if possible) extend existing map to new hdd.What kind of "map" are you referring to?

In any case, I would suggest using RAID. The only problem with that is that spreading a filesystem across two hard disks doubles (obviously) its failure probability, so I would not recommend using that solution unless you are willing to add *two* more hard disks, rather than just one.

A somewhat messier alternative would be to split your users into two groups, and store each group on a different disk. That way, the probability of losing any given user's files would remain about the same... but things would be much more complicated to administer!

What kind of solution did you have in mind?

---

### Post by Mirtma on 2007-03-26
I made linux file server on Windows domain network. That server only purpose is to share one directory to all users because it contains a lot of pictures (archive). I need more space on that same server and I don't want to create new directory and new share (so that it wouldn't be confusing for users - they should not see any change, except more free space in directory). 

Sorry for my poor English... I know it causes problems with understanding what I want to do....:confused:

---

### Post by kidders on 2007-03-26
> **Mirtma said:**
> Sorry for my poor English... I know it causes problems with understanding what I want to do....:confused:Don't worry. If you can manage to successfully express subtle distinctions between different sorts of file sharing solutions, you should be proud of yourself! :-P Also, don't forget to ask people to rephrase things, if you can't figure out what they mean.

Anyhow, it seems like the only acceptable solution for you is RAID-based. In case you don't know what I'm talking about...

[LIST]
[*]RAID lets you create large filesystems, using multiple smaller physical devices.
[*]When done properly, RAID can increase the performance and reliability of your filesystems.
[*]Unfortunately, two-disk RAID sets are often either (a) wasteful, because one disk mirrors the other, or (b) dangerous, because no disaster recovery information is being maintained, despite the _massive_ increase in failure probability.
[/LIST]

In my opinion (Rui Pais may have another option), the ideal solution would be to add _two_ more disks (instead of only one). You would use the space from two to increase (maybe double) the size of your fileshare, and "waste" the space from the third, to allow you to recover cleanly from various failure scenarios (ie the **RAID 5** model). Would this be possible?

Specifically, you would need three partitions, all of which are *exactly* the same size, and an application called **mdadm** to set up RAID in software (rather than using a hardware-based solution). Software RAID has the advantage of being relatively bug-free, and readily portable, in the event of a server failure.

How does that sound?

---

### Post by Mirtma on 2007-03-26
Thank you for all effort. It looks like RAID will be final solution. Well, I saved around 1.000 € for using Ubuntu instead WinSBS... I could buy more HDDs.. ;) Thank's again @kidders & Rui Pais!

---

