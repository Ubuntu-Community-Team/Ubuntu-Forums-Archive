---
title: "fsck problem"
date: 2007-12-12
forum: General Help
---

### Post by rabid9797 on 2007-12-12
im having a problem upon boot-up of gutsy...

i get this error about half-way through start up, and it asks me to use the matinence shell to fix it, but i can exit and continue start up fine from there. its just annoying really.

the error:

```

Log of fsck -C -R -A -a 
Wed Dec 12 20:33:13 2007

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=0c11bc28-b00b-47c6-8dae-f14fbf63825a'

fsck died with exit status 8

Wed Dec 12 20:33:13 2007
----------------

```

i checked fstab and had a different UUID at first(i just wiped windows), so i changed sda3 to the correct UUID, but i keep getting the same error at startup anyways...

```

 cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8749381c-d223-4ccc-a3ec-ba41ac0a38d1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=0c11bc28-b00b-47c6-8dae-f14fbf63825a /media/sda3     ext3    defaults        0       2
# /dev/sda5
UUID=91cecbd2-67ce-4884-952d-751abd5957fc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

so what could be my problem?

---

### Post by rabid9797 on 2007-12-12
hahaha, sorry guys, my bad.

it doesn't check correctly *becuase it doesn't exist*. 

im stupid. once i wiped windows, the partition didn't exist. its just unallocated space. ](*,)

problem solved.

---

