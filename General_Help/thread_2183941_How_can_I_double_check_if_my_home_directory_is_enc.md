---
title: "How can I double check if my /home directory is encrypted?"
date: 2013-10-27
forum: General Help
---

### Post by Psil0cybin on 2013-10-27
Hey guys to start off, I have two laptops that I want to double check that I encrypted the home directory properly in both of them.
first laptop was encrypted using the standard ubuntu install option (during install/creation of Ubuntu partition).
the second laptop was encrypted after install via this method ([http://www.howtogeek.com/116032/](http://www.howtogeek.com/116032/)) 

Now I want to run this by you guys, to check that both home folders are encrypted properly.

I ran this command on the first laptop.
```
sudo fdisk -l
```

the result yielded (keep in mind I have a winblows 7 install as well, hence a lot of partitions-ubuntu installed second-windows7 came with the laptop) 
 
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   497674651   248733902    7  HPFS/NTFS/exFAT
/dev/sda3       497676286   625141759    63732737    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       497676288   623069183    62696448   83  Linux
/dev/sda6       623071232   625141759     1035264   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 1060 MB, 1060110336 bytes
255 heads, 63 sectors/track, 128 cylinders, total 2070528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 


Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```

Now what I am pretty much asking at this step is the fact that I can see that it says cryptswap1 is encrypted, but the fact that nothing else is shown makes me wonder if the home directory is infact encrypted.

So I decided to go a step further, I popped in my Xubuntu live CD
and tried to access the /home/username

it said access denied knowing that default permissions could cause an access denied, I attempted to access the folder using root
using the following command;

```
[COLOR=#000000][FONT=Consolas]sudo ls -l /media/fdf81723-08d4-4be4-bd6a-56b1a18497d8/home/username[/FONT][/COLOR]
```

which yielded the following result.

```

[COLOR=#000000]xubuntu@xubuntu:~$ sudo ls -l /media/fdf81723-08d4-4be4-bd6a-56b1a18497d8/home/username
[/COLOR][COLOR=#000000]total 0
[/COLOR][COLOR=#000000]lrwxrwxrwx 1 1000 1000 56 Sep 19 16:52 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
[/COLOR][COLOR=#000000]lrwxrwxrwx 1 1000 1000 52 Sep 19 16:52 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt[/COLOR][COLOR=#000000]
[/COLOR]
```

opening up 

```
[COLOR=#000000][FONT=Ubuntu Mono]/usr/share/ecryptfs-utils/ecryptfs-mount-private.txt[/FONT][/COLOR]
```

yielded a result that stated that my home has been unmounted for security , and I can mount it using the ecryptfs-mount something rather command

I decided not to go a step further in order to not damage anything.
both results happen twice on both laptops-except that the numbers where different during fdisk -l (that encrypted the home directory using different methods-one using the ubuntu install gui one using the terminal after by creating a temp account ...moving files..encrypting deleting old)
Can I conclude that my home directories are encrypted properly?
Or does this still conclude nothing and that only my swap is encrypted?

Thanks in advance guys,
Psil0

---

### Post by TheFu on 2013-10-27
look for an look for an /home/.ecryptfs folder.

---

