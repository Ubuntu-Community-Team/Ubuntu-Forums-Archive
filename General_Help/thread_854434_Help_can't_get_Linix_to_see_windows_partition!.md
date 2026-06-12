---
title: "Help can't get Linix to see windows partition!"
date: 2008-07-09
forum: General Help
---

### Post by rauhjam on 2008-07-09
I'm very new at Linix..but not new on computers. I decided I wanted to try Linix...so I downloaded Xubuntu and duel booted it with Windows 2000 pro.  Everything seems to work fine.  Love linix! The first week I had it up, I could even go and look at my windows partition from Linix, but of course can't see Linix from Windows.  But now somehow, while playing around learning about Linux... I made the icon for the   Windows partition disapear and can't find it showing up in the file system anywhere.  Don't know what I did and don't know how to get it back. I can still boot up into windows and everyhting is there.  both partitions work fine...just that now Linix can't read that partition or so it seems.  I used to be able to take files in from Linix and place them into the windows files folders.  I did this cause I didn't have Windows set up for internet and I did have Linix set up for it. Anyway, now I can't do that.  Any idea how to get Linix to read my Windows partition again? Would appreciate it!

-James Rauh 

Edit Bodhi.zazen : James, unless you are wanting spam, best not post your e-mail address on public forums :)

---

### Post by bodhi.zazen on 2008-07-09
Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ]("http://www.psychocats.net/ubuntu/mountwindows")
For read-write: 
[LIST=1]
[*]vfat (FAT) use dmask=027,fmask=137[INDENT]more permissive permissions : dmask=000,fmask=111[/INDENT]
[*]ntfs use [ntfs-3g]("http://ubuntuforums.org/showthread.php?t=217009") and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)[INDENT][http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)[/INDENT]
[/LIST]

---

