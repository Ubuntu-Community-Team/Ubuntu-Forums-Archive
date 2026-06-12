---
title: "Wubi 7.04 and RAID0"
date: 2007-06-13
forum: General Help
---

### Post by brian_rbk on 2007-06-13
Just installed wubi and tried to boot up ubuntu but it wont work. When i select Ubuntu at the startup its starts to load then says ...


"[	10.178482] Buffer I/O error on device sda2, logical block 615112576 "

this is repeated several times with different values.

I assume this is because im using raid0. Is there anything else i can do to get ubuntu installed?

Brian

---

### Post by ago on 2007-06-13
I'll have a look, it would help if you could find what device is normally used when you mount the raided partition. You can use a live CD, mount the partition and then look in "mount" to find out the device.

---

### Post by brian_rbk on 2007-06-13
I have the live cd running... how do i mount the partition ?

---

### Post by brian_rbk on 2007-06-13
dont know if this would be anyhelp but when i enter sudo fdisk -l into the terminal i get ...

Disk /dev/sda: 160.gb 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders  of 16065 * 512 = 8225280 bytes

Device           boot       Start         End        Blocks         Id  System
/dev/sda1                         1             7          56196       de  Dell Utility
/dev/sda2        *               8     38296  307556392+     7   HPFS/NTFS
/dev/sda3                    38298  38903     4867695        db  CP/M / CTOS/ ...

Disk /dev/sdb: 160gb 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders  of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a vaild partition table



Thanks,
brian

---

### Post by ago on 2007-06-13
What is your raid setup?

---

### Post by brian_rbk on 2007-06-13
the startup screen says RAID0

---

### Post by ago on 2007-06-13
That's testing for raid0, does not necessarily mean that you use raid0

---

### Post by brian_rbk on 2007-06-13
ok, any idea how id find out ? bios setup menu maybe?

there is definitely 2 hard drives 160gb each... and in windows it only shows up as the one .. c:\ with approx 290gb


brian

---

### Post by ago on 2007-06-13
It might be a raid0, but how does it work? is that a using windows software raid or a raid card?

---

### Post by brian_rbk on 2007-06-13
Device manager lists under SCSI and RAID controllers ..

  - Intel(R) 82801GR/GH SATA RAID controller

---

### Post by CrazyGuy123 on 2007-06-14
I think thats the same as my RAID I was testing.  I believe the RAID is a bit of a mix between software and hardware.  It's basicly software RAID, but the BIOS has an extension with the RAID software in to make the RAID array bootable (ie. the RAID array works in MS-DOS because the BIOS deals with the RAID).  As soon as any protected mode OS runs, it requires software of some kind to continue using the RAID, otherwise it reverts back to appearing as two hard disks, both of which have no mountable filesystems on.

---

### Post by ago on 2007-06-14
What happens when you boot from the Ubuntu LiveISO? How are your disks "visible" to the system? If with Ubuntu LiveCD you cannot see the raid properly it is highly unlikely for us to provide support for it within wubi.

---

### Post by CrazyGuy123 on 2007-06-14
I don't know exactly how it's best to collect the most useful information, however here is some stuff (attached) that looks useful (as screenshots I'm afraid as I couldn't find any equivilant info on the command line).

Thats with the RAID not mounted, and not working, and it's running wubi from the first disk listed, which works great.  The other two are in a RAID0 array, and don't work.  

I believe I assigned the name "Volume" to the array when setting it up, so it appears ubuntu has picked that up somehow.

---

### Post by ago on 2007-06-14
What I need is for you to run a Live CD (Ubuntu or Knoppix) and then tell me how the Raid0 is represented. Does it appear as a single partition? Or do you still see 2 separate drives? What do you see under /dev/mapper? Do you have any relevant entry under /sys/block? If you want to mount the partitions within the raid what command does work (if any)? It should be something like: "mount /dev/XXX /mnt"

---

