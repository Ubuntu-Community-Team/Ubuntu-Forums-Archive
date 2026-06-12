---
title: "GnomeBaker can't burn DVD's"
date: 2005-07-14
forum: General Help
---

### Post by SlugO on 2005-07-14
I tried to burn a DVD-RW with GnomeBaker and got this error message:

The mount point (e.g. /mnt/cdrom) for the writing device could not be obtained. Please check that the writing device has an entry in /etc/fstab and then go to preferences and rescan for devices.

As far as I remember I haven't changed anything from fstab concerning the dvd-drive:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/windows  ntfs    umask=0222      0       0
``` 

And here's GnomeBaker's detected devices:
Name: HL-DT-ST DVDRAM GSA-4160B
Id: 1,0,0
Node: /dev/sr0
Mount point: [empty]
And the rest of the options are all checked.

I tried to change the mount point to a few different places but then it
just complained that they're not defined in mtab.

Nautilus's burner seems to work fine but it's not versatile enough for me.
So how could I get GnomeBaker to work?

---

### Post by SlugO on 2005-07-15
Anyone have any ideas?

---

### Post by SlugO on 2005-07-15
**bump bump**

Any advice would be appreciated.

There should be something in the UbuntuGuide
about configuring dvd-drives correctly...

---

### Post by crispingatiesa on 2005-07-15
Try using K3b , so far no problem at all. (and I'm using gnome not kde)

---

### Post by juicybananahead on 2005-11-19
Are you using an external USB writer? I have the same problem, but if I change the ID in Gnomebaker from 0,0,0 to /dev/scd0 it seems to work. Trouble is, I haven't figured out how to get Gnomebaker to automatically use this ID.

/juicy

---

