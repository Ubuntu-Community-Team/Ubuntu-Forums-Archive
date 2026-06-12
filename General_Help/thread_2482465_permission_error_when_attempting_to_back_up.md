---
title: "permission error when attempting to back up"
date: 2023-01-01
forum: General Help
---

### Post by jonfisher on 2023-01-01
Permission error when attempting to back up my home folder to my backup HD

And when searching for the file, it just hangs with "searching" indefinitely....

Of course I can skip it, but I would like to address the problem...

See 2 screenshots please & any suggestions please...

---

### Post by Bashing-om on 2023-01-01
jonfisher; Hey

Mount the backup HD in terminal and look at the file system permissions assigned to that target.

[INDENT]all about access rights
[/INDENT]

---

### Post by The Cog on 2023-01-01
The error message says you don't have the right to read the mythtv folder. What is the full path to this folder - is it in your home directory or somewhere else on the directory tree? 
What are the permissions on that directory, and are you the owner?
Posting the output from these two commands will help us understand, but you need to put the correct path to the folder into the commands:
```
ls -ld /mythtv
ls -l /mythtv
```

---

### Post by jonfisher on 2023-01-06
> **The Cog said:**
> The error message says you don't have the right to read the mythtv folder. What is the full path to this folder - is it in your home directory or somewhere else on the directory tree? 
What are the permissions on that directory, and are you the owner?
Posting the output from these two commands will help us understand, but you need to put the correct path to the folder into the commands:
```
ls -ld /mythtv
ls -l /mythtv
```

How would I determine the correct path to the folder?

Yes, I am the owner of everything on this computer....

When I click the icon on the bottom left (to show applications) and type in mythtv to search for it, it never finds anything - just indefintely searches....

What can I type into terminal to find out more about this "mythtv"   ?

---

### Post by jonfisher on 2023-01-06
> **Bashing-om said:**
> jonfisher; Hey

Mount the backup HD in terminal and look at the file system permissions assigned to that target.
[INDENT]all about access rights
[/INDENT]


ok, I can mount the backup hd,
however, I don't know what to type into terminal to do the other things you speak of

help please with what exactly to type into terminal....

---

### Post by Bashing-om on 2023-01-07
jonfisher - Well !
> 
help please with what exactly to type into terminal....


O'Kay - so a hunt'n we will go.
From square one; post back the result of terminal command:
```

sudo fdisk -lu

```
and we see where next we jump to :D
Looking to find - somewhere - that mythical mythtv directory that is - somewhere - in the file system.


[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by jonfisher on 2023-01-08
```

Disk /dev/loop0: 187.9 MiB, 197029888 bytes, 384824 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 3.2 MiB, 3358720 bytes, 6560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 187.9 MiB, 197029888 bytes, 384824 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 146.57 MiB, 153686016 bytes, 300168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 146.95 MiB, 154083328 bytes, 300944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 116.69 MiB, 122359808 bytes, 238984 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 55.61 MiB, 58314752 bytes, 113896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: Samsung SSD 870 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 8FB7D54A-C82B-4B16-96AA-37640511E023

Device       Start        End    Sectors  Size Type
/dev/sda1     2048    1050623    1048576  512M EFI System
/dev/sda2  1050624 1953523711 1952473088  931G Linux filesystem


Disk /dev/sdb: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000NM0033-9ZM
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: D46CF724-B6A7-4363-8BFD-90A0B4D144B8

Device          Start        End    Sectors   Size Type
/dev/sdb1        2048 1937139711 1937137664 923.7G Linux filesystem
/dev/sdb2  1937139712 1953523711   16384000   7.8G Linux swap


Disk /dev/sdc: 14.84 GiB, 15931539456 bytes, 31116288 sectors
Disk model: STORAGE DEVICE  
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     8192 31116287 31108096 14.8G  b W95 FAT32


Disk /dev/loop8: 55.61 MiB, 58310656 bytes, 113888 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 63.23 MiB, 66301952 bytes, 129496 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 63.27 MiB, 66347008 bytes, 129584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 72.86 MiB, 76398592 bytes, 149216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 72.91 MiB, 76451840 bytes, 149320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop13: 55.1 MiB, 57778176 bytes, 112848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop14: 55.03 MiB, 57704448 bytes, 112704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop15: 22.16 MiB, 23232512 bytes, 45376 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop16: 238.43 MiB, 250015744 bytes, 488312 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop17: 238.48 MiB, 250060800 bytes, 488400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop18: 391.27 MiB, 410279936 bytes, 801328 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop19: 521.44 MiB, 546766848 bytes, 1067904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop20: 164.76 MiB, 172761088 bytes, 337424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop21: 346.3 MiB, 363118592 bytes, 709216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop22: 346.33 MiB, 363151360 bytes, 709280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop23: 446.29 MiB, 467963904 bytes, 913992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop24: 140 KiB, 143360 bytes, 280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop25: 81.26 MiB, 85209088 bytes, 166424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop26: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop28: 52.35 MiB, 54894592 bytes, 107216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop29: 37.09 MiB, 38891520 bytes, 75960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop30: 4 MiB, 4190208 bytes, 8184 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop31: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop32: 114.05 MiB, 119586816 bytes, 233568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop33: 157.76 MiB, 165425152 bytes, 323096 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop34: 260.71 MiB, 273375232 bytes, 533936 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop35: 101.47 MiB, 106397696 bytes, 207808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop37: 36.43 MiB, 38195200 bytes, 74600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop38: 45.93 MiB, 48156672 bytes, 94056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop39: 45.93 MiB, 48160768 bytes, 94064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop40: 49.62 MiB, 52031488 bytes, 101624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop41: 304 KiB, 311296 bytes, 608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop42: 304 KiB, 311296 bytes, 608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop43: 295.71 MiB, 310079488 bytes, 605624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop44: 320.44 MiB, 336003072 bytes, 656256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop45: 52.35 MiB, 54894592 bytes, 107216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop46: 36.43 MiB, 38195200 bytes, 74600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdd: 7.8 GiB, 8376025088 bytes, 8179712 sectors
Disk model: Clip Jam        
Units: sectors of 1 * 1024 = 1024 bytes
Sector size (logical/physical): 1024 bytes / 1024 bytes
I/O size (minimum/optimal): 1024 bytes / 1024 bytes
Disklabel type: dos
Disk identifier: 0x500a0dff

Device     Boot      Start        End    Sectors  Size Id Type
/dev/sdd1       1948285285 3650263507 1701978223  1.6T 6e unknown
/dev/sdd2                0          0          0    0B 74 unknown
/dev/sdd4         28049408   28049848        441  441K  0 Empty

Partition table entries are not in disk order.
michael@michael-HP-EliteDesk-800-G1-SFF:~$ 


```

---

### Post by ajgreeny on 2023-01-08
Open a terminal and run command ```
locate mythtv
``` and copy back here the output you get.
Please use Code-Tags when pasting terminal output. See my signature below for a how-to.

We can then look at permissions of all those mythtv directories.
You believe you are the owner of everything on your computer but when using Linux that is never the situation; understanding permissions is essential.

---

