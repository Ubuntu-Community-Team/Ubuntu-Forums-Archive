---
title: "fsck dispalys &quot;fail&quot; messages at boot...."
date: 2007-08-07
forum: General Help
---

### Post by rogsmejl on 2007-08-07
When booting up Mint, I get the following message (from /var/log/fsck/checkfs)

Log of fsck -C -R -A -a
Wed Aug 8 00:45:35 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/sda10: clean, 1372/2011296 files, 735151/4018250 blocks (check after next mount)
fsck.ext2: Unable to resolve 'UUID=01aaad96-9ba5-4c29-9f47-1758cda62922'

fsck.ext2: Unable to resolve 'UUID=a219b048-716e-4172-9353-157c41bab3f7'

/dev/sda5: clean, 177820/1360896 files, 4677232/10883972 blocks
/dev/sda7: clean, 441/1762304 files, 267478/14097004 blocks
fsck died with exit status 8

Wed Aug 8 00:45:35 2007
----------------
The system halts at prompt asking me to resolve the issue manually.
I can still boot the system by entering "Ctrl + D"

After starting Mint, the system "freezes" constantly for no apparent reason, (meaning that it totally or partially stops to respond) often while browsing with Firefox. I don't know if the two issues have a common cause.

I have a dual boot with LinuxMint and Mandriva 2007 on the same disk, (tried to take a screen picture of the partition table to post here but failed).

I will be very obliged to anyone who can advise me on how to resolve these annoying issues???....

---

### Post by meierfra on 2007-08-07
I'm not sure what is going on, but could you post the output of

```
sudo fdisk -l
```


```
sudo blkid 
```

and

```
gksudo gedit /etc/fstab
```

---

### Post by rogsmejl on 2007-08-08
Thanks for getting back meierfra

Here U go...


If your life was a horse, you'd have to shoot it.
pappsan@pappsan-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 122,9 GB, 122942324736 byte
255 huvuden, 63 sektorer/spår, 14946 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1        7649    61440561    5  Utökad
/dev/sda5               1        1355    10883974+  83  Linux
/dev/sda6            1356        2069     5735173+  82  Linux växling / Solaris
/dev/sda7            2070        3824    14097006   83  Linux
/dev/sda8            3825        5040     9767488+  83  Linux
/dev/sda9            5041        5648     4883728+  82  Linux växling / Solaris
/dev/sda10           5649        7649    16073001   83  Linux


You will live a long, healthy, happy life and make bags of money.
pappsan@pappsan-desktop:~$ sudo blkid
Password:
/dev/sda5: UUID="2f783cf6-402f-11dc-bcf8-8b79549d6436" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="35b13f64-402f-11dc-b903-2b74f97bff57" TYPE="swap" 
/dev/sda7: UUID="35bc0fc0-402f-11dc-9acc-f73217d15239" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="03f49306-731d-44ba-9681-a3530a672fa7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="0785563e-e9d0-4d4b-8eb3-69c73cadb0c0" TYPE="swap" 
/dev/sda10: UUID="08bafb5b-3797-4a30-aa19-405af673807b" SEC_TYPE="ext2" TYPE="ext3" 
pappsan@pappsan-desktop:~$ 


pappsan@pappsan-desktop:~$ 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=03f49306-731d-44ba-9681-a3530a672fa7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda10
UUID=08bafb5b-3797-4a30-aa19-405af673807b /home           ext3    defaults        0       2
# /dev/sda3
UUID=01aaad96-9ba5-4c29-9f47-1758cda62922 /media/sda3     ext2    defaults        0       2
# /dev/sda4
UUID=a219b048-716e-4172-9353-157c41bab3f7 /media/sda4     ext2    defaults        0       2
# /dev/sda5
UUID=2f783cf6-402f-11dc-bcf8-8b79549d6436 /media/sda5     ext3    defaults        0       2
# /dev/sda7
UUID=35bc0fc0-402f-11dc-9acc-f73217d15239 /media/sda7     ext3    defaults        0       2
# /dev/sda6
UUID=35b13f64-402f-11dc-b903-2b74f97bff57 none            swap    sw              0       0
# /dev/sda9
UUID=0785563e-e9d0-4d4b-8eb3-69c73cadb0c0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by meierfra on 2007-08-08
It seems that you have a problem with two of you partitions (sda3 and sda4). They don't show up in "fdisk -l" and  fsck isn't able to check on them during boot up. 
Do you know what is on these partitions ( they are supposed to be mounted in /media/sda3 and /media/sda4) ?

I don't think your firefox problem is related. firefox is giving lots of people problems, including myself. I just hope the next version is more stable.

---

### Post by rogsmejl on 2007-08-08
I decided to do a re-install instead which resolved the issues.
Fortunately I had created a HOME-partition at the first installation, so my files and stuff were intact after the re-install.

Many thanks meierfra for all the help... I really appreciate.

---

