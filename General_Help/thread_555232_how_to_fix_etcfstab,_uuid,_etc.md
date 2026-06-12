---
title: "how to fix /etc/fstab, uuid, etc?"
date: 2007-09-19
forum: General Help
---

### Post by eclectic4 on 2007-09-19
Hi, Folks,

A few weeks ago I wiped out my old Windows partitions, reformatting them to ext3.  But then they were not mounted automatically.  I am using them all for various media storage (sound and video files, etc.) and so would like them automatically available to me as /home is.  

I tried to edit /etc/fstab, and forgot to back it up first, but then the system would not boot.  I am running Ubuntu 7.04.  I got it running again by making etc/fstab.edgy into /etc/fstab,   I can boot my newly reformatted partitions by mounting them manually every time, but I would like to have /etc/fstab reflect reality and my needs.  Also, my cdrom is now not mounting automatically, which I need it to do.

When I tried to edit /etc/fstab, I simply changed the lines for the three refomatted partitions to match the settings for /home, but this resulted in the system not booting.

I have tried to figure this out for myself, and am getting nowhere.  I thought the problem might lie with those uuid labels, so I researched that, and tried the vol_id command, but I get this every time:

```
vol_id /dev/hda1
/dev/hda1: error open volume

```

here is /etc/fstab, with some irrelevant partitions omitted for brevity:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=26c1b742-6d2e-41c1-888d-8ef36f46224c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda12
UUID=d2d72513-1637-4c42-9ded-4a4ded8b01de /home           ext3    defaults        0       2
# /dev/hda1
UUID=2E71-1BF7  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=F2CCDAD6CCDA93E7 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=241C-4832  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
....
# /dev/hda13
UUID=c6050fb4-69a3-40c9-a56b-a490ba4ca5d4 none            swap    sw              0       0
# /dev/hda8
UUID=1be62bd8-eb00-4fc4-9a36-dc5de18c248b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

hda1, 5 and 6 are actually now ext3.

I read somewhere that I could just comment out the uuid's (switching the uuids with the "file system" label, like /dev/hda1, I suppose?) and it would work.  And I am tempted to just change noauto to auto for hdc.  But I'd rather follow accurate instructions than break it again, if I could find some.

Now I'm more confused.  I am quite sure I reformatted hda1, 5 and 6 to ext3, with cfdisk, I believe.  Just now I used fdisk to look at my partitions and it says they are still vfat & ntfs!  Does fdisk get it's info from fstab instead of reading the hard drive? I mounted these partions with the command:
```
 sudo mount -t ext3 /dev/hda1 /media/hda1
```
etc.  Right clicking the shortcuts on the Desktop and going to Properties, shows them as ext3.
   
And I am surprised to see I have TWO swap partions (where, it seems, none are really needed, with my usage of 1G RAM).  
  
Please help me to understand and fix this.

Thanks, 

Bill

---

### Post by prince_niceguy on 2007-09-19
yes it is safe to change the uuid's

can you post the /dev/hda you are having and what mount point you want to mount the volumes to?

if you can post that i can give you the fstab will look like.

---

### Post by eclectic4 on 2007-09-19
I'm not sure what you mean by:
> can you post the /dev/hda you are having

But maybe this output from fdisk is what you mean:
```
Disk /dev/hda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   c  W95 FAT32 (LBA)
/dev/hda2            1913       20023   145476607+   f  W95 Ext'd (LBA)
/dev/hda5            1913        3834    15438433+   7  HPFS/NTFS
/dev/hda6            3835        7530    29688088+   b  W95 FAT32
/dev/hda7            7531        7631      811251   83  Linux
/dev/hda8            7632        7834     1630566   82  Linux swap / Solaris
/dev/hda9            7835        9162    10667128+  83  Linux
/dev/hda10           9163       10703    12378051   83  Linux
/dev/hda11          10704       11354     5229126   83  Linux
/dev/hda12          11355       16508    41399473+  83  Linux
/dev/hda13          16509       16770     2104483+  82  Linux swap / Solaris
/dev/hda14          16771       20023    26129691   83  Linux

```

The mount points I am using are:

/dev/hda1 /media/hda1 
/dev/hda6 /media/hda6
/dev/hda5 /media/hda5

Can I just change cdrom (and floppy, I suppose) from "noauto" to "auto" as well?

I'm wondering where the official instructions for doing this are.  

Well, thanks for your quick response!

---

### Post by logos34 on 2007-09-19
Could you post your fdisk (even if wrong)?  Not sure why it's still showing the partitions with their old filesystem types.  

