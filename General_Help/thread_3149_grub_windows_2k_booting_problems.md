---
title: "grub windows 2k booting problems"
date: 2004-11-03
forum: General Help
---

### Post by Moobert on 2004-11-03
Hey,

i'm having problems setting up my grub config file to allow me to load windows from a 2nd harddrive.

so far i have:

title Windows
root	(hd0,1)
map	(hd0) (hd1)
map	(hd1) (hd0)
makeactive
chainloader +1

however this just gives error and wont boot.
i've tried different varations of the above with no luck, i have i feeling that the problems are down to a strange harddrive setup. which is:

primary master ide : linux
primary slave ide : cdrom
secondary master ide : windows 2000
secondary slave ide : cdrom

and the config i have tried before is infact maybe  trying to boot from the primary slave ide.

I'm wondering what i need to add to the above config to boot the windows dive in the secondary master ide ? Also what the numbers after  "root	(hd0,1)" each mean. ?

theres my df for extra info

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1              9614116   2637368   6488376  29% /
tmpfs                   128468         0    128468   0% /dev/shm
/dev/hda6            105274496  46008028  53918836  47% /home
/dev/hdc1             80016224  51307584  28708640  65% /mnt/hdc1

(hdc1 is my windows drive)

Thanks

Peter

---

### Post by ulrich on 2004-11-03
hi,
the numbers afterr root are (drive,partition)
your setup is almost finished but there are some things to know:

the 'map' command fools the order of the hdds, but grub isnt 'fooled' by this.
so 'root' and in the case of using windows 'rootnoverify' must be the hd win actually lives on. 
and grub counts the partitions starting at 0 not 1. 1 is the second partition on the drive, 0 the first.

also check that /boot/grub/device.map is correct (if it doesnt exist, create it)
should be in your case
```

(hd0)   /dev/hda
(hd1)   /dev/hdc

```

your menu.lst should then look like
```

title           Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader     +1
makeactive

```

---

### Post by Moobert on 2004-11-04
Thanks, that works fine now.

---

