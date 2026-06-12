---
title: "after changing dvd-r hardware permissions are denied"
date: 2008-04-10
forum: General Help
---

### Post by jeffspen on 2008-04-10
hi

i recently replaced one IDE DVD-R device with another similar one (due to dropping the old one!) and now i am unable to mount either blanks or written CDs or DVDs.
In the user groups the "CD-ROM" drive is owner unknown and set to read only.

i have tried various things i've found on this forum but to no avail.

if it helps I can provide this:

```
*-cdrom
                description: SCSI CD-ROM
                product: IDE H16X
                vendor: DVDRW
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: B02V
                capabilities: removable audio
                configuration: ansiversion=5 status=ready
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom

```

I tried manually mounting an audio CD:

```
jeff@jeff-desktop:~$ sudo mount /dev/cdrom
[sudo] password for jeff:
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

jeff@jeff-desktop:~$ dmesg | tail
[18171.884255] end_request: I/O error, dev sr0, sector 804008
[18171.885151] end_request: I/O error, dev sr0, sector 803784
[18171.886050] end_request: I/O error, dev sr0, sector 805024
[18171.886944] end_request: I/O error, dev sr0, sector 804000
[18171.887840] end_request: I/O error, dev sr0, sector 803776
[18171.888733] end_request: I/O error, dev sr0, sector 1248
[18171.889626] end_request: I/O error, dev sr0, sector 1024
[18171.889707] UDF-fs: No partition found (1)
[18171.946196] end_request: I/O error, dev sr0, sector 64
[18171.946286] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
jeff@jeff-desktop:~$ 

```

My /etc/fstab file looks like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2ac5894d-4b17-442d-b9a4-7e8d94de82a2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0cdc879d-4598-4766-a330-1229754ed242 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

and then there is this:

```

jeff@jeff-desktop:~$ ls -l /media
total 8
lrwxrwxrwx 1 root root    6 2008-01-23 23:48 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-01-23 23:48 cdrom0
lrwxrwxrwx 1 root root    7 2008-01-23 23:48 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2008-01-23 23:48 floppy0
jeff@jeff-desktop:~$ 

```

Has anyone got any ideas? I can't read audio CDs, DVDs, burn anything...!

Thanks in advance

---

### Post by Het Irv on 2008-04-10
Just out of curiosity, are your jumper settings correct on the back of the drive?  I don't know if it would even show up in Ubuntu if they were not, but I know that is a mistake I make every time I add a drive to my computer.

---

### Post by jeffspen on 2008-04-10
hey thanks for the reply.
i don't know yet. i'm currently burning a DVDrom in K3b! Apparently this programme uses the root user privilege ? So probably they are ok. Will take it apart when the burn is finished...
What I really want to do of course is to use general nautilus and gnome CD/DVD stuff like serpentine and the wonderfully simple sound juicer

---

### Post by Het Irv on 2008-04-10
If you are burning to a disk using the drive in question then your jumper settings are correct.  ls -l /media looks the same as mine, but I am not that good at reading fstab yet.  I don't have any ideas.

EDIT: wouldn't the mount point be /media/cdrom.  All those errors look like it couldn't find a partition (which it wouldn't on a cd).

---

### Post by jeffspen on 2008-04-10
thanks for that. i didn't really want to start pulling things out of my box!

When i finished burning the disk it showed up on my desktop as normal. so i went for another burn (a copy of the system backup from your really handy quickstart :) ) using the nautilus burner and the new blank dvd appeared on the desktop but the burner only wanted to create an image - there was no option too select my drive.

hmmmm

any ideas??

---

