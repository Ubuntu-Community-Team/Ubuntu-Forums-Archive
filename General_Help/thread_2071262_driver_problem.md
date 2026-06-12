---
title: "driver problem"
date: 2012-10-15
forum: General Help
---

### Post by ThethundarBird on 2012-10-15
i have AMD Radeon&#8482; HD 6450 Graphics

and it makes problem with me when i download its driver from the suggested ubuntu Aditional driver


does anyone know from where i can get a better driver

---

### Post by NikTh on 2012-10-15
Hi , 
please be more specific about your problem and give some additional info. 

Open a terminal (with Ctrl+Alt+T keys combo) and copy-paste from here to the terminal bellow commands , one at time and press [Enter] key. 

```
cat /etc/lsb-release
uname -r 
sudo fdisk -l
dpkg -l | grep fglrx 
lspci -nnk | grep -iA2 vga
```Post back the results (by copy-paste them from the terminal here) between the brackets [noparse]```
here
```[/noparse].

Also tell us what excactly is the problem ? Video - tearing ? Desktop environment.. Describe your problem.
**Be aware:** The 3rd command will ask for your password. Write it normally and carefully because nothing will show up. Like you don't write.
Thanks

---

### Post by ThethundarBird on 2012-10-15
```
Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0d91aeaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   209717247   104755200    7  HPFS/NTFS/exFAT
/dev/sda3       209717248  1953519615   871901184    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 7933 MB, 7933526016 bytes
255 heads, 63 sectors/track, 964 cylinders, total 15495168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8064    15495167     7743552    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 16.0 GB, 16047407104 bytes
255 heads, 63 sectors/track, 1950 cylinders, total 31342592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x008c767f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048    31336447    15667200    7  HPFS/NTFS/exFAT

Disk /dev/sde: 2055 MB, 2055019008 bytes
64 heads, 62 sectors/track, 1011 cylinders, total 4013709 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          62     4011647     2005793    c  W95 FAT32 (LBA)

Disk /dev/sdf: 250.1 GB, 250059350016 bytes
64 heads, 32 sectors/track, 238475 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *        2048   236331007   118164480   83  Linux
/dev/sdf2       236331008   244146175     3907584   82  Linux swap / Solaris
/dev/sdf3       244148222   488396799   122124289    5  Extended
/dev/sdf5       244148224   488396799   122124288    b  W95 FAT32

Disk /dev/sdg: 506 MB, 506986496 bytes
33 heads, 32 sectors/track, 937 cylinders, total 990208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *          32      990527      495248    6  FAT16

Disk /dev/mapper/cryptswap1: 4001 MB, 4001366016 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7815168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3ce53d4d

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
ahmed@EngAsZ:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
ahmed@EngAsZ:~$ uname -r 
3.2.0-32-generic-pae
ahmed@EngAsZ:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0d91aeaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   209717247   104755200    7  HPFS/NTFS/exFAT
/dev/sda3       209717248  1953519615   871901184    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 7933 MB, 7933526016 bytes
255 heads, 63 sectors/track, 964 cylinders, total 15495168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8064    15495167     7743552    7  HPFS/NTFS/exFAT

Disk /dev/sdd: 16.0 GB, 16047407104 bytes
255 heads, 63 sectors/track, 1950 cylinders, total 31342592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x008c767f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048    31336447    15667200    7  HPFS/NTFS/exFAT

Disk /dev/sde: 2055 MB, 2055019008 bytes
64 heads, 62 sectors/track, 1011 cylinders, total 4013709 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          62     4011647     2005793    c  W95 FAT32 (LBA)

Disk /dev/sdf: 250.1 GB, 250059350016 bytes
64 heads, 32 sectors/track, 238475 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *        2048   236331007   118164480   83  Linux
/dev/sdf2       236331008   244146175     3907584   82  Linux swap / Solaris
/dev/sdf3       244148222   488396799   122124289    5  Extended
/dev/sdf5       244148224   488396799   122124288    b  W95 FAT32

Disk /dev/sdg: 506 MB, 506986496 bytes
33 heads, 32 sectors/track, 937 cylinders, total 990208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *          32      990527      495248    6  FAT16

Disk /dev/mapper/cryptswap1: 4001 MB, 4001366016 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7815168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3ce53d4d

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
ahmed@EngAsZ:~$ dpkg -l | grep fglrx 
ahmed@EngAsZ:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV730XT [Radeon HD 4670] [1002:9490]
	Subsystem: Hightech Information System Ltd. Device [1787:2268]
	Kernel driver in use: radeon
```



the problem is the ubuntu additional driver once i open , suggests me to istall a drive of ati , but when i installed this driver before it made the  screen freeze many times before ,so this time i wont install it again ,but i want a good driver to install it instead

 i mean this 

[[IMG]http://imageshack.us/a/img812/8926/screenshotfrom201210151.png[/IMG]](http://imageshack.us/photo/my-images/812/screenshotfrom201210151.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by NikTh on 2012-10-15
> **ThethundarBird said:**
> ```
Advanced Micro Devices [AMD] nee ATI **RV730XT [Radeon HD 4670]** [1002:9490]
    Subsystem: Hightech Information System Ltd. Device [1787:2268]
    Kernel driver in use: **radeon**
``` 

This graphics card supported by the open source driver (radeon) that already loaded correctly to your system. 

Do you have any specific problem with the graphics ? If not , is not necessarily to install any additional drivers. 

&#913;dditional drivers are not compulsory. You can install them when you have a problem with the open source driver. 

The open source driver (radeon) is developed by Ubuntu developers and is not something general driver (like Windows). Is a specific driver for specific graphic card (yours included). 

The problem you faced is a common problem with Jockey program (responsible to mention to user for additional drivers and install them). 

If you really have a problem with your graphics - Environment , then we can try other ways to install the additional driver (restricted driver).

Thanks

---

