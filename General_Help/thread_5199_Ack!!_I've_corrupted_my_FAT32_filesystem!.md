---
title: "Ack!! I've corrupted my FAT32 filesystem!"
date: 2004-11-16
forum: General Help
---

### Post by ming0 on 2004-11-16
I have all of my media (mp3s, videos, etc.) on a HDD formated as FAT32 (yes, I still boot into windows every once in a while), and just today i have found that things are VERY messed up.

When I try to play songs, about 60% of them work properly, 35% skip and don't play, and 5% are half the regular song, and the last half is some other random song from a totally different artist.

Can I do some sort of scandisk on the drive to fix things?  [-o< 

Oh, one other quirk--this drive has been unmounting itself and remounting as read only... I normally have it writable by my normal user, so I can rip CDs and DVDs to the drive and stuff.

Thanks in advance for the help!

---

### Post by p!=f on 2004-11-16
Do you play those songs from Windows or from Ubuntu Linux?
 Did you try to run filesystem check on Windows?
 How do you mount FAT32 partitions under Linux?
 Could you post your /etc/fstab here?

---

### Post by TravisNewman on 2004-11-16
[QUOTE=ming0]I have all of my media (mp3s, videos, etc.) on a HDD formated as FAT32 (yes, I still boot into windows every once in a while), and just today i have found that things are VERY messed up.

When I try to play songs, about 60% of them work properly, 35% skip and don't play, and 5% are half the regular song, and the last half is some other random song from a totally different artist.

Can I do some sort of scandisk on the drive to fix things?  [-o< 

Oh, one other quirk--this drive has been unmounting itself and remounting as read only... I normally have it writable by my normal user, so I can rip CDs and DVDs to the drive and stuff.

Thanks in advance for the help![/QUOTE]
 You say you still boot into windows... have you tried a scandisk there? I'd say the windows tools for fat32 would be better suited for it.

---

### Post by ming0 on 2004-11-16
Okay, I went into windows and checked it out--I did a chkdsk, and had no errors... I could play all files normally. Now I'm back in Ubuntu, and am still having problems, but not nearly as bad--now just a few songs won't play, and the songs aren't mixed together (that I've played, thus far), tho some songs sort of turn into jibberish and speed to the end.

I can't write to the media drive right now (tho I have in the past), and the other FAT32 drive I have is still writable (/mnt/project).
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               reiserfs defaults        0       1
/dev/hda3       /home           reiserfs defaults        0       2
/dev/hda4       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc1       /mnt/media      vfat    rw,users,uid=1000 0     0
/dev/sda1       /mnt/project    vfat    rw,users,uid=1000 0     0
/dev/hda1       /mnt/c          ntfs    ro,users,uid=1000 0     0
192.168.0.102:/net /mnt/net     nfs     rw,users,hard,intr 0     0

```

---

### Post by ming0 on 2004-11-16
I've been messing around, and here are some of the strange details of this filesystem:

1.) I can mount the drive and immediately write data to it, but as soon as I play a song or watch a video, I get the following error:
```
dean@dim:~ $ mkdir /mnt/media/tmp
mkdir: cannot create directory `/mnt/media/tmp': Read-only file system
``` 2.) Some of the media on the drive are unwatchable (in Ubuntu, NOT windows) while some are jumbled or messed up (partially viewable or listenable, but at times sound or look strange)
3.) I cannot fast forward any of the movies--the timeline in mplayer doesn't move
4.) When I try to copy files from the drive (onto the desktop, which is a different drive that is Reiserfs), I get the following dialogue: ```
Error "I/O error" while copying "/home/dean/...h - 01.avi".
``` 5.) My other nearly identical but smaller FAT 32 drive does NOT have these symptoms; it is always writable, nothing appears corrupt, and I can fast forward videos.

I'm know that I've been able to write to this drive with Ubuntu before--the problem seems to have popped up in the last few weeks... 

Anyone have anything similar, or any advice? Need more info? Thanks!

UPDATE:
I just ran fsck.vfat, and got some interesting results:
```

dean@dim:~ $ sudo fsck.vfat /dev/hdc1
Password:
dosfsck 2.10, 22 Sep 2003, FAT32, LFN
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT

```
Hope it helps

---

### Post by poptones on 2004-11-16
Dude, it would work ok in windows but not in linux? Why are you remounting it writable in linux? Why are you playing around writing data to the drive, possibly making the partition table even more confused?

Don't make it worse! Move the stuff (in windows, if it still works) to another drive, CDs, DVDs, laptop, whatever you need to do, then repartition, reformat, and reload. It doesn't have to become a big deal, but if you have a drive that's so fragged it keeps unmounting and mounting read only, you need to pay attention to what this is telling you about the drive or it WILL become a big deal.

---

### Post by ming0 on 2004-11-16
I guess I wasn't aware that writing w/ vfat was so touchy... 

The other problem is that I have something in excess of 100 GB on this disk, and no good way to push it onto ext3 or reiserfs. 

If I do find a place for the data to hang out while I format the drive,
I assume that I cannot just format it as FAT32 again? If I make it ext3, are there any applications I can use in windows to be able to read and write to it?

Thanks again for the feedback!

---

### Post by poptones on 2004-11-16
[QUOTE=ming0]I guess I wasn't aware that writing w/ vfat was so touchy... [/QUOTE]

It's not normally - but if your drive is so munged linux is mounting it r/o then it has a problem. and if it's crosslinking files and the problem began recently it's likely the drive is failing and you need to get that stuff off there while you can. Even if it's not failing, if it's this munged you need to back it up, use dd if=/dev/zero of=/dev/thishdd to wipe it clean, and hope rebuilding the file system is all it needs :)

If you want to access it in windows, you'll need to use fat32. Linux works just fine with fat32, but not if the drive is flaky.

I don't mean to be alarmist, but what I'm saying is it's quite possible you won't be accessing that drive at all very much longer. At the very least, if it's not working in linux but it's ok in windows, you need to do what you can to get that data backed up before it's toast in windows as well. DO NOT do a chkdisk on the drive until AFTER you get as much data as you can; I've seen lots of marginal drives go south while running recovery checks.

*The other problem is that I have something in excess of 100 GB on this disk, and no good way to push it onto ext3 or reiserfs. *

100GB is easy: buy a big fat rebate special drive at costco or office depot, backup your stuff, then sell it (or your old drive - after a good checkout, of course) on ebay and get your money back.

---

### Post by ming0 on 2004-11-17
:(  I suppose I'll borrow a drive and see what can be done...

computers are such a beeotch sometimes! :)

Again, thanks for the advice...

---

### Post by TravisNewman on 2004-11-17
Better yet, buy a big drive (from a chain, they ask less questions), back everything up, zero your old drive, partition it and make sure everything works, restore the backup, secure-wipe the data on the drive you recently purchased (meaning write zeros to everything, maybe doing a few passes just to be sure) and then take it back and tell them it wasn't compatible with your pc ;) That's if you want to be a bit shady.

---

### Post by zenwhen on 2004-11-17
Oh panickedthumb, you cad. ;)

---

