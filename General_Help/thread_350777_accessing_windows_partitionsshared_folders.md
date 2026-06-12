---
title: "accessing windows partitions/shared folders?"
date: 2007-02-01
forum: General Help
---

### Post by Mygly on 2007-02-01
Hey, last time I had ubuntu installed I seem to remember being able to access my music somehow from my windows partition or else it was a windows shared folder. Is there any way I can access the music that's in a shared folder on my own machine through linux? I remember something about samba being the name of something i used. I don't remember if it was on my own machine or on my brothers, who had backed up a lot of my files for a time. I'd really love to be able to have music and video in some folder that could be accessed by linux and windows. I'm not sure how to do this. Anyone know how it might be done? Thanks.

---

### Post by chriscando on 2007-02-01
Im guessing you are dual booting Linux and windows since you said that windows is on another partition. If this is the case you won't need samba (thats for file sharing with a windows computer over a network), hopefully your windows partition is mounted already, the default location is something like /media. So see if you can just use your file manager (Nautilus) to goto /meda and check the folders there.

If not we can try something else.

---

### Post by Mygly on 2007-02-01
The only thing I can find in /media is cdrom, cdrom0, floppy, and floppy0. Perhaps I did something wrong during installation? I remember last I had Ubuntu installed being able to access the music and videos, etc. fairly easily. Any other ideas? Thanks.

Edit: I found this [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows), will that do it? I didn't read very much of it yet just skimmed it a bit.

---

### Post by Mygly on 2007-02-01
Following the link above I get stuck after it says > Note: Starting with Edgy Eft (Ubuntu 6.10), the appearance of the /etc/fstab file has changed a bit, but the principle still remains. Instead of looking like this:
This mostly is referring to versions before 6.10 and since Edgy's fstab is a little different, I can't figure it out. my [COLOR="Blue"]fdisk -l[/COLOR] returns this > Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1            3381       19457   129138502+   7  HPFS/NTFS
/dev/hdb2               1         783     6289416   83  Linux
/dev/hdb3             784        2089    10490445   82  Linux swap / Solaris
/dev/hdb4            2090        3380    10369957+  83  Linux

Can you guys help? I'd like to mount both my windows partitions. Thanks.

---

### Post by dexter on 2007-02-01
Do you have a line that mounts /dev/hdb1 (your windows partition) in /etc/fstab ? If not, create a folder in /media (eg windowsdisk) and add this line to your /etc/fstab
```

/dev/hdb1  /media/windowsdisk  ntfs   defaults,nls=utf8,umask=007,gid=46   0   1

```

---

### Post by Mygly on 2007-02-01
I did not have a line that mounted /dev/hdb1, so I did as you said and it worked. Now what if I wanted to mount my other windows partition? the one at /dev/hda1? how do you know what to make the [COLOR="Blue"]unmask[/COLOR] and [COLOR="Blue"]gid[/COLOR] values?

---

