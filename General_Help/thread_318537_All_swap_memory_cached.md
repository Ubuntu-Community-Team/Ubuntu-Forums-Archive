---
title: "All swap memory cached"
date: 2006-12-14
forum: General Help
---

### Post by lordroger on 2006-12-14
Hello,

I run $top and I get this:


Mem:   1034928k total,   707700k used,   327228k free,    16080k buffers
Swap:        0k total,        0k used,        0k free,   457812k cached


I don't really know why there are 0k of total swap, because I've got a 2GB partition for swap purposes that used to work. And then, the cached swap memory constantly changes, although I don't know exactly why.

In /etc/fstab I've got:

/dev/sda6 none            swap    sw              0       0

Where /dev/sda6 is a swap type partition.


What can I do to re-enable swap space? Or, what's wrong with it?


Thank you very much,

Roger

---

### Post by taurus on 2006-12-14
What's the output of this command from a terminal?

```
free
```

---

### Post by lordroger on 2006-12-14
total       used       free     shared    buffers     cached
Mem:       1034928     751236     283692          0      21672     492136
-/+ buffers/cache:     237428     797500
Swap:            0          0          0

> **taurus said:**
> What's the output of this command from a terminal?

```
free
```

---

### Post by taurus on 2006-12-14
You don't have swap partition enable!!!  Are you sure it's /dev/sda6 not /dev/sda5???

What's the output of this command?

```
sudo fdisk -l
```

---

### Post by lordroger on 2006-12-14
Disc /dev/sda: 160.0 GiB, 160041885696 octets
255 capçals, 63 sectors/pista, 19457 cilindres
Unitats = cilindres de 16065 * 512 = 8225280 octets

Dispositiu Arrenc.   Comença       Acaba    Blocs    Id  Sistema
/dev/sda1               1        1279    10273536   83  Linux
/dev/sda2   *        1280        3829    20482875    7  HPFS/NTFS
/dev/sda3            3830        6379    20482875   83  Linux
/dev/sda4            6380       19457   105049035    5  Estesa
/dev/sda5            6380        8929    20482843+   7  HPFS/NTFS
/dev/sda6            8930        9178     2000061   82  Linux swap / Solaris
/dev/sda7            9179       19457    82566036    7  HPFS/NTFS

Disc /dev/sdb: 320.0 GiB, 320072933376 octets
255 capçals, 63 sectors/pista, 38913 cilindres
Unitats = cilindres de 16065 * 512 = 8225280 octets

Dispositiu Arrenc.   Comença       Acaba    Blocs    Id  Sistema
/dev/sdb1               1       38913   312568641   83  Linux

---

### Post by taurus on 2006-12-14
What happens if you run this command from a terminal?

```
sudo swapon /dev/sda6
free
```

---

### Post by lordroger on 2006-12-15
$swapon /dev/sda6

swapon: /dev/sda6: Invalid argument



$free

             total       used       free     shared    buffers     cached
Mem:       1034928    1015804      19124          0       9640     671176
-/+ buffers/cache:     334988     699940
Swap:            0          0          0



I don't know if it may help, but I'm having the same problem on a Debian Linux 2.4.25-grsec.3 #1 mie sep 13 01:27:15 CEST 2006 i686

---

### Post by mcduck on 2006-12-15
swapon doesn't take device names as arguments.

try 'sudo swapon -a'

or if that doesn't work 'sudo mkswap /dev/sda6' and then again 'sudo swapon -a'

---

### Post by lordroger on 2006-12-15
Ultra-cool!

I had already tried "#swapon -a" with same results as before.

"#mkswap /dev/sda6" and then "swapon -a" worked, now I have:

"$free":

             total       used       free     shared    buffers     cached
Mem:       1034928    1013052      21876          0      29256     624632
-/+ buffers/cache:     359164     675764
Swap:      2000052          0    20000


"$top":
Mem:   1034928k total,  1017568k used,    17360k free,    29492k buffers
Swap:  2000052k total,        0k used,  2000052k free,   628612k cached


Thus it is solved now. Thank you very much taurus, McDuck. :)

But... why did it happened? I don't remember having changed anything related to memory, partitions, etc.

---

### Post by mcduck on 2006-12-15
> **lordroger said:**
> Ultra-cool!

I had already tried "#swapon -a" with same results as before.

"#mkswap /dev/sda6" and then "swapon -a" worked, now I have:

"$free":

             total       used       free     shared    buffers     cached
Mem:       1034928    1013052      21876          0      29256     624632
-/+ buffers/cache:     359164     675764
Swap:      2000052          0    20000


"$top":
Mem:   1034928k total,  1017568k used,    17360k free,    29492k buffers
Swap:  2000052k total,        0k used,  2000052k free,   628612k cached


Thus it is solved now. Thank you very much taurus, McDuck. :)

But... why did it happened? I don't remember having changed anything related to memory, partitions, etc.
Great that it's working now. I have no idea why I didn't work before.

By the way, you can use 'free -m' to get free output that is easier to read (megabytes instead of bytes)

---

### Post by taurus on 2006-12-15
Try to reboot to see if your swap partition is mounted automatically!!!

---

