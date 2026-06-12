---
title: "Can't mount my SWAP partition"
date: 2014-06-14
forum: General Help
---

### Post by frogwarrior on 2014-06-14
A program I ran messed parts of my system, so I need to fix it. My system is running really slowly, so I ran htop and see this: [IMG]http://i.gyazo.com/52d274be1fac5381254c832781f29467.png[/IMG] 
no SWAP partition. I have a 6Gb SWAP partition, heres the output of fdisk -l:
 ```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   202125311   101061632   83  Linux
/dev/sda2   *   202125312   202330111      102400    7  HPFS/NTFS/exFAT
/dev/sda3       202330112   295661567    46665728    7  HPFS/NTFS/exFAT
/dev/sda4       300783614   312580095     5898241    5  Extended
/dev/sda5       300783616   312580095     5898240   82  Linux swap / Solaris
``` 

I'm dual booting Windows 7, so sda2 and sda3 (why are there two of them) are Windows partitions. I don't know what sda4 is, but I see it occupies the same space as the SWAP partition. I checked /etc/fstab and there was no entry for the swap partition, so I added one. My home directory is encrypted, that means I need to add an extra cryptswap1 line or something doesn't it? Heres my fstab file now: 

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=98a784e7-79f0-4756-a94a-96cf3de2340a /               ext4    errors=remount-ro 0       1
/dev/sda5           none                   swap         sw                0                0
/dev/mapper/cryptswap1 none swap sw 0 0
``` 

I ran sudo mountall -v, heres the output (the important part): 
```
All filesystems mounted local 4/4 remote 0/0 virtual 16/16 swap 0/2 
```  
so its not mounting. I ran sudo parted -l, heres the output: 

```
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  103GB  103GB   primary   ext4
 2      103GB   104GB  105MB   primary   ntfs         boot
 3      104GB   151GB  47.8GB  primary   ntfs
 4      154GB   160GB  6040MB  extended
 5      154GB   160GB  6040MB  logical

 
```


  Heres what gparted says about it: 



[IMG]http://i.gyazo.com/fc101560f628b8e4fd4ac813748cfe82.png[/IMG]  [IMG]http://i.gyazo.com/07a440641f8411fdb8037eccb4263f2a.png[/IMG]  



2.4Gb of unallocated space, I should really turn that into SWAP. The only thing in /dev/mapper is a yellow "directory" which is not a directory when I try to enter it, its called control. This program (bleachbit) seems to have wiped out the whole SWAP partition. Theres no cryptswap1 in there. I don't know what cryptswap is to be honest so I'm completely stuck here. I think I need to reformat the swap drive, but the encrypted part is what has me confused.

---

### Post by frogwarrior on 2014-06-14
SOLVED: I formatted it with GParted to linux-swap, and it worked, it gave me a new UUID so I put that into /etc/fstab and ran mountall, and it mounted it, so the SWAP space is up and running. Its not encrypted, but I don't care about that, I just need the RAM.

---

