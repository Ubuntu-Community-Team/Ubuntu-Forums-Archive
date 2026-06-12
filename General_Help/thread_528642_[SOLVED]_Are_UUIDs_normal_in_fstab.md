---
title: "[SOLVED] Are UUIDs normal in fstab?"
date: 2007-08-18
forum: General Help
---

### Post by nvteighen on 2007-08-18
This is my /etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=a0487629-795d-4589-a72c-cee252e82132 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/sda1
#UUID=2A90699A90696CEF /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=4
6 0       1
# /dev/sda5
UUID=cd958dd4-dec7-457b-9697-cb6702739484 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

(/dev/sda1 is commented out in purpose)

My question are:
1. Are UUIDs needed?
2. How do I know how much spaces should there be between columns?

I have no issue with fstab, actually iI ask this just for curiosity... and to learn more.

Thanks!

---

### Post by Gary.M on 2007-08-18
One space between sections is enough, and the options section is run together with commas between, but no spaces.

---

### Post by nvteighen on 2007-08-18
> **Gary.M said:**
> One space between sections is enough, and the options section is run together with commas between, but no spaces.

I see. A space means a new argument/option, like in bash commands.

What I still don't figure out what UUIDs are doing there. Shouldn't there be just "/dev/sda#"?

---

### Post by Backharlow on 2007-08-18
Kind of a beginner question here, but, I'd kind of like to put more UUID's in my fstab but i'm not sure how to find the UUID of a disk. I've been just putting the /dev/location-of-disk into my fstab until now.:confused:

---

### Post by PilotJLR on 2007-08-18
Device names, like /dev/sda, are fine. You can also use labels or UUID's.

To find the UUID of an ext2/3 filesystem, do
```

sudo dumpe2fs /dev/<device name and partition>

```

Might want to direct that output to a file for large partitions... UUID is 3rd line from the top.

---

### Post by Thingymebob on 2007-08-18
UUID stands for Universally Unique Identifier and is a mechanism to give each filesystem a unique identifier. It is designed so that collisions are unlikely. All Linux filesystems (including swap) support UUID. FAT and NTFS filesystems don't support UUID, but are still listed in by-uuid with a unique identifier:

```
$ ls -lF /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 Oct 16 10:27 2d781b26-0285-421a-b9d0-d4a0d3b55680 -> ../../sda1
lrwxrwxrwx 1 root root 10 Oct 16 10:27 31f8eb0d-612b-4805-835e-0e6d8b8c5591 -> ../../sda7
lrwxrwxrwx 1 root root 10 Oct 16 10:27 3FC2-3DDB -> ../../sda6
lrwxrwxrwx 1 root root 10 Oct 16 10:27 5090093f-e023-4a93-b2b6-8a9568dd23dc -> ../../sda2
lrwxrwxrwx 1 root root 10 Oct 16 10:27 912c7844-5430-4eea-b55c-e23f8959a8ee -> ../../sda5
lrwxrwxrwx 1 root root 10 Oct 16 10:27 B0DC1977DC193954 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Oct 16 10:27 bae98338-ec29-4beb-aacf-107e44599b2e -> ../../sdb2
```

As you can see, the fat and ntfs partitions (fat and windows labels above) have shorter names, but are still listed. The advantage about using the uuid method is that it is less likely that you have name collisions than with labels; the disadvantage is that they are more difficult to memorise.

---

### Post by ruibernardo on 2007-08-18
Another command to see UUID 

```
blkid
```

Type it to see the UUID of mounted devices or mount any new device and type it to see its UUID.

---

### Post by nvteighen on 2007-08-18
Thank you. I'm going to replace UUIDs by device names.

---

### Post by ruibernardo on 2007-08-18
I woudn't do that. Probably you will break avahi and the auto mount system.

---

### Post by nvteighen on 2007-08-18
Oh, thanks for the warning. I won't do it, then... But I plan to format my Windows partition to be my /home and I understand UUIDs are reset when formatting, I suppose then I'll have to use the device filename or get the new UUID with the commands you wrote above, isn't it?

---

### Post by ruibernardo on 2007-08-18
Yes. Just mount it and run "blkid". Then edit /etc/fstab to use the new UUID.

---

### Post by nvteighen on 2007-08-19
Thank you very much!

---

### Post by cody50 on 2007-08-19
does anyone know can you use a UUID with the umount command? with mount and the -U option it works fine but if i try using a UUID with umount it says it is not mounted according to the mtab (this is because in the mtab it is listed by device.

---

### Post by az on 2007-08-19
> **cody50 said:**
> does anyone know can you use a UUID with the umount command? with mount and the -U option it works fine but if i try using a UUID with umount it says it is not mounted according to the mtab (this is because in the mtab it is listed by device.

You should be able to unmount it by specifying the mount point.

Ex:

sudo umount /mnt

---

### Post by cody50 on 2007-08-19
I tried that and I got 


```
cody@dellbuntu:~$ umount /media/externalHD 
umount: /media/externalHD mount disagrees with the fstab

```

i think that might be because it thinks its unmounting with /dev/sdb1 instead of the uuid in the fstab? that might be the disagreement.

---

