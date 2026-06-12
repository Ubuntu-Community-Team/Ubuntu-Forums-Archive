---
title: "dpkg: unrecoverable fatal error"
date: 2016-03-13
forum: General Help
---

### Post by dali5 on 2016-03-13
Need some help, have tried some methods that are suggested to people that had same kind of problems, but nothing works for me. 

```
dali@dali-X75VC:~$  sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gstreamer1.0-libav gstreamer1.0-libav:i386
The following packages will be upgraded:
  bind9-host dnsutils firefox flashplugin-installer gir1.2-gstreamer-1.0
  gstreamer1.0-tools libbind9-90 libbsh-java libdns-export100 libdns100
  libgstreamer1.0-0 libgstreamer1.0-0:i386 libirs-export91 libisc-export95
  libisc95 libisccc90 libisccfg-export90 libisccfg90 liblwres90
  libnautilus-extension1a libnss3 libnss3-nssdb liboxideqt-qmlplugin
  liboxideqtcore0 liboxideqtquick0 libsmbclient libwbclient0 nautilus
  nautilus-data oxideqt-codecs python-samba samba-common samba-common-bin
  samba-libs thunderbird thunderbird-gnome-support
36 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/117 MB of archives.
After this operation, 4318 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: unrecoverable fatal error, aborting:
 unable to create '/var/lib/dpkg/updates/tmp.i': Stale file handle
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by Bashing-om on 2016-03-13
dali5; Hello; Welcome to the forum,

Many times we see this condition due to a lack of disk space.

Post back = Between Code Tags = the outputs of terminal commands:
```

df -h
df -i
sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
and we see where we go from here.

[INDENT][INDENT]6 pounds of sugar in a 5 pound sack ?[/INDENT][/INDENT]

---

### Post by dali5 on 2016-03-13
hallo, thanks for the reply. Sorry about posting my code just like that , i didnt knew... 
So here are the results of the commands : 
```
dali@dali-X75VC:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1,9G     0  1,9G   0% /dev
tmpfs           384M  6,2M  378M   2% /run
/dev/sda6        52G   15G   38G  28% /
tmpfs           1,9G  348K  1,9G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           1,9G     0  1,9G   0% /sys/fs/cgroup
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           384M   44K  384M   1% /run/user/1000
/dev/sr0        708M  708M     0 100% /media/dali/Disk
dali@dali-X75VC:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
udev             486955    563   486392    1% /dev
tmpfs            491259    786   490473    1% /run
/dev/sda6      78477952 354502 78123450    1% /
tmpfs            491259     10   491249    1% /dev/shm
tmpfs            491259      6   491253    1% /run/lock
tmpfs            491259     17   491242    1% /sys/fs/cgroup
cgmfs            491259     13   491246    1% /run/cgmanager/fs
tmpfs            491259     27   491232    1% /run/user/1000
/dev/sr0              0      0        0     - /media/dali/Disk
dali@dali-X75VC:~$ sudo fdisk -lu
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 465,8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf8fe70c6

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *           65 689750774 689750710 328,9G  7 HPFS/NTFS/exFAT
/dev/sda2       689752064 728821759  39069696  18,6G  7 HPFS/NTFS/exFAT
/dev/sda3       732733438 976769023 244035586 116,4G  5 Extended
/dev/sda4       728821760 732727295   3905536   1,9G 82 Linux swap / Solaris
/dev/sda5       841228288 976769023 135540736  64,6G  7 HPFS/NTFS/exFAT
/dev/sda6       732733440 841220095 108486656  51,7G 83 Linux

Partition table entries are not in disk order.

```

---

### Post by Bashing-om on 2016-03-13
dali5; Hummm ..

Not at all sure of what I am seeing --- all those "Disk /dev/ram" allocations from bios for Windows use. I do not know how the memory allocation would effect ubuntu.

But as this is NOT a disk usage space constraint issue, we can look at it as a file system error.
What returns:
```

ls -al /var/lib/dpkg/updates/

```

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by dali5 on 2016-03-14
thank you for your time wasting with my problem Bashing-om
.. so this returns :
```


dali@dali-X75VC:~$ ls -al /var/lib/dpkg/updates/
total 32
drwxr-xr-x 2 root root     8 Mär  7 10:51 .
drwxr-xr-x 8 root root 12288 Mär 13 13:06 ..
-rw-r--r-- 1 man  root 12462 Okt 21 17:59 tmp.i



```

---

### Post by Bashing-om on 2016-03-14
dali5; Good morning .

> 
thank you for your time wasting 

WRONG ! NOT in the least wasted time ! As it helps you in many ways, and I too progress on this curve of learning. Bottom line is that I do this because I want to . It is also "bread cast on the waters" . 

To the problem at hand.
we have:
> 
unable to create '/var/lib/dpkg/updates/tmp.i': Stale file handle


but the file does exist .. maybe have the system make it up once more ?? Mind you I do not know that it will, this is that "learning curve", and why we make a backup of the file prior to removing it . That way if there is a problem, we can put it back !

How 'bout we do:
```

sudo cp /var/lib/dpkg/updates/tmp.i /var/lib/dpkg/updates/tmp.i-14Mar2016
sudo rm /var/lib/dpkg/updates/tmp.i
sudo apt update
sudo apt upgrade

```

What now does the system and package manager relate ? Post back all those results, and we see where we go from here .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by dali5 on 2016-03-14
Well that perfectly solved my problems, i can now upgrade, update, install ...  

Thank You very  much Sir !!   God bless you !!

---

### Post by Bashing-om on 2016-03-14
dali5; Great !

I take your blessing with gratitude .

Now IF and only IF there are no problems with the system, 
clean up the debris:
```

sudo rm /var/lib/dpkg/updates/tmp.i-14Mar2016

```

and verify that the system has cleaned up after it's self, that the file " tmp.i " is no longer needed and the system has removed it:
```

ls -al /var/lib/dpkg/updates/tmp.i

```

[INDENT][INDENT]all finer than a frog's hair
[/INDENT][/INDENT]

---

### Post by dali5 on 2016-03-14
done that , thanks a lot !!

---

