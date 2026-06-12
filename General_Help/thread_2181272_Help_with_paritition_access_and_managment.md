---
title: "Help with paritition access and managment"
date: 2013-10-17
forum: General Help
---

### Post by marcosilvaesteves on 2013-10-17
Hello!

For the first time, I've created an extended partition.

My idea was create a smaller paritition and then a paritition to be accessed from windows and from linux as backup.

However, I'm not able to write to it. When I try to write any file, gives an error that I cannot write to the partition.

This is my current partition scheme
[ATTACH=CONFIG]247006[/ATTACH]

I figured that I need to format the unllocated one to swap. If I format to swap, it will be automatcly used?

---

### Post by ibjsb4 on 2013-10-17
As far as I know (I do not run windows), windows cannot read or write to ext4.

---

### Post by marcosilvaesteves on 2013-10-17
> **ibjsb4 said:**
> As far as I know (I do not run windows), windows cannot read or write to ext4.

I Intend to use linux reader.
It is an effective program!

---

### Post by marcosilvaesteves on 2013-10-17
I've been searching.
I've change the partition sizes, and I've tried to changed the partition permissions.
I cannot write to the backup partition on linux.
I'm not sure if linux is using the swap.
I think my swap parition is always chaning the UUID.

This is the output of my blkid
```
/dev/sda1: SEC_TYPE="msdos" LABEL="DELLUTILITY" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: LABEL="Recovery" UUID="CC70378A703779F2" TYPE="ntfs" 
/dev/sda3: UUID="647A12867A125560" TYPE="ntfs" 
/dev/sda6: UUID="76faaaa5-ea05-480d-b551-1f501f3c129d" TYPE="ext4" 
/dev/sda7: UUID="128db7f8-5831-4a4b-9b2a-ba0b2241edb6" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="57a73dc0-7c56-4f46-9978-830031bf07c1" TYPE="swap"
```

I edited the fstab to this version

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=128db7f8-5831-4a4b-9b2a-ba0b2241edb6 /               ext4    errors=remount-ro 0       1

# /media/backup was on /dev/sda6 during installation
UUID=76faaaa5-ea05-480d-b551-1f501f3c129d /media/backup    ext4    defaults    02
# swap was on /dev/sda5 during installation
UUID=f0335109-89c1-45b0-b560-f14aa9f9b49e none            swap    sw              0       0
#/dev/mapper/cryptswap1 none swap sw 0 0


```

Output of swaps:
```
cat /proc/swaps 
Filename                Type        Size    Used    Priori
```

```
sudo swapon --all --verbose
swapon: cannot find the device for UUID=f0335109-89c1-45b0-b560-f14aa9f9b49e
```

---

