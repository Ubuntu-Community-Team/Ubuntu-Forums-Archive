---
title: "Recovering data with testdisk"
date: 2019-12-24
forum: General Help
---

### Post by bcedrix on 2019-12-24
Hello,

Today I couldn't display my hardrive content (ntfs). Instead, with gparted, it shown a partition with no file system.
After searching the issue, I found several things to try:
- chkdsk E. /r /f (didn't work under windows 8)
- sudo [COLOR=#242729][FONT=Consolas]ntfsfix /dev/sdb (didn't work)
[/FONT][/COLOR]- sudo fsck -t ntfs /dev/sdb (didn't work)
Then I did something that partially worked:
```
**sudo testdisk /dev/sdb > Advanced > Boot > Repuild BS**
```
Now I can see most of the content of my harddrive. But I have a directory /media/cedric/MAIN_4TO/photo that is empty.
However, If I do again *sudo testdisk /dev/sdb > Advanced > Boot > List*
I can see the missing directory and files.
What shall I do to recover those ? Rebuild MS again ? Repair MTF ? Copy the directory somewhere else (very large directory) ?

Thanks in advance

---

### Post by yancek on 2019-12-24
You need to run ntfsfix on a partition not the drive, not sudo ntfsfix /dev/sdb but rather sudo ntfsfix /dev/sdb1 (change the 1 to the correct partition.  If you ran chkdsk from the proprietary windows OS on a partition (E) with a proprietary windows filesysteem (ntfs) and it failed, it is extremely unlikely that any Linux software such as ntfsfix is going to do the job.  ntfsfix is far more limited in what it can do than the windows chkdsk software.  If chkdsk doesn't help, you might continue trying test disk as they have very complete documentation on its use on their page.

You might try the microsoft support site or a windows forum to resolve your problem with windows .

---

### Post by bcedrix on 2019-12-24
Hello,
Thanks for your reply. I tried "[COLOR=#000000]sudo ntfsfix /dev/sdb1[/COLOR]" and it says
```
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
Checking the alternate boot sector... OK
NTFS volume version is 3.1.
NTFS partition /dev/sdb1 was processed successfully.
```
But my question is more about testdisk.
testdisk can see all of my missing directory and files. How to ask testdisk to restore it ?

[IMG]https://i.imgur.com/E2AbGzZ.jpg[/IMG]

---

### Post by oldfred on 2019-12-24
If you do not have good backups, I would back up from testdisk to another drive.

If chkdsk did not work, but testdisk had to restore BS - Boot sector, you generally then have to run chkdsk after that.

Linux cannot really fix most NTFS issues. Ntfsfix mostly just sets the chkdsk flag, so Windows runs chkdsk on a reboot if c: partition. If some other partition you may have to run chkdsk on that.

---

### Post by yancek on 2019-12-25
I referred to the testdisk documentation in my earlier post and the link is posted below.  Step by Step use of the software, had you not seen that?

[https://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](https://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by bcedrix on 2019-12-25
Hello,
"[COLOR=#000000]If chkdsk did not work, but testdisk had to restore BS - Boot sector, you generally then have to run chkdsk after that.[/COLOR]"
So I run again chkdsk. It deleted and fixed many things. Now my images directory was turned into an empty file.
I ran again testdisk. testdisk doesn't see my directory anymore (only an empty file).
So I guess now my data are lost or is there a chance to recover my images directory ?
"[COLOR=#000000] Step by Step use of the software, had you not seen that?"[/COLOR]
[COLOR=#000000]Yes but when you don't know how it works, you don't know what to try…[/COLOR]

---

### Post by dragonfly41 on 2019-12-25
> 
" or is there a chance to recover my images directory ?"


Go to the link posted by Yancek and try [Photorec link]("https://www.cgsecurity.org/wiki/PhotoRec") if you are attempting recovery of photos. Same principle applies .. save to external flash drive. Be aware that recovered files will lose filenames and other such data. 
But there are documented methods for reinstating their positions in the filesystem by inspecting metadata.

---

