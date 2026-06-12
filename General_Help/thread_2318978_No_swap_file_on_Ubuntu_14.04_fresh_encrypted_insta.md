---
title: "No swap file on Ubuntu 14.04 fresh encrypted install"
date: 2016-03-31
forum: General Help
---

### Post by jnemes23 on 2016-03-31
First of all, I want to say that I know similar questions have been posted and I'm sorry, but I'm in a period of recovery from an illness and my brain isn't working as well as usual.  I just could not piece together the solution from other posts this time.  

Ubuntu 14.04 install.  Noticed performance lag when using several intense applications.  I have 6gb of ram. Checked and there is no swapfile and I obviously need one as my computer will freeze up for a while if I'm using too much ram.

Thanks in advance for any step-by-step help anyone is willing to offer.  I am using Linux exclusively and would prefer not to bork it as I don't currently have the energy for a fresh install in my condition.  I have included some information that may be helpful.  

```
sudo swapon -a

swapon: /dev/mapper/ubuntu--vg-swap_1: read swap header failed: Invalid argument
swapon: /dev/mapper/cryptswap1: stat failed: No such file or directory 
```

Cryptab:
```

cat /etc/crypttab
sda3_crypt UUID=8992d06e-2c19-467e-af2d-1f49e7c59ce9 none luks,discard
cryptswap1 UUID=2aec9a27-8510-4c15-9ceb-a8b2927847bd /dev/urandom swap,cipher=aes-cbc-essiv:sha256


```

Fstab:
```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=f0fc8d75-f0b6-4517-8278-7eeb36c0a42c /boot           ext2    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=0A3C-FD40  /boot/efi       vfat    defaults        0       1
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0



```

Partition list:
```

sudo fdisk -l
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.


Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08622858


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976766975   488382464    7  HPFS/NTFS/exFAT


Disk /dev/mapper/sda3_crypt: 999.4 GB, 999408271360 bytes
255 heads, 63 sectors/track, 121504 cylinders, total 1951969280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/sda3_crypt doesn't contain a valid partition table


Disk /dev/mapper/ubuntu--vg-root: 993.1 GB, 993060192256 bytes
255 heads, 63 sectors/track, 120732 cylinders, total 1939570688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table


Disk /dev/mapper/ubuntu--vg-swap_1: 6337 MB, 6337593344 bytes
255 heads, 63 sectors/track, 770 cylinders, total 12378112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

```

---

### Post by frostschutz on 2016-03-31
Normally you use either ubuntu-vg-swap or cryptswap, not both.

The ubuntu-vg-swap is what you want if you have LVM on LUKS (check using lsblk). It should be suitable for Hibernate (Suspend to disk).

Here is example lsblk output for LVM on LUKS on RAID: (my VG is named SSD, in your case it would say ubuntu- instead of SSD-)

```

NAME                               MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                                  8:0    0  59.6G  0 disk  
&#9492;&#9472;sda1                               8:1    0  59.6G  0 part  
  &#9492;&#9472;md0                              9:0    0  59.6G  0 raid1 
    &#9492;&#9472;luksSSD1                     253:9    0  59.6G  0 crypt 
      &#9500;&#9472;SSD-root                   253:10   0    18G  0 lvm   /
      &#9492;&#9472;SSD-home                   253:41   0    36G  0 lvm   /home

```

The cryptswap is just random encrypted swap created dynamically at boot - which is fine for swapping, but it is not suitable for Hibernate.

Ubuntu has a bug with its cryptswap setup. The crypttab entry you have shown can not possibly work. The UUID it is looking for, is lost the moment the swap is created, so at best it works only once.

With the UUID lost, we also no longer know which partition was designated to be used as swap partition. Your fdisk output is not showing your partitions either because you are using GPT and your fdisk can not yet handle GPT.

Please show your partition table by using 'parted /dev/sda unit mib print free'. And which of these partitions (if any) should be swap...

---

