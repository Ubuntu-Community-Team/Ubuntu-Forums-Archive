---
title: "Please Help: Ubuntu constantly switches IDs of my HD partitions"
date: 2007-10-26
forum: General Help
---

### Post by matthias_k on 2007-10-26
Hi,

I have the following problem: Ubuntu treats my hard disks as if they were SCSI devices. From what I understand, this is because in Edgy or Feisty they changed the kernel module that is responsible from handling hard drives, resulting in hard drives now always being /dev/sdX instead of /dev/hdX.

Anyway, the problem is that these device files can **change** after rebooting. This is a showstopper, because I can't mount my root device in /etc/fstab to some fixed device, e.g. /dev/sda, because sometimes /dev/sda is my first HD, sometimes not.

I also can't mount by UUID, because there seems to be a major bug in Gutsy that results in a race condition at boot time when mounting the root device via UUID (I have filed a bug under [https://bugs.launchpad.net/ubuntu/+bug/156597](https://bugs.launchpad.net/ubuntu/+bug/156597)).

Now what do I do?

---

### Post by matthias_k on 2007-10-28
bump

---

### Post by matthias_k on 2007-10-30
bump

---

### Post by matthias_k on 2007-10-31
I can't believe I'm the only one having this problem?!

---

### Post by nowshining on 2007-10-31
hmmm,  what is the contents of ur fstab file on reboots?

example copy and paste a copy of it now here by opening up a terminal and typing sudo gedit /etc/fstab 

and pasting it here, exit and reboot and re-open the terminal and type out the new copy of the fstab file u don't have to re type the sudo /etc/fstab part just hit the up arrow button until u find it and hit enter.

---

### Post by matthias_k on 2007-10-31
What do you mean "on reboots". /etc/fstab does not change unless *I* change it of course.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda1       /home/matthias/backup ext3 defaults 0 0
/dev/sdc1       /home/matthias/storage ext3 defaults 0 0

pluto:/Qmultimedia /home/matthias/media nfs rw,user,noauto 0 0
#//pluto/Qmultimedia /home/matthias/media cifs user,noauto,rw,uid=matthias,credentials=/home/matthias/.smbcreds

That's my fstab. It doesn't work this way though, because my root partition is not always /dev/sdb1. I can't mount it via UUID either, for the reasons I already stated.

---

### Post by nowshining on 2007-10-31
then well I don't know what numbers ur talking about unless it's the ones between the ```
 [ and ] 
``` brackets.

---

### Post by matthias_k on 2007-10-31
> **nowshining said:**
> then well I don't know what numbers ur talking about unless it's the ones between the ```
 [ and ] 
``` brackets.

Errr... numbers? Can you point me to the post where I said someting about numbers? :D Nevermind.

Does someone actually have an answer to my issue? Maybe somone with Linux experience and libata knowledge in particular?

---

### Post by nowshining on 2007-10-31
u said UUIDS change WHERE ARE THEY CHANGING ON U :/ where do U THINK they are changing on u or WHERE do u see em' change?

---

### Post by nowshining on 2007-10-31
n/m u'll have to wait until someone comes here with more knowledge.

---

