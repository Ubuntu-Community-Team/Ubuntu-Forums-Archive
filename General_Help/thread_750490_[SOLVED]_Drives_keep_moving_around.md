---
title: "[SOLVED] Drives keep moving around"
date: 2008-04-09
forum: General Help
---

### Post by Wastedyouthfx0 on 2008-04-09
Hello, I moved my home partition to another drive and added that drive to the /etc/fstab so it would automount.  While I was in there poking around like a newbie, I added my third drive also.  I even rebooted to make sure it all worked right, and everything seemed okay for a day or so until the next reboot.  During boot it drops to a recovery console and doesn't load ex, claiming that fsck can't check a drive because its in use.  I'm new to Linux, so pardon my terminology.  I can continue onto X if I just mount my /home directory manually.  The error seems to be caused by my drives moving around.

So, at my last boot: /dev/sdb1 was /, /dev/sdc1 was /home, and /dev/sdb1 was /media/disk.

After rebooting, they all moved to different places.  / is mounted at /dev/sda1, and /home is at /dev/sdb1.

Is it normal for the "drive letters" to change around randomly like that?  I can't mount them in fstab because they seem to keep changing.  I have a hard time mounting them manually because I keep having to guess which device holds my /home data.  Are there commands like "df" that will make that easier also?  

Any help would be appreciated.  At least I don't have to reboot often =)

---

### Post by drdrewdown on 2008-04-09
Wastedyouthfx0,

this is a common problem that i ran into a couple years ago on my big server.

you need to go back into your /etc/fstab & make a few changes.

the fix is setting UUID's for each drive & path so they never change..

if you do a quick search on google or this forum you will find the necessary changes you need to make..  there is a command to determine the UUID (it escapes me at this time sorry) of each drive & you will set that up in fstab.. there is alot of information out there regarding this..

i apologize for not linking you to the proper location but i dont have time to...


once you setup this information in fstab you will not have any more problems.. 
good luck

---

### Post by davidpbrown on 2008-04-09
You can get UUID's with..
```
ls /dev/disk/by-uuid/ -alh
```

---

### Post by Wastedyouthfx0 on 2008-04-09
Thanks guys!  That was just enough info for me to get it fixed.  The ls /dev/disk/by-uuid/ -alh gave me a list of UUID's.  Strangely enough, when I took a second look at my fstab, the old way root had been mounted was commeted out and the UUID method for mounting was being used.  I swear it wasn't like that this morning, but perhaps I'm just crazy.  I heard that a driver has changed that handles both SATA and PATA, and perhaps this happened when the drives went from hda to sda.

I mounted the other drives using that as an example and I can now boot normally and everything is in its place.  Ubuntu is keeping me on my toes lately, but I actually appreciate the chance to learn how everything works.  Thanks for taking the time to help me!

Here is my new fstab.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=b3045d4b-c9cd-49b6-8dbe-7478703a8a75 /               ext3    errors=remount
-ro 0       1
# /dev/hda5
UUID=e6c0c3d6-948b-4943-8457-127c384c02c4 none            swap    sw            
  0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#/dev/sdc1 	/home 		ext3 defaults,errors=remount-ro 0 1
UUID=1966839c-6e88-47eb-b037-f97ab9ce165b /media/disk ext3 defaults,errors=remou
nt-ro 0 1
#/dev/sda1	/media/disk	ext3 defaults,errors=remount-ro 0 1
UUID=4155fe14-c3ce-440b-ae93-fda3d6a566ec /home ext3 defaults,errors=remount-ro 
0 1



```

---

