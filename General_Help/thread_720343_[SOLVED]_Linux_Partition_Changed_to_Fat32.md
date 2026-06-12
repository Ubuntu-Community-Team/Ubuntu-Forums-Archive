---
title: "[SOLVED] Linux Partition Changed to Fat32"
date: 2008-03-10
forum: General Help
---

### Post by Dithers on 2008-03-10
This is the second time this has happened to this laptop "dell inspiron 6400" works great for a week or two  and one morning you turn it on to be greeted by a grub error 17 "Linux partition not found"
after running sudo fdisk from boot cd I realized my sda1 LINUX partition is listed as FAT32
I do NOT have windows on this computer it has one HD Linux only NO dual boot. last time I thought it was because of the recovery partition left on the drive when I got it but when I reinstalled I made sure it was gone and linux was sda1.

I am pretty sure I can change the partition type back with fdisk but have no idea how and do not want to mess it up.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   222516378   226709279     2096451    c  W95 FAT32 (LBA)
/dev/sda2       228380040   234436544     3028252+   5  Extended
/dev/sda5       228380103   234436544     3028221   82  Linux swap / Solaris

---

### Post by phrawzty on 2008-03-10
> **Dithers said:**
> I am pretty sure I can change the partition type back with fdisk but have no idea how and do not want to mess it up.

While i don't know what the cause of your (strange) problem is, changing a partition type with fdisk is quite easy :

```
$ sudo fdisk /dev/sda

Command (m for help): m
   ...
   t   change a partition's system id
   ...

Command (m for help): t
Partition number (1-4): <partition>
Hex code (type L to list codes): L
   ...
83  Linux
   ...

Hex code (type L to list codes): 83
Command (m for help): w
```

---

### Post by Dithers on 2008-03-10
Thankyou so much 
your instructions were perfect but it didn't take

here is my fdisk verify if that helps

Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(68, 13, 10) logical=(116387, 225, 36)
Partition 1 has different physical/logical endings:
     phys=(288, 115, 43) logical=(126888, 82, 1)
Partition 1 does not end on cylinder boundary.
Partitions 1: cylinder 289 greater than maximum 260
Partition 1: previous sectors 2038460886 disagrees with total 4637545
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(105914, 175, 47)
Partition 2 has different physical/logical endings:
     phys=(366, 32, 33) logical=(222309, 108, 57)
Partition 2 does not end on cylinder boundary.
Partitions 2: cylinder 367 greater than maximum 260
Partition 2: previous sectors -723566351 disagrees with total 5887982
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(0, 40, 54)
Partition 3 has different physical/logical endings:
     phys=(372, 97, 50) logical=(0, 40, 53)
Partition 3 does not end on cylinder boundary.
Partitions 3: cylinder 373 greater than maximum 260
Partition 3: previous sectors 2572 disagrees with total 5988772
Total allocated sectors 2038570988 greater than the maximum 4192902

---

### Post by Dithers on 2008-03-10
do I have to mount the drive for fdisk to work? " because it wont mount
is there another way to change the partition type like with super grub disk or something?

---

### Post by phrawzty on 2008-03-10
> **Dithers said:**
> do I have to mount the drive for fdisk to work? " because it wont mount
is there another way to change the partition type like with super grub disk or something?

Drives don't get mounted - partitions on drives get mounted.  You can fdisk a drive which has mounted partitions, but of course, it is often safer to perform fdisk functions on a drive which is not active.

The output you provided above is.. well, it's odd.  If you could post every command you typed in order to get that output, it might help to further interpret it - the context is relevant.

---

### Post by dgray_from_dc on 2008-03-10
That is weird!

I agree with phrawzty as far as how to change it.  That should have worked.

The only reason I can think of that it didn't work is that it **IS** a FAT32 volume somehow.

Have you tried looking at it as a FAT32 partition just to see what is there?

If it is in fact a FAT32 volume, looking at what that volume contains may help you figure out where it came from.

---

### Post by drsaamah on 2008-03-10
I'm not as terminal knowledgable as these guys so hopefully they get your problem fixed.  As for the cause of the problem though... did your computer come that "media direct" crap?  Because I've heard problems along these lines being caused by media direct trying to mess around with other partitions.

---

### Post by justleen on 2008-03-10
yea wel.. err...

i know how to change it, but thats destructive (!!!)
```

$ mkfs.ext3 /dev/sda1

```

that will reformat the partition using ext3 filesystem.. again, this is destructive, all data will be lost!

---

### Post by Dithers on 2008-03-10
to get the output I posted I did

$ sudo fdisk /dev/sda1

Command (m for help): m
   ...
abd chose verify

I do have that "Media Direct Crap"

it mounts as a partition with the live cd but I have no idea where it lives or how to kill it. I thought it was on the recovery partition that I deleted last time I guess I was wrong

I think were making progress

---

### Post by justleen on 2008-03-10
you can install gparted to get a GUIfication of you partition.. it sometimes helps to see the partitions in a GUI, rather then fdisk's txt output

---

### Post by phrawzty on 2008-03-10
> **Dithers said:**
> to get the output I posted I did

$ sudo fdisk /dev/sda1

Ack - no, stop!  As i mentioned previously, you **do not fdisk a partition** - that is not how to use fdisk.

This is **wrong** :
```
$ sudo fdisk /dev/sda**1**
```

This is correct :
```
$ sudo fdisk /dev/sda
```

That explains why your output was so strange - fdisk was attempting to read partition data from a single partition, which is not possible under normal usage.

Please run fdisk again properly, and you should be able to change the partition type as indicated in the instructions above.

---

### Post by Dithers on 2008-03-10
> **phrawzty said:**
> While i don't know what the cause of your (strange) problem is, changing a partition type with fdisk is quite easy :

```
$ sudo fdisk /dev/sda

Command (m for help): m
   ...
   t   change a partition's system id
   ...

Command (m for help): t
Partition number (1-4): <partition>
Hex code (type L to list codes): L
   ...
83  Linux
   ...

Hex code (type L to list codes): 83
Command (m for help): w
```


This worked But with knoppix STD 0.16 cd I had 

Knoppix called the disk hda instead of sda but everything else was the same. and it was definetly caused by media direct that I will figure out how to get rid of latter

thanks to All especially phrawzty

---

