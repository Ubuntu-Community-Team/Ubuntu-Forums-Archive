---
title: "[SOLVED] Cloning XP to another HDD using NTFSCLONE - XP will freeze on login screen"
date: 2008-03-09
forum: General Help
---

### Post by perixx on 2008-03-09
Good evening, or good morning - depending on where you live... O:)

Perhaps somebody can help: I'm trying to clone XP (making a working backup) to another HDD's first primary partition, but it won't seem work out, as described here:
[http://www.linux-ntfs.org/doku.php?id=ntfsclone]("http://www.linux-ntfs.org/doku.php?id=ntfsclone")
[http://www.dominok.net/en/it/en.it.clonexp.html]("http://www.dominok.net/en/it/en.it.clonexp.html")

The difference from the procedure above and my experiment is, that I'm trying to clone XP back to but another HDD, yet on the first primary partition (so skewing the partition's starting point shouldn't be necessary). I used the following commands:
```
sudo ntfsclone -so XP.img /dev/hda1
``` 
To save XP from HDD1 (first partition) to an image in the special compressed file format.
```
sudo cat XP.img | ntfsclone -rO /dev/sda1 -
```
To recover that compressed image to the target partition on HDD 2 (first partition, formatted NTFS, size 34GB). I had to ```
chroot USER /dev/sda1
``` from 'root', to be able to carry out the recovery procedure first.

When trying to boot the cloned XP, I would only get to the blue login screen with a movable mouse arrow, only hard reset helped. Well, not exactly till to the login screen, only to the colorful blue screen with the XP logo, but no login dialog shown at all. Tried to edit the registy offline with UBCD4WIN, and removed all 'known mounted devices', as told, but no difference.

I noticed, that the 'recovered' XP partition will only reach the exact size of the old, backed-up partition (19GB); the rest of the (actually much larger) target partition is 'lost'. So I figured, I might try to manually edit and 'fix' the ending point of the target partition with 'Boot Builder' (did save both partition's boot sectors first), but that only resulted in having no more boot logo...   

So I'm kinda lost now; can XP clones only be realized on the very same HDD? Am I doing it wrong? Did changing the ownership of the target partition (which was actually needed to carry out the task in the first place) cause a mess?

:confused:
Please help!

perixx

---

### Post by perixx on 2008-03-10
HEHE, I'm making progress :¬)


I've took several different steps to get where I'm now, so I'll have to verify what exactly lead to success; I'm using /dev/sda1 as TARGET nad /dev/hda1 as SOURCE in my example - here's how:

**[COLOR="Teal"]Preparations:[/COLOR]**

[COLOR="Orange"]**1)**[/COLOR] You'll need to install the following packages, if you don't already have them:
- ntfsprogs (includes ntfsclone)
- ntfs-3g
- hexedit (simplified: needed, when cloning XP to partitions to others than the first, primary one)
```
sudo apt-get install ntfsprogs ntfs-3g hexedit
```

[COLOR="Orange"]**2)**[/COLOR] The TARGET partition was built with Gparted first, a little larger than the actual XP partition.

[COLOR="Orange"]**3)** Created a backup of the TARGET bootsector/MBR in a file on /media/sda5 for recovery purposes first, with ```
sudo dd if=/dev/sda1 of=/media/sda5/original_sda.mbr bs=446 count=1
```
[COLOR="Orange"]**4)**[/COLOR] Both TARGET and SOURCE need to be unmounted prior to the procedure, with > sudo umount /dev/[TARGET]
sudo umount /dev/[SOURCE]
[COLOR="Orange"]**5)**[/COLOR] the TARGET partition needs to be 'owned' before beginning: ```
sudo chown USER /dev/sda1
```


**[COLOR="Blue"]Procedure:[/COLOR]**

[COLOR="Orange"]**1)** the actual, DIRECT cloning command (no image file used): ```
sudo ntfsclone --overwrite /dev/sda1 /dev/hda1
``` This is done in TARGET-SOURCE format, unlike many other commands, be careful not to mix that up!!

[COLOR="Orange"]**2)**[/COLOR] Changing ownership back to 'root': ```
sudo chown root /dev/sda1
```

[COLOR="Orange"]**3)**[/COLOR] Rebooting into the XP installation-CD's recovery console (log into the appropriate Windows partition and do ```
chkdsk d: /p
exit
``` 

[COLOR="DarkGreen"]- Boot into a freshly cloned XP system!![/COLOR] :cool:


perixx

---

### Post by perixx on 2008-03-11
New problem...

Though I've managed to set up a running XP clone in the first place, it seems, that things gone awry by enlarging the questionable partition! 

I used Gparted zu 'inflate' the cloned NTFS partition (26GB) to the actual size of that I've put it into (34GB). After that, it wouldn't boot anymore, so I once again did a 'fixboot' and 'chkdsk' from the XP recovery console. 

Booting worked again, but when I took a closer look, I recognized that there's about 12GB of my user data in 'documents and settings' folder is missing; the data is actually still using the disk space (still 26GB 'in use'), but no data can be found anymore... 

I tried to delete all trash and tempfiles and defragmented the whole disk - the data is neither removed from the filesystem, nor does it show up again!

Who knows how this can happen??

perixx

---

### Post by perixx on 2008-03-17
The data-loss was FALSE ALARM :)

I had an ownership issue, probably due to copying the data with Ubuntu into the XP partition, or whatever. This prevented me from exploring the used disk space with Easy Cleaner... Anyway, after claiming ownership in XP pro, the problem was solved!

greetz,

perixx

---

### Post by perixx on 2008-03-25
Issue *SOLVED* :) 
For problems regarding NTFS resizing see also this thread:
[http://ubuntuforums.org/showpost.php?p=4497644&postcount=1]("http://ubuntuforums.org/showpost.php?p=4497644&postcount=1")

I'm gonna mark the thread as solved now, but will continue to post further experiences...


perixx

---

