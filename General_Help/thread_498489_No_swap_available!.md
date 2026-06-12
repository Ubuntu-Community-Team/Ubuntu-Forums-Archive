---
title: "No swap available!"
date: 2007-07-11
forum: General Help
---

### Post by mogie on 2007-07-11
hi folks!

I've got a problem with my server where there are no swap available. It says so in command "top" and other outputs i get in phpsysinfo I've installed. look for youself if it is to any help :)

[http://teamgule.net/phpsysinfo/index.php]("http://teamgule.net/phpsysinfo/index.php")

There are a swap partition at the sda device. Here are the output from my /etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=4aca87ce-67a3-4ebd-a4ce-0c6eb3b62131 /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
# /dev/hda3
UUID=a93fe079-2f04-4a57-ada2-dc5cd48af386 /boot           ext3    defaults        0       2
# /dev/hda4
UUID=29091b3b-9923-4772-8615-919aa4d8b12c /home           ext3    defaults,usrquota,grpquota        0       2
# /dev/hda2
UUID=2436fe6c-ecc4-42d6-b21d-349ddc1eaf8b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


```

Any advice on how to fix this quick n easy? :) I'm still a noob at most to Linux, though I managed to set up a pretty multitasked server..

*I've been ghost-cp a IDE-HD to a SATA-HD. Therefore you may see hda instead of sda some places in fstab. I had to set the grub-boot to sda instead of hda ofcourse to get the server to boot.. I've done no more changes to the "sda/hda" problem after this.

Thanks for all help!

---

### Post by louieb on 2007-07-11
Are you using Feisty? One of the updates messed up the uuid of my swap partition.  use  ```
ls -l /dev/disk/by-uuid/
```and compare your swap partitions uuid. If it can't find your swap it can't mount it. You just need to edit /etc/fstab  then   run the **swapon** command   or you can use **mount -a**.

---

### Post by mogie on 2007-07-12
No. I'm using Edgy...stupidly enough.. 

The cause of this may have to be the disk clone from the other disk, as I've mentioned... maybe..

I cannot find the swap UUID with "ls -l /dev/disk/by-uuid/",
and "swapon -a" gives me the error:

swapon: cannot stat /dev/disk/by-uuid/2436fe6c-ecc4-42d6-b21d-349ddc1eaf8b: No such file or directory

..so Im not sure what or where to edit in my /etc/fstab.. 

btw - I do find the swap partition using Partition Magic 8.0, so the UUID has to be wrong? I've no clue on how the UUID should look though..

---

### Post by mogie on 2007-07-12
Weeho! Got it working. Dont have time to explain it all but here is all the cmds I used, and this Norwegian forum thread telling me:

[http://linux1.no/node/2496](http://linux1.no/node/2496)

sudo fdisk -l

I then for instance get out:

/dev/sda1 * 1 2550 20482843+ 83 Linux
/dev/sda2 2551 5100 20482875 83 Linux
/dev/sda3 5101 5355 2048287+ 82 Linux swap / Solaris 

..where my swap partition is sda3

then:
vol_id /dev/sda3

ID_FS_USAGE=other
ID_FS_TYPE=swap
ID_FS_VERSION=2
ID_FS_UUID=
ID_FS_LABEL=
ID_FS_LABEL_SAFE=


but I then see there's no UUID to the disk. But there is an alternative solution to mount the swap:

I could use one of the following, it Will all do the same in /etc/fstab ;)

/dev/sda3 none swap sw 0 0
UUID=eed99fb6-c17c-420c-a834-6798f96ffbfd none swap sw 0 0
LABEL=olavs_disk none swap sw 0 0

---

### Post by ringmaster on 2007-07-14
Thank you!
Changing the uuid in the fstab solved my missing swap!!

This is the power of the community.

Ringmaster

---