### Post by frostschutz on 2016-03-31
There is an example for a working crypttab entry for cryptswap over at the ArchLinux Wiki: [https://wiki.archlinux.org/index.php/Dm-crypt/Swap_encryption#UUID_and_LABEL](https://wiki.archlinux.org/index.php/Dm-crypt/Swap_encryption#UUID_and_LABEL)

It's sort of a hack: it uses a small 1 megabyte ext filesystem to provide a UUID or LABEL for the swap parititon, and uses an offset for the encrypted swap so this filesystem UUID/label survives reboots.

This method also works for Ubuntu except in Ubuntu you also need to add the option: precheck=/bin/true

---

### Post by jnemes23 on 2016-04-02
as requested:

```
$ sudo parted /dev/sda unit mib print free


Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 953870MiB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start      End        Size       File system  Name  Flags
        0.02MiB    1.00MiB    0.98MiB    Free Space
 1      1.00MiB    513MiB     512MiB     fat32              boot
 2      513MiB     757MiB     244MiB     ext2
 3      757MiB     953869MiB  953112MiB
        953869MiB  953870MiB  0.69MiB    Free Space



```

---

### Post by jnemes23 on 2016-04-08
BUMP

Can anyone help me with this or should I just go ahead and reinstall without using full disk encryption to avoid this again?

Thanks!

---

### Post by frostschutz on 2016-04-08
Your partition table looks like a full LVM install. And according to your crypttab it's fully encrypted (sda3_crypt).

In this case you should just remove the cryptswap1 entry from crypttab altogether. And in its place, if you want swap at all, create a logical volume for swap. Since the entire LVM is encrypted, that LV would be encrypted along with it.

Your fstab suggests you already have such a swap volume anyway ( 
ubuntu--vg-swap_1

) if that works you won't need anything else.

I'm wondering why it created a cryptswap entry for you at all. Did you choose full LUKS encryption, and then again home encryption? That would encrypt everything twice which is usually not very useful.

Related commands of interest: free -m, lsblk, vgdisplay, lvdisplay, ...

---

### Post by jnemes23 on 2016-04-08
I probably did do full disk encryption *and* home directory encryption without knowing it would be redundant. At this point I'm thinking I have no choice but to reinstall, I'm having too many problems with my system (for instance, typing anything in the Unity dash right now results in "Sorry, there is nothing that matches your search").

I absolutely need a swap file with only 6gb of ram, and I don't think I can fix this issue alone.  My brain is too fried from health problems.  I guess I have learned a lot from this install so it won't be a total loss.  This is the first time I have used Linux exclusively without a dual Windows boot and thus I have learned a lot more.

On an unrelated issue, wonder why so many guides suggest that you only need a 200MB boot partiton. I constantly have problems with low disk space when a new kernel is installed.  I don't want to have to delete old kernels *every* time I install a new one, it is very inconvenient.

You seem to know a lot, [FONT=arial]frostschutz, can you recommend any favorite guides that would help me avoid some common pitfalls and understand better a modern partitioning scheme?  I have followed guides but as you can tell I have still made mistakes.

[/FONT]As poor as my knowledge is, I have used Linux in one way or another since 1996, but I still run into plenty of trouble.

---

### Post by frostschutz on 2016-04-08
> **jnemes23 said:**
> On an unrelated issue, wonder why so many guides suggest that you only need a 200MB boot partiton.

 I constantly have problems with low disk space when a new kernel is  installed.  I don't want to have to delete old kernels *every* time I  install a new one, it is very inconvenient.

This is a recommendation that dates back 10+ years when kernels were still tiny in comparison to today. If the installer chooses such sizes by itself, it should be reported as a bug.

Nowadays kernels are just huge. Even if you custom compile it and toss everything out that's not needed, you're already past the 10MB mark per kernel. With a generic kernel like Ubuntu's that's supposed to work on any hardware and support everything no matter how exotic it may be - a single kernel might break the 100MB barrier. It's not quite that bad yet but getting close.

So I think 512MB is the minimum for a boot partition that holds maybe 2-3 old kernels. If you are not tight on disk space, it's not wrong to spend 1GB. But even so, over time you'll just have to uninstall old kernels if the package manager is still not smart enough to do so automagically.

---