The cdrom can't automount unless there's a disc (containing a filsystem) loaded...You want the 'noauto' option (otherwise you'll have a problem when there's no cd iin tray)...To have it automount cd/dvd's go to system>prefs>removable drives and media>check 'mount removable media when inserted'.  

Take out one of the swaps...But you really should leave one no matter how much ram you have.  

prince_niceguy is right, it is safe to change the uuid's.  To find the new ones:
[B]
ls -l /dev/disk/by-uuid[/B]

But you don't need them...frankly I'd just take them out and use a line like this for each:
[B]
/dev/hda1 /media/hda1 ext3 defaults 0 0[/B]

the original mount points should be fine

do the same for the other two

the floppy line should read '/dev**/fd0 **...'

---

### Post by psusi on 2007-09-19
fdisk only looks at the partition table.  The partition table has a byte to describe the partition type.  Microsoft defined one value for fat, and one for ntfs.  Linux just uses the value of 83.  Other than fdisk, Linux does not look at the tag byte, it will mount whatever filesystem you tell it to on any partition.  

You want your cdrom and floppy set to auto so they will auto mount.  Or you can remote the line for them entirely and they will still auto mount.

By the way, why do you have 14 partitions?  That's an awful lot.

---

### Post by eclectic4 on 2007-09-19
If I want to run without uuid's (I've read they are designed for situations with more devices than I am likely to ever have) can I just remove all of them, for all my partitions?  

As you see from fdisk, I made a lot of partitions.  Yeah, I overdid it.  I heard recommendations for putting /var, /tmp, etc, on different partitions, and didn't realize that was really for server security, and not needed for desktops.  It would be a hassle to change it now.

---

### Post by rsambuca on 2007-09-19
Yeah, I have removed mine since I like to test out a lot of distros.

---

### Post by eclectic4 on 2007-09-19
Yaaaay!  I've rebooted with my new fstab, and all is well with that.

Thanks to all ya'll!

:guitar:

---

### Post by logos34 on 2007-09-20
> **psusi said:**
> You want your cdrom and floppy set to auto so they will auto mount.  Or you can remote the line for them entirely and they will still auto mount.

Here's what tuxfiles site [recommends]("http://www.tuxfiles.org/linuxhelp/fstab.html"):

"Also note that the **noauto** option is used with the floppy and CD-ROM. This means that they won't be automatically mounted when your Linux system boots up. This is useful for removable media, because sometimes there won't be any floppy or CD-ROM when you boot up your system, so there isn't any reason to try to mount something that doesn't even exist."

That makes sense to me, so that's why I leave the standard entries in fstab.  Configure the desktop preferences to handle automounting or not.

---

### Post by eclectic4 on 2007-09-20
At some point recently when I inserted a cdrom, the system was not responding to it as usual by automatically mounting it and popping up a file manager, or showing the disk on the desktop.  I thought this was related to the "noauto" option in fstab, but I see that I was wrong about that.  Something else caused this.

I am learning to use VMware, and the guest system was running slowly, and the manual said try turning off cdrom recognition, which I did, and I think somehow that interfered with the host systems recognition of the cdrom.  I have to digest the manual more thoroughly.  On a previous attempt with VMware, it's use of my network card interfered with the main network access.  I'm not sure of any of this, and need to fool with it more.

---

### Post by bodhi.zazen on 2007-09-20
> **logos34 said:**
> prince_niceguy is right, it is safe to change the uuid's.  To find the new ones:
[B]
ls -l /dev/disk/by-uuid[/B]

FYI, you can also blkid :```
sudo blkid
```

It is shorter to type :twisted:

---

### Post by stanz on 2008-05-02
hummm....so no more labels?
I'm finding conflicting information about replacing id's back to the old.
It lacked info on replacing them in the fstab file -- so I didn't proceed.
id's are so confusing...labels are clear.
oh`well.

:)

---

### Post by bodhi.zazen on 2008-05-02
> **stanz said:**
> hummm....so no more labels?
I'm finding conflicting information about replacing id's back to the old.
It lacked info on replacing them in the fstab file -- so I didn't proceed.
id's are so confusing...labels are clear.
oh`well.

:)

Labels work just fine.

mount LABEL=ZIP /media/Zip\ Drive

LABEL=ZIP /media/Zip\ Drive -t vfat users,uid=1000,gid=100,umask=007 0 0

---

### Post by stanz on 2008-05-07
Thanks for the response bodhi, but I'm looking for more of the rhythm and reason.
I'll need to explain better--when time permits.
And continue finding the difference between the '/dev', and '/media' mounting theory.

Just some newbie thoughts,,,,, ;)

---

