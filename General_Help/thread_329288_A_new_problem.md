---
title: "A new problem"
date: 2007-01-01
forum: General Help
---

### Post by b1ackhawk on 2007-01-01
I've edited the fstab and instantly found a problem with my edit. i typed mount -a and it told me this

mount: wrong fs type, bad optioni, bad superblock on /dev/disk/by-uuid/12E05745E0572DEB,
                  missing codepage or other error
                  In some cases useful info is found in syslog - try
                  dmesg |  tail   or  so


im trying to mount a storage partition on my slave drive

---

### Post by taurus on 2007-01-01
Can you post your /etc/fstab here?

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

---

### Post by b1ackhawk on 2007-01-01
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd5
UUID=af4e8a70-737c-4671-9d94-23a7ca7d0110 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd6
UUID=9e29e61b-a316-4ca2-adbf-1181b1cfa36e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/hdd1
UUID=12E05745E0572DEB    /media  ext3   ro   0   0




i believe thats what you wanted?

---

### Post by kidders on 2007-01-01
Hi there,

If you could also post the output of **sudo vol_id /dev/disk/by-uuid/12E05745E0572DEB**, that would also be helpful.

**Edit:** It's also worth noting that mounting this filesystem at /media will probably render mounted CDs inaccessible. You should choose a different location.

---

### Post by taurus on 2007-01-01
I would change the last line in /etc/fstab from

```
UUID=12E05745E0572DEB /media ext3 ro 0 0
```
to
```
/dev/hdd1   /media/share   ext3   defaults   0   1
```
Then, create a new mount point for it.

```
sudo mkdir /media/share
```
You can edit /etc/fstab by running

```
gksudo gedit /etc/fstab
```

---

### Post by b1ackhawk on 2007-01-01
/dev/disk/by-uuid/12E5745E0572DEB: error open volume

---

### Post by kidders on 2007-01-01
Hmm... the UUID you're pointing to in /etc/fstab doesn't seem to exist. How did you determine it?

---

### Post by b1ackhawk on 2007-01-01
i did the change (although gksudo didntwork, i just used sudo) and it gave me another one of those mounting superblock errors

"bad superblock"?

---

### Post by b1ackhawk on 2007-01-01
its the name of hdd1 in the dev/disk/by-uuid

---

### Post by kidders on 2007-01-01
Sorry to ask you for yet one more thing, but can we see **sudo fdisk -l /dev/hdd**, please? I'm just trying to make sure everything is as it should be. :-)

---

### Post by b1ackhawk on 2007-01-01
Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
     
    Device Boot          Start          End            Blocks          Id       System
/dev/hdd1                    1              28871   231906276     7        HPFS/NTFS
/dev/hdd2                 28872        30401    12289725      f            W95 Ext'd (LBA)
/dev/hdd5                 28872        30359    11952328+   83        Linux
/dev/hdd6                 30360        30401       337333+     82       Linux swap  /  Solaris



hope thats what you need. no problem doin in if it helps

---

### Post by kidders on 2007-01-01
It looks as though the filesystem you're trying to mount is NTFS, but your /etc/fstab says it's Ext3. Try correcting your /etc/fstab.

---

### Post by b1ackhawk on 2007-01-01
NTFS is called an unknown file system type

---

### Post by kidders on 2007-01-01
:confused: Could you post your new /etc/fstab?

---

### Post by b1ackhawk on 2007-01-01
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd5
UUID=af4e8a70-737c-4671-9d94-23a7ca7d0110 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd6
UUID=9e29e61b-a316-4ca2-adbf-1181b1cfa36e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/hdd1
/dev/hdd1   /media/share   NTFS   defaults   0   1



i know whatever is wrong is just a stupid mistake...somewhere...this is day two on ubuntu for me

---

### Post by kidders on 2007-01-01
Hey again,

Switch "NTFS" for "ntfs" (see mount's man page for more info). That should do the trick :-)

---

### Post by b1ackhawk on 2007-01-01
that did it:-D thankyou,

now where do i open the file explorer to view the contents?

---

### Post by taurus on 2007-01-01
I recommend you modify the last line in /etc/fstab to look like this so you, as a regular user, can read from it (as of right now, only root can read from your /media/share)...

```
/dev/hdd1   /media/share   ntfs   nls=utf8,umask=0222   0   0
```

---

