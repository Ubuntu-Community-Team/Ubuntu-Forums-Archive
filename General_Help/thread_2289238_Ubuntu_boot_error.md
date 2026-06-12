---
title: "Ubuntu boot error"
date: 2015-08-02
forum: General Help
---

### Post by Lightning Dragon on 2015-08-02
Okay, so long story short...I had a seperate drive that I installed Windows 10 on. For a bout a week it ran fine. Nothing wrong. However, last night it wanted two updates: an AMD driver update and a system update. I performed the AMD driver update first, and then the Windows 10 update. Upon rebooting like it wanted, I suppose it turned itself off mid-update. Now rebooting back in I was given a blue screen of death with "NTFS_FILE_SYSTEM" as the only error indication besides that stupid frowning face.

Whatever. I decided to log into Windows 7 to figure out how to fix 10. Nope. 7 is now reporting the following:

After numerous attempts to use Startup Repair to fix Win7, it failed. So angrily I loaded up Ubuntu to try and backup really important files on Win7 and Ubuntu, my main OS. It worked, I was in and got to move a few things to Ubuntu in order to transfer them over to a drive. However, upon trying to use the terminal I started experiencing really odd issues. It kept saying something about sudo not existing in /tmp/username/root (may have the order wrong; it went real fast) and then the system froze. I restarted and upon rebooting into Ubuntu, I am greeted with a screen telling me:[INDENT]The disk drive for / is not ready yet or not present
[/INDENT]

I pressed *S* and then it said:[INDENT]The disk drive for /tmp is not ready yet or not present
[/INDENT]

I can get into the command window that follows by pressing *M*. I turned off my machine and hooked up my USB that I keep a Ubuntu installer on to check out the system. However I can't see any of my drives, Windows or Ubuntu, like I usually can when opening up a "Try Ubuntu" environment.

What do I do? I have incredibly important things on Ubuntu, as well as Windows. Is there anything I can do to recover my systems long enough to just backup the data?

Here is the output of sudo fdisk -l:

```
sudo fdisk -l

Disk /dev/loop0: 1.1 GiB, 1147891712 bytes, 2241976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/loop1: 1000 MiB, 1048576000 bytes, 2048000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 29A5B19C-7989-45F6-A1AD-D126B5C36918

Device         Start       End   Sectors   Size Type
/dev/sda1       2048    194559    192512    94M EFI System
/dev/sda2     194560 964438015 964243456 459.8G EFI System
/dev/sda3  964438016 976771071  12333056   5.9G Linux swap

Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: D0E2ED7D-0138-4E11-A5B7-16A58B013F6C

Device      Start       End   Sectors   Size Type
/dev/sdb1    2048    206847    204800   100M EFI System
/dev/sdb2  206848    468991    262144   128M Microsoft reserved
/dev/sdb3  468992 976773119 976304128 465.6G EFI System

Disk /dev/sdc: 7.3 GiB, 7803174912 bytes, 15240576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x20ac7dda

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdc1  ?    3224498923 3657370039  432871117 206.4G  7 HPFS/NTFS/exFAT
/dev/sdc2  ?    3272020941 5225480974 1953460034 931.5G 16 Hidden FAT16
/dev/sdc3  ?             0          0          0     0B 6f unknown
/dev/sdc4         50200576  974536369  924335794 440.8G  0 Empty

Partition table entries are not in disk order.

```

**Boot-Repair Summary:**

[http://paste.ubuntu.com/11987574/](http://paste.ubuntu.com/11987574/)

Boot-Repair also says I have "Ubuntu 14.04 LTS" and "Windows" if I click "GRUB Location" tab and then check the dropbox of "OS to boot by Default".

Oh, and just in case it is important...on boot of Ubuntu it reported "The volume "efi" has only "0" bytes left". 

If you need any other outputs, please say so and I will gladly provide them.

Thank you!

---

### Post by Bashing-om on 2015-08-02
Lightning Dragon; Scary situation.

'fdisk' does not cope with GPT partitioning, let's use different tools and take a look at the hard drive partitioning before we say else.
Boot up the liveUSB, and let's look
```

sudo parted -l
sudo blkid
sudo apt-get install gdisk
sudo gdisk -l /dev/sda
sudo gdisk -l /dev/sdb

```
and see what there is to work with.

[INDENT][INDENT]bad things can happen
[INDENT][INDENT]we work toward making things right
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Lightning Dragon on 2015-08-02
> **Bashing-om said:**
> Lightning Dragon; Scary situation.

'fdisk' does not cope with GPT partitioning, let's use different tools and take a look at the hard drive partitioning before we say else.
Boot up the liveUSB, and let's look
```

sudo parted -l
sudo blkid
sudo apt-get install gdisk
sudo gdisk -l /dev/sda
sudo gdisk -l /dev/sdb

```
and see what there is to work with.[INDENT][INDENT]bad things can happen[INDENT][INDENT]we work toward making things right
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


It is very frustrating. :( I have had my issues of booting, but I have never had an issue like this before.

So I managed to boot into my Ubuntu drive. I managed to do this with the a LiveUSB (don't have cds/dvds) and ran boot-repair once. I am back in my Ubuntu system but the "The volume "efi has only 0 bytes remaining" errors still occur. I pressed "examine" and this is what it shows me...many upon many boot-repair log folders or something:

[http://i.imgur.com/Nf2lxUW.png](http://i.imgur.com/Nf2lxUW.png)
[http://i.imgur.com/y6mE8d4.png](http://i.imgur.com/y6mE8d4.png)
[SIZE=1] (totals to 73.5 mb and I can no longer save or make any files anywhere on my syste...I'm assuming this is due to space)[/SIZE]

Anyways, I tried to run the command in my system but it reports the following:

```
ld@Solsum:~$ sudo parted -l
[sudo] password for ld: 
sudo: unable to open /var/lib/sudo/ld/0: No such file or directory

```

And then it immediately closes, no matter what I try. I had to time a picture to get the above information. So I loaded up the LiveUSB again and opened the terminal to do the commands. However, it too reports the same thing however the "username" isn't apart of it, it is just "/var/lib/sudo/0: No such file or directory". I cannot progress any further. Oh, and when I attempt to open files, delete them, move them etc I get an error and in details it states "**Unable to create trashing info file: Read-only file system**".

I opened GIMP to edit one of the images above, too, and it gave me this. I am just trying to give as much as I can in case it might help lead towards a solution.

```
Unable to open a test swap file.
To avoid data loss, please check the location and permissions of the swap directory defined in your Preferences (currently "/home/ld/.gimp-2.8").
```

I am in the process of reburning a 14.04 to a USB to see if that is the problem with the LiveUSB. I will edit this post if it succeeds and will include the outputs.

---

### Post by Bashing-om on 2015-08-02
Lightning Dragon' Hummm ..

No space left on device can result in all kinds of problems.
If you are able to boot into the install, we can look and see what the space constraints are:
```

df -h
df -i
cd /
sudo du -sx * | sort -n

```

a quick look at the authentication issue:
```

egrep ':[0-9]{4}:' /etc/passwd

```
indepth
```

cat /etc/passwd

```
 a quick look if 'YOU" are you.
```

who
groups

```


Keep'n in mind that no operating headroom, and the system mounted 'read only' might be the why can not so anything.

We look about, try and identify what needs the fix'n
[INDENT][INDENT]then go to work on the real issue
[/INDENT][/INDENT]

---

### Post by Lightning Dragon on 2015-08-02
> **Bashing-om said:**
> Lightning Dragon' Hummm ..

No space left on device can result in all kinds of problems.
If you are able to boot into the install, we can look and see what the space constraints are:
```

df -h
df -i
cd /
sudo du -sx * | sort -n

```

a quick look at the authentication issue:
```

egrep ':[0-9]{4}:' /etc/passwd

```
indepth
```

cat /etc/passwd

```
 a quick look if 'YOU" are you.
```

who
groups

```


Keep'n in mind that no operating headroom, and the system mounted 'read only' might be the why can not so anything.

We look about, try and identify what needs the fix'n[INDENT][INDENT]then go to work on the real issue
[/INDENT]
[/INDENT]



Outputs:

```
ld@Solsum:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       453G  200G  231G  47% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.9G   12K  3.9G   1% /dev
tmpfs           793M  1.7M  792M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  160K  3.9G   1% /run/shm
none            100M   40K  100M   1% /run/user
/dev/sdc1       299G  175G  124G  59% /media/Games
/dev/sdb1        96M   96M     0 100% /boot/efi
/dev/sdd        7.3G  2.1G  5.2G  29% /media/ld/MYLINUXLIVE (< my LiveUSB)
/dev/sr1        666M  666M     0 100% /media/ld/WD SmartWare

```

```
ld@Solsum:~$  df -i
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
/dev/sda2       30138368 600187  29538181    2% /
none             1014949      2   1014947    1% /sys/fs/cgroup
udev             1012277    657   1011620    1% /dev
tmpfs            1014949    754   1014195    1% /run
none             1014949      3   1014946    1% /run/lock
none             1014949      8   1014941    1% /run/shm
none             1014949     26   1014923    1% /run/user
/dev/sdc1      129883464  35435 129848029    1% /media/Games
/dev/sdb1              0      0         0     - /boot/efi
/dev/sdd               0      0         0     - /media/ld/MYLINUXLIVE
/dev/sr1            1454   1454         0  100% /media/ld/WD SmartWare

```

```
ld@Solsum:~$  cd /
ld@Solsum:/$ 

```

The command "sudo du -sx * | sort -n" crashed the terminal.

```
ld@Solsum:~$ egrep ':[0-9]{4}:' /etc/passwd
ld:x:1000:1000:LD,,,:/home/ld:/bin/bash

```

```
ld@Solsum:~$ cat /etc/passwd

```

Another crash.

```
ld@Solsum:~$ who
ld    :0           2015-08-02 20:53 (:0)
ld    pts/0        2015-08-02 18:00 (:0)
ld@Solsum:~$ groups
ld adm cdrom sudo dip plugdev lpadmin sambashare

```

---

### Post by Bashing-om on 2015-08-02
Lightning Dragon; wehelll ...

We know the source of 1 problem:
> 
/dev/sdb1        96M   96M     0 100% /boot/efi


Let's work on that, but I do not see there to be a relationship here to the crashing.

What returns:
```

dpkg -l | grep linux-
ls -al /boot
ls -al /boot/efi

```
Be aware ..... I do not consider myself qualified to work in EFI . However, we can struggle on.

Are you still mounted read only ?
Maybe we can do :
```

sudo apt-get autoremove

```
see if the package manager has the operating head room in which to operate.

One thing for sure, we have to get some head room .

[INDENT][INDENT][INDENT]let the fight begin
[/INDENT][/INDENT][/INDENT]

---

### Post by Lightning Dragon on 2015-08-02
> **Bashing-om said:**
> Lightning Dragon; wehelll ...

We know the source of 1 problem:


Let's work on that, but I do not see there to be a relationship here to the crashing.

What returns:
```

dpkg -l | grep linux-
ls -al /boot
ls -al /boot/efi

```
Be aware ..... I do not consider myself qualified to work in EFI . However, we can struggle on.

Are you still mounted read only ?
Maybe we can do :
```

sudo apt-get autoremove

```
see if the package manager has the operating head room in which to operate.

One thing for sure, we have to get some head room .[INDENT][INDENT][INDENT]let the fight begin
[/INDENT]
[/INDENT]
[/INDENT]


"dpkg -l | grep linux-" 

Crashes my terminal. I'm not sure if I should posst the rest of the commands without the first, but I tried anyways. The second one crashes the terminal as well, but the third works:

```
ld@Solsum:~$  ls -al /boot/efi
total 7
drwxr-xr-x 4 root root 1024 Dec 31  1969 .
drwxr-xr-x 5 root root 4096 Aug  2 04:53 ..
drwxr-xr-x 4 root root 1024 Jan 14  2015 boot-sav
drwxr-xr-x 5 root root 1024 Feb  2  2014 EFI

```

```
ld@Solsum:~$  sudo apt-get autoremove
[sudo] password for ld: 
sudo: unable to open /var/lib/sudo/ld/0: No such file or directory
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

```

Yes, I am still read only. Because of that, no adobe or java or programs/software is working right either.

I appreciate the help. If I could just access my Windows drive to backup one folder, I would be happy and reinstall everything. [-o<

EDIT

I'm about to test my USB now. I will be back shortly! :)

---

### Post by Lightning Dragon on 2015-08-02
Success for LiveUSB! I cannot see my Ubuntu install, or my Windows install though. The outputs of all commands given:

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000AAKS-6 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  99.6MB  98.6MB  fat32                 boot
 2      99.6MB  494GB   494GB   ext4                  boot
 3      494GB   500GB   6315MB  linux-swap(v1)


Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                          Flags
 1      1049kB  106MB  105MB  fat32        EFI system partition          boot
 2      106MB   240MB  134MB               Microsoft reserved partition  msftres
 3      240MB   500GB  500GB  ntfs         Basic data partition          boot


Model: ATA WDC WD3200AAKS-0 (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary  ntfs         boot


Model: Kingston DataTraveler SE9 (scsi)
Disk /dev/sdd: 7803MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  7803MB  7803MB  fat32

```

```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="636f3ff7-c08c-8e41-8910-2c9e31d0a7a3" TYPE="ext2" 
/dev/sda1: UUID="5263-5DAA" TYPE="vfat" 
/dev/sda2: UUID="d5cad172-4a97-44c5-82fd-8a6d4871a39d" TYPE="ext4" 
/dev/sda3: UUID="e25ccd0b-5fa3-4212-ad90-07d477583371" TYPE="swap" 
/dev/sdb1: UUID="641C-3B35" TYPE="vfat" 
/dev/sdb3: UUID="507AF9077AF8EB1C" TYPE="ntfs" 
/dev/sdc1: LABEL="Games" UUID="3EF44951F4490D19" TYPE="ntfs" 
/dev/sdd: LABEL="MYLINUXLIVE" UUID="0C9B-7DB4" TYPE="vfat" 

```

```
ubuntu@ubuntu:~$ sudo apt-get install gdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdisk is already the newest version.
gdisk set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 29A5B19C-7989-45F6-A1AD-D126B5C36918
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 4077 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          194559   94.0 MiB    EF00  
   2          194560       964438015   459.8 GiB   EF00  
   3       964438016       976771071   5.9 GiB     8200  

```

```
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): D0E2ED7D-0138-4E11-A5B7-16A58B013F6C
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2029 sectors (1014.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  EFI system partition
   2          206848          468991   128.0 MiB   0C01  Microsoft reserved part
   3          468992       976773119   465.5 GiB   EF00  Basic data partition

```

```
ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            969M  114M  806M  13% /
udev            3.9G  8.0K  3.9G   1% /dev
tmpfs           793M  1.5M  792M   1% /run
/dev/sdd        7.3G  2.1G  5.2G  29% /cdrom
/dev/loop0      953M  953M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           3.9G  1.1M  3.9G   1% /tmp
none            5.0M  4.0K  5.0M   1% /run/lock
none            3.9G   80K  3.9G   1% /run/shm
none            100M   64K  100M   1% /run/user
ubuntu@ubuntu:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/cow            256000   1054  254946    1% /
udev           1012081    612 1011469    1% /dev
tmpfs          1014953    707 1014246    1% /run
/dev/sdd             0      0       0     - /cdrom
/dev/loop0      179796 179796       0  100% /rofs
none           1014953      2 1014951    1% /sys/fs/cgroup
tmpfs          1014953     17 1014936    1% /tmp
none           1014953      2 1014951    1% /run/lock
none           1014953      5 1014948    1% /run/shm
none           1014953     32 1014921    1% /run/user

```

```

ubuntu@ubuntu:~$ cd /
ubuntu@ubuntu:/$ sudo du -sx * | sort -n
du: cannot access &#8216;proc/17934/task/17934/fd/4&#8217;: No such file or directory
du: cannot access &#8216;proc/17934/task/17934/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;proc/17934/fd/4&#8217;: No such file or directory
du: cannot access &#8216;proc/17934/fdinfo/4&#8217;: No such file or directory
0    bin
0    initrd.img
0    lib
0    lib64
0    mnt
0    opt
0    proc
0    root
0    sbin
0    srv
0    sys
4    media
4    tmp
8    boot
8    dev
16    lost+found
72    etc
184    usr
196    var
460    home
1492    run
2199740    cdrom
2801506    rofs

```

```
egrep ':[0-9]{4}:' /etc/passwd
```
No output

```

ubuntu@ubuntu:/$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
libuuid:x:100:101::/var/lib/libuuid:
syslog:x:101:104::/home/syslog:/bin/false
messagebus:x:102:106::/var/run/dbus:/bin/false
usbmux:x:103:46:usbmux daemon,,,:/home/usbmux:/bin/false
dnsmasq:x:104:65534:dnsmasq,,,:/var/lib/misc:/bin/false
avahi-autoipd:x:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
kernoops:x:106:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
rtkit:x:107:114:RealtimeKit,,,:/proc:/bin/false
saned:x:108:115::/home/saned:/bin/false
whoopsie:x:109:116::/nonexistent:/bin/false
speech-dispatcher:x:110:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
avahi:x:111:117:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
lightdm:x:112:118:Light Display Manager:/var/lib/lightdm:/bin/false
colord:x:113:121:colord colour management daemon,,,:/var/lib/colord:/bin/false
hplip:x:114:7:HPLIP system user,,,:/var/run/hplip:/bin/false
pulse:x:115:122:PulseAudio daemon,,,:/var/run/pulse:/bin/false
ubuntu:x:999:999:Live session user,,,:/home/ubuntu:/bin/bash

```

```

ubuntu@ubuntu:/$ who
ubuntu   tty4         2015-08-02 18:44
ubuntu   tty6         2015-08-02 18:44
ubuntu   tty3         2015-08-02 18:44
ubuntu   tty5         2015-08-02 18:44
ubuntu   tty2         2015-08-02 18:44
ubuntu   tty1         2015-08-02 18:44
ubuntu   pts/0        2015-08-02 22:49 (:0)
ubuntu   :0           2015-08-02 22:46 (:0)
ubuntu@ubuntu:/$ groups
ubuntu adm cdrom sudo dip plugdev lpadmin sambashare

```

```

ubuntu@ubuntu:/$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.11                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-utopic                              3.16.0.30.23                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.16.0-30                               3.16.0-30.40~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-30-generic                       3.16.0-30.40~14.04.1                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-generic-lts-utopic                      3.16.0.30.23                                        amd64        Generic Linux kernel headers
ii  linux-image-3.16.0-30-generic                         3.16.0-30.40~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-30-generic                   3.16.0-30.40~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-utopic                        3.16.0.30.23                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-45.74                                        amd64        Linux Kernel Headers for development
ii  linux-signed-generic-lts-utopic                       3.16.0.30.23                                        amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-3.16.0-30-generic                  3.16.0-30.40~14.04.1                                amd64        Signed kernel image generic
ii  linux-signed-image-generic-lts-utopic                 3.16.0.30.23                                        amd64        Signed Generic Linux kernel image
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

```

ubuntu@ubuntu:/$ ls -al /boot
total 34230
drwxr-xr-x 1 root root     4096 Aug  2 22:45 .
drwxrwxrwx 1 root root     4096 Aug  2 18:44 ..
-rw-r--r-- 1 root root  1207386 Jan 15  2015 abi-3.16.0-30-generic
-rw-r--r-- 1 root root   171768 Jan 15  2015 config-3.16.0-30-generic
drwxr-xr-x 1 root root     4096 Aug  2 18:44 grub
-rw-r--r-- 1 root root 29577011 Aug  2 22:45 initrd.img-3.16.0-30-generic
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3511040 Jan 15  2015 System.map-3.16.0-30-generic

```

```

ubuntu@ubuntu:/$ ls -al /boot/efi
ls: cannot access /boot/efi: No such file or directory

```

There, that's all of the commands except the "autoremove". :)

You might be interested to know what Gparted is doing:

[IMG]http://i.imgur.com/TToCpmc.png[/IMG]
[IMG]http://i.imgur.com/W78TDJ4.png[/IMG]

---

### Post by Bashing-om on 2015-08-02
Lightning Dragon; Hoy Boy !

I am undecided what to do, or where to look .
Dithering about .

I am hesitant to mount the file system for writing until we identify why the system insists on further protecting it's self by mounting read only;

No idea of why the system crashes running a couple of simple commands;

I do not know why the system will not allow you privileged  authorization;

I am not to this time sure about how to address the 'boot/efi' partition ;

Nor until the above is addressed do I want to tackle:
> 
E: The package lists or status file could not be parsed or opened.


Lemme ponder a bit on best practice to get us sudo'n .

[INDENT][INDENT]It I know it all
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Lightning Dragon on 2015-08-02
> **Bashing-om said:**
> Lightning Dragon; Hoy Boy !

I am undecided what to do, or where to look .
Dithering about .

I am hesitant to mount the file system for writing until we identify why the system insists on further protecting it's self by mounting read only;

No idea of why the system crashes running a couple of simple commands;

I do not know why the system will not allow you privileged  authorization;

I am not to this time sure about how to address the 'boot/efi' partition ;

Nor until the above is addressed do I want to tackle:


Lemme ponder a bit on best practice to get us sudo'n .[INDENT][INDENT]It I know it all[INDENT][INDENT][INDENT]I would not be me
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


It doesn't crash the entire system, just the terminal. Makes it crash/turn off.

Oh and after running the commands, I rebooted to get to my Ubuntu drive and found that my new USB key now reports back as "Bootmgr is missing". haha I did however manage to get gParted open and then went to my Windows drive to see what the !! marks were about. This is what Information says:

[IMG]http://i.imgur.com/GV2vfQX.png[/IMG]
[IMG]http://i.imgur.com/TjfzfTw.png[/IMG]
[IMG]http://i.imgur.com/AYItBqm.png[/IMG]
[IMG]http://i.imgur.com/ytLC3eC.png[/IMG]

And the "efi volume" thing:

[IMG]http://i.imgur.com/iQg2ir4.png[/IMG]
[IMG]http://i.imgur.com/qByn55M.png[/IMG]
[IMG]http://i.imgur.com/xVFh2C2.png[/IMG]



And guess what? I can now edit and remove things for some reason...what should I try now? All of the commands again?

---

### Post by Bashing-om on 2015-08-02
Lightning Dragon; K;

Then we can go back to working to free up space in ' /boot/efi'.

From your output we have :
> 
ld@Solsum:~$  ls -al /boot/efi
total 7
drwxr-xr-x 4 root root 1024 Dec 31  1969 .
drwxr-xr-x 5 root root 4096 Aug  2 04:53 ..
drwxr-xr-x 4 root root 1024 Jan 14  2015 boot-sav
drwxr-xr-x 5 root root 1024 Feb  2  2014 EFI


The documentation says we need to look at:
> 
Writes the EFI boot-loader to /boot/efi/EFI/$OS_NAME/grubx64.efi. Some Linux distributions will copy the GRUB modules and config to the UEFI ESP (e.g. Fedora) whilst others copy them to /boot/grub/ (e.g. Debian, Ubuntu, OpenSUSE). It also calls on efibootmgr to add a boot menu entry into the UEFI configuration of the system motherboard.


Now, I think as /boot/efi/ is not a part of the operating system that some means should exist within the extendable firmware interface to remove those unwanted entries ( generated by boot-repair ??). To that end I am looking to see what I can learn.

Maybe boot into the install and see what is there ?
```

ls -al /boot/efi/EFI/

```

We are not going to just arbitrarily remove them without knowing the effect ! I do be doing homework - the efibootmgr .

[INDENT][INDENT]read thrice
[INDENT][INDENT][INDENT]act once
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Lightning Dragon on 2015-08-02
> **Bashing-om said:**
> Lightning Dragon; K;

Then we can go back to working to free up space in ' /boot/efi'.

From your output we have :


The documentation says we need to look at:


Now, I think as /boot/efi/ is not a part of the operating system that some means should exist within the extendable firmware interface to remove those unwanted entries ( generated by boot-repair ??). To that end I am looking to see what I can learn.

Maybe boot into the install and see what is there ?
```

ls -al /boot/efi/EFI/

```

We are not going to just arbitrarily remove them without knowing the effect ! I do be doing homework - the efibootmgr .[INDENT][INDENT]read thrice[INDENT][INDENT][INDENT]act once
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


This is from my Ubuntu install, not the LiveUSB. :)

```
ld@Solsum:~$ ls -al /boot/efi/EFI/
total 5
drwxr-xr-x 5 root root 1024 Feb  2  2014 .
drwxr-xr-x 4 root root 1024 Dec 31  1969 ..
drwxr-xr-x 2 root root 1024 Aug  1 23:32 Boot
drwxr-xr-x 3 root root 1024 Jan 17  2014 Microsoft
drwxr-xr-x 2 root root 1024 Jan 13  2015 ubuntu

```


EDIT

Here are all the commands that I ran in LiveUSB on my Ubuntu install. Some of them are the same, others are really different:

```

ld@Solsum:~$ sudo parted -l
[sudo] password for ld: 
Model: ATA WDC WD5000AAKS-6 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  99.6MB  98.6MB  fat32                 boot
 2      99.6MB  494GB   494GB   ext4                  boot
 3      494GB   500GB   6315MB  linux-swap(v1)


Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                          Flags
 1      1049kB  106MB  105MB  fat32        EFI system partition          boot
 2      106MB   240MB  134MB               Microsoft reserved partition  msftres
 3      240MB   500GB  500GB  ntfs         Basic data partition          boot


Model: ATA WDC WD3200AAKS-0 (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  320GB  320GB  primary  ntfs         boot

```

```
ld@Solsum:~$ sudo blkid
/dev/sda1: UUID="5263-5DAA" TYPE="vfat" 
/dev/sda2: UUID="d5cad172-4a97-44c5-82fd-8a6d4871a39d" TYPE="ext4" 
/dev/sda3: UUID="e25ccd0b-5fa3-4212-ad90-07d477583371" TYPE="swap" 
/dev/sdb1: UUID="641C-3B35" TYPE="vfat" 
/dev/sdb3: UUID="507AF9077AF8EB1C" TYPE="ntfs" 
/dev/sdc1: LABEL="Games" UUID="3EF44951F4490D19" TYPE="ntfs" 

```

```
ld@Solsum:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 29A5B19C-7989-45F6-A1AD-D126B5C36918
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 4077 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          194559   94.0 MiB    EF00  
   2          194560       964438015   459.8 GiB   EF00  
   3       964438016       976771071   5.9 GiB     8200  

```

```
ld@Solsum:~$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): D0E2ED7D-0138-4E11-A5B7-16A58B013F6C
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2029 sectors (1014.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  EFI system partition
   2          206848          468991   128.0 MiB   0C01  Microsoft reserved part
   3          468992       976773119   465.5 GiB   EF00  Basic data partition

```

```
ld@Solsum:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       453G  203G  227G  48% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.9G   12K  3.9G   1% /dev
tmpfs           793M  1.7M  792M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  808K  3.9G   1% /run/shm
none            100M   60K  100M   1% /run/user
/dev/sdc1       299G  175G  124G  59% /media/Games
/dev/sdb1        96M   96M     0 100% /boot/efi

```

```
ld@Solsum:~$ cd /
ld@Solsum:~/$ sudo du -sx * | sort -n
du: cannot access &#8216;proc/7492/task/7492/fd/4&#8217;: No such file or directory
du: cannot access &#8216;proc/7492/task/7492/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;proc/7492/fd/4&#8217;: No such file or directory
du: cannot access &#8216;proc/7492/fdinfo/4&#8217;: No such file or directory
0    initrd.img
0    initrd.img.old
0    proc
0    sys
0    vmlinuz
0    vmlinuz.old
4    cdrom
4    lib64
4    srv
12    dev
16    lost+found
24    tmp
28    media
84    mnt
1640    run
3572    lib32
4228    libx32
9984    bin
12172    sbin
197980    boot
297824    etc
345964    opt
1270864    var
1292112    lib
5635768    usr
32724428    root
170760188    home

```

```
ld@Solsum:~/$ egrep ':[0-9]{4}:' /etc/passwd
ld:x:1000:1000:Ld,,,:/home/ld:/bin/bash

```

```
ld@Solsum:~/$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
libuuid:x:100:101::/var/lib/libuuid:
syslog:x:101:104::/home/syslog:/bin/false
messagebus:x:102:106::/var/run/dbus:/bin/false
usbmux:x:103:46:usbmux daemon,,,:/home/usbmux:/bin/false
dnsmasq:x:104:65534:dnsmasq,,,:/var/lib/misc:/bin/false
avahi-autoipd:x:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
kernoops:x:106:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
rtkit:x:107:114:RealtimeKit,,,:/proc:/bin/false
saned:x:108:115::/home/saned:/bin/false
whoopsie:x:109:116::/nonexistent:/bin/false
speech-dispatcher:x:110:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
avahi:x:111:117:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
lightdm:x:112:118:Light Display Manager:/var/lib/lightdm:/bin/false
colord:x:113:121:colord colour management daemon,,,:/var/lib/colord:/bin/false
hplip:x:114:7:HPLIP system user,,,:/var/run/hplip:/bin/false
pulse:x:115:122:PulseAudio daemon,,,:/var/run/pulse:/bin/false
ld:x:1000:1000:Ld,,,:/home/ld:/bin/bash
vboxadd:x:999:1::/var/run/vboxadd:/bin/false

```

```
ld@Solsum:~/$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.14                                            all          Firmware for Linux kernel drivers
ii  linux-generic-lts-utopic                              3.16.0.45.36                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-55                               3.13.0-55.94                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                       3.13.0-55.94                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-61                               3.13.0-61.100                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                       3.13.0-61.100                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-34                               3.16.0-34.47~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-34-generic                       3.16.0-34.47~14.04.1                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-37                               3.16.0-37.51~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-37-generic                       3.16.0-37.51~14.04.1                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-41                               3.16.0-41.57~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-41-generic                       3.16.0-41.57~14.04.1                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-45                               3.16.0-45.60~14.04.1                                all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-45-generic                       3.16.0-45.60~14.04.1                                amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.61.68                                        amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-utopic                      3.16.0.45.36                                        amd64        Generic Linux kernel headers
rc  linux-image-3.13.0-53-generic                         3.13.0-53.89                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-55-generic                         3.13.0-55.94                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-57-generic                         3.13.0-57.95                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-58-generic                         3.13.0-58.97                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-59-generic                         3.13.0-59.98                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-61-generic                         3.13.0-61.100                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-30-generic                         3.16.0-30.40~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-33-generic                         3.16.0-33.44~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-34-generic                         3.16.0-34.47~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-36-generic                         3.16.0-36.48~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-37-generic                         3.16.0-37.51~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-38-generic                         3.16.0-38.52~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-41-generic                         3.16.0-41.57~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-43-generic                         3.16.0-43.58~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-44-generic                         3.16.0-44.59~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-45-generic                         3.16.0-45.60~14.04.1                                amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-53-generic                   3.13.0-53.89                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-58-generic                   3.13.0-58.97                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-59-generic                   3.13.0-59.98                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-30-generic                   3.16.0-30.40~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-33-generic                   3.16.0-33.44~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-34-generic                   3.16.0-34.47~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-36-generic                   3.16.0-36.48~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-37-generic                   3.16.0-37.51~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-38-generic                   3.16.0-38.52~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-41-generic                   3.16.0-41.57~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-43-generic                   3.16.0-43.58~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-44-generic                   3.16.0-44.59~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-45-generic                   3.16.0-45.60~14.04.1                                amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-utopic                        3.16.0.45.36                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-61.100                                       amd64        Linux Kernel Headers for development
ii  linux-libc-dev-arm64-cross                            3.13.0-12.32cross0.10                               all          Linux Kernel Headers for development (for cross-compiling)
ii  linux-libc-dev-armel-cross                            3.13.0-12.32cross1.104                              all          Linux Kernel Headers for development (for cross-compiling)
ii  linux-libc-dev-armhf-cross                            3.13.0-12.32cross1.104                              all          Linux Kernel Headers for development (for cross-compiling)
ii  linux-libc-dev-powerpc-cross                          3.13.0-13.33cross1.1                                all          Linux Kernel Headers for development (for cross-compiling)
ii  linux-libc-dev-ppc64el-cross                          3.13.0-13.33cross0.2                                all          Linux Kernel Headers for development (for cross-compiling)
ii  linux-signed-generic                                  3.13.0.61.68                                        amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-3.13.0-61-generic                  3.13.0-61.100                                       amd64        Signed kernel image generic
ii  linux-signed-image-generic                            3.13.0.61.68                                        amd64        Signed Generic Linux kernel image
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

```
ld@Solsum:~/$ ls -al /boot
total 184285
drwxr-xr-x  5 root root     4096 Aug  2 04:53 .
drwxr-xr-x 25 root root     4096 Aug  2 04:59 ..
-rw-r--r--  1 root root  1164806 Jun 17 21:03 abi-3.13.0-55-generic
-rw-r--r--  1 root root  1165129 Jul 29 08:35 abi-3.13.0-61-generic
-rw-r--r--  1 root root  1207327 Apr 10 14:48 abi-3.16.0-34-generic
-rw-r--r--  1 root root  1206938 May  6 12:22 abi-3.16.0-37-generic
-rw-r--r--  1 root root  1207366 Jun 18 15:02 abi-3.16.0-41-generic
-rw-r--r--  1 root root  1207297 Jul 24 19:24 abi-3.16.0-45-generic
-rw-r--r--  1 root root   165762 Jun 17 21:03 config-3.13.0-55-generic
-rw-r--r--  1 root root   165763 Jul 29 08:35 config-3.13.0-61-generic
-rw-r--r--  1 root root   171827 Apr 10 14:48 config-3.16.0-34-generic
-rw-r--r--  1 root root   171816 May  6 12:22 config-3.16.0-37-generic
-rw-r--r--  1 root root   171817 Jun 18 15:02 config-3.16.0-41-generic
-rw-r--r--  1 root root   171813 Jul 24 19:24 config-3.16.0-45-generic
drwxr-xr-x  4 root root     1024 Dec 31  1969 efi
drwxr-xr-x  5 root root     4096 Aug  2 04:53 grub
drwxr-xr-x  6 root root     4096 Jun  3 08:47 grub.bak
-rw-r--r--  1 root root 19210535 Jun 27 02:41 initrd.img-3.13.0-55-generic
-rw-r--r--  1 root root 19215673 Aug  1 23:29 initrd.img-3.13.0-61-generic
-rw-r--r--  1 root root 19439473 Apr 14 03:13 initrd.img-3.16.0-34-generic
-rw-r--r--  1 root root 19441050 May  7 00:47 initrd.img-3.16.0-37-generic
-rw-r--r--  1 root root 19441196 Jun 27 02:42 initrd.img-3.16.0-41-generic
-rw-r--r--  1 root root 19446202 Aug  1 23:40 initrd.img-3.16.0-45-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3390881 Jun 17 21:03 System.map-3.13.0-55-generic
-rw-------  1 root root  3391819 Jul 29 08:35 System.map-3.13.0-61-generic
-rw-------  1 root root  3512405 Apr 10 14:48 System.map-3.16.0-34-generic
-rw-------  1 root root  3512899 May  6 12:22 System.map-3.16.0-37-generic
-rw-------  1 root root  3514712 Jun 18 15:02 System.map-3.16.0-41-generic
-rw-------  1 root root  3515045 Jul 24 19:24 System.map-3.16.0-45-generic
-rw-------  1 root root  5821984 Jun 17 21:03 vmlinuz-3.13.0-55-generic
-rw-------  1 root root  5822208 Jul 29 08:35 vmlinuz-3.13.0-61-generic
-rw-------  1 root root  5824120 Aug  1 23:29 vmlinuz-3.13.0-61-generic.efi.signed
-rw-------  1 root root  6350864 Apr 10 14:48 vmlinuz-3.16.0-34-generic
-rw-------  1 root root  6352688 May  6 12:22 vmlinuz-3.16.0-37-generic
-rw-------  1 root root  6353360 Jun 18 15:02 vmlinuz-3.16.0-41-generic
-rw-------  1 root root  6357520 Jul 24 19:24 vmlinuz-3.16.0-45-generic

```

EDIT 2

Holy Moley! I got my Windows 7 drive to mount! I used "sudo mount /dev/sdb3 /mnt" and now I can see my Windows 7 drive in /mnt! I'm going to save my stuff now! xD

---

### Post by Bashing-om on 2015-08-02
Lightning Dragon; Wow


Looky looky what I found, the proper way to remove unwanted entries !
see:
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)

Boot the liveUSB, install as per directions, run the toll, and now
reboot into the install and see what we now have:
```

df -h

```

[INDENT][INDENT]progress made
[INDENT][INDENT][INDENT]slowly ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Lightning Dragon on 2015-08-02
> **Bashing-om said:**
> Lightning Dragon; Wow


Looky looky what I found, the proper way to remove unwanted entries !
see:
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)

Boot the liveUSB, install as per directions, run the toll, and now
reboot into the install and see what we now have:
```

df -h

```
[INDENT][INDENT]progress made[INDENT][INDENT][INDENT]slowly ?
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Thank you! Less clutter is a wonderful thing. :guitar:

Oh, I edited my post. I got Windows 7 to mount and now I am copying files. I will boot into LiveUSB (gotta reburn it because it broke) and do the directions once my backups have finished. :) I'm then gonna try to mount my Win10 to make backups...here's hoping!

---

### Post by Bashing-om on 2015-08-02
Lightning Dragon; K

Then after the backups are made we see what we can do about removing all those old kernel images.
I am done for this session, and I have a rather full day tomorrow, so will be in my afternoon -long about 10:00 GMT - before I can get back on here .

[INDENT][INDENT]hard work pays better than
[INDENT][INDENT][INDENT]good luck
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Lightning Dragon on 2015-08-02
> **Bashing-om said:**
> Lightning Dragon; K

Then after the backups are made we see what we can do about removing all those old kernel images.
I am done for this session, and I have a rather full day tomorrow, so will be in my afternoon -long about 10:00 GMT - before I can get back on here .[INDENT][INDENT]hard work pays better than[INDENT][INDENT][INDENT]good luck
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]



Sure, *whenever* you can help, don't feel the need to be rushed on account me. I do appreciate what you have done so far, though. :)

**EDIT 1**

Well, I started with cleaning out the system. Not sure which to delete though.

```
ld@Solsum:~$ sudo efibootmgr
BootCurrent: 0006
Timeout: 1 seconds
BootOrder: 0006,0005,0008,0002,0009,000E,0001,0003
Boot0001* Hard Drive 
Boot0002* Windows Boot Manager
Boot0003* UEFI: Built-in EFI Shell 
Boot0005* Windows Boot Manager
Boot0006* ubuntu
Boot0008* ubuntu
Boot0009* UEFI OS
Boot000E* Windows Boot Manager

```

Oh, and how I got into my Windows 10 drive even though it was in Hibernation, I used the following:

```
sudo ntfsfix /dev/sdXY
```

In my case, it was "/dev/sdc4" and it allowed me into the drive.

**EDIT 2**

Okay, I have finished backing up what I wanted/needed. Thank God! I have come to the conclusion that I really would just like to reinstall *everything*, as I very much doubt we will be able to fix Windows 7 and 10. I know that Ubuntu is recoverable and that we would definitely do it (or rather...you xD) but I think it could be cleaner and easier to do a fresh install for all my OSes on separate drives. So my question next is: Do you have a comprehensive guide I could read on how to dual (triple) boot my OSes all on different drives? It seems like I had no idea how to do it in the first place so it put the installation all over the place.

Thank you again! I wouldn't have been able to recover my precious files without you. :)

---

### Post by Bashing-om on 2015-08-03
Lightning Dragon; Sure !

I also am a firm believer in fresh clean installs in the case of multiple problems at the system levels. It is much faster to just (RE-)install [ubuntu, that is ] and go on !

I too multi boot - ubuntu's ! - ( for testing and awareness) Arranging the boot code for a particular use case is an art in and of it's self. I highly recommend Windows on it's own hard drive with it's boot code installed to that hard drive.
Ubunt(s) installed to it's own hard drive, with ubuntu's grub installed to that hard drive, and with grub chainload Windows .
Be advised, there can be ONLY one bootloader installed per hard drive that controls booting. Windows will not talk to ubuntu. Now if you are going to have more than one linux system installed on the same hard drive, I do suggest that grub's chainloader mechanism be disabled in all subsequent secondary linux installs. In this arrangement, no matter what happens to the linux boot code, by changing the boot priority in bios to the Windows hard drive, one can still boot Windows.

Partitioning schemes will vary depending on the individual use case. Not a thing wrong with the starting point to just dual boot up with the "install alongside" option and let the install wizard make all the decisions. Once you have an idea of what the actual use case is, then one re-partitions to suit. 

[INDENT][INDENT][INDENT]just my thoughts
[/INDENT][/INDENT][/INDENT]

---

### Post by Lightning Dragon on 2015-08-03
> **Bashing-om said:**
> Lightning Dragon; Sure !

I also am a firm believer in fresh clean installs in the case of multiple problems at the system levels. It is much faster to just (RE-)install [ubuntu, that is ] and go on !

I too multi boot - ubuntu's ! - ( for testing and awareness) Arranging the boot code for a particular use case is an art in and of it's self. I highly recommend Windows on it's own hard drive with it's boot code installed to that hard drive.
Ubunt(s) installed to it's own hard drive, with ubuntu's grub installed to that hard drive, and with grub chainload Windows .
Be advised, there can be ONLY one bootloader installed per hard drive that controls booting. Windows will not talk to ubuntu. Now if you are going to have more than one linux system installed on the same hard drive, I do suggest that grub's chainloader mechanism be disabled in all subsequent secondary linux installs. In this arrangement, no matter what happens to the linux boot code, by changing the boot priority in bios to the Windows hard drive, one can still boot Windows.

Partitioning schemes will vary depending on the individual use case. Not a thing wrong with the starting point to just dual boot up with the "install alongside" option and let the install wizard make all the decisions. Once you have an idea of what the actual use case is, then one re-partitions to suit. [INDENT][INDENT][INDENT]just my thoughts
[/INDENT]
[/INDENT]
[/INDENT]


Thanks for the reply!

Yes, I intend to keep each OS on its own drive. I will start with Windows 7 and then Windows 10, and then Ubuntu (I don't intend to install multiple Linux OSes on one drive). I'm not sure of the actual process to make sure I don't screw it up again though. How do I make sure the boot code (?) gets installed on Windows' drive and the grub etc? Is there a video or graphical guide I can follow? The reason is I'm not sure how large I should make my / and /home partitions as well as swap. I do intend to install a *lot* of stuff on Ubuntu, but I also don't want to lose too much saving space for /home as I tend to download lots of images or save lots of documents etc.

---

### Post by Bashing-om on 2015-08-03
Lightning Dragon; Hey;

Two words -> "data partition" "symbolic link". You will be impressed with what you can manage. But again, it is your particular use case that is the determining factor on the size of the partitions - only you can know how much data will be wrote to the file system and where .
Only time and use will tell .

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Lightning Dragon on 2015-08-03
> **Bashing-om said:**
> Lightning Dragon; Hey;

Two words -> "data partition" "symbolic link". You will be impressed with what you can manage. But again, it is your particular use case that is the determining factor on the size of the partitions - only you can know how much data will be wrote to the file system and where .
Only time and use will tell .
[INDENT][INDENT]it's 'buntu[INDENT][INDENT][INDENT]you can have it your way
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Alright then, thank you! I guess I just gotta deal out the amount and just go with it. At least as far as I know it is possible to repartition later if I need more space so I won't be screwed anyways. haha

What should I do to ensure that I get a Grub menu to select the OSes from upon install? My normal method before was installing and then using Boot-Repair but that's what got me the multiple entries and log files. :lol:

Thank you again for the help! :)

---

### Post by Bashing-om on 2015-08-03
Lightning Dragon; Well ..

Honestly, it has been ages since I did an install in anything other than "something else" and manually set up my partitions. I usually have set up my partitions in 'gparted' prior to the install. I do think that in installing using the default " install along side" that the wizard defaults to installing the boot code to the 1st device ( what ever is discovered as that 1st device) . In 'something else', you have the option of where to install grub.

Like in anything, once you depart from a wizard there is a learning curve. Do not be afraid to mess up. One can always wipe/remove/delete whatever, and start all over again with what you have learned from the failure.

To be on the safe side, one can disconnect the windows' hard drive, and install using a DVD. Then grub has no other option than to install correctly .
As a safety net, one can always use a liveDVD and install grub where ever one wants it .

[INDENT][INDENT]safety is no accident
[/INDENT][/INDENT]

---

### Post by Lightning Dragon on 2015-08-03
> **Bashing-om said:**
> Lightning Dragon; Well ..

Honestly, it has been ages since I did an install in anything other than "something else" and manually set up my partitions. I usually have set up my partitions in 'gparted' prior to the install. I do think that in installing using the default " install along side" that the wizard defaults to installing the boot code to the 1st device ( what ever is discovered as that 1st device) . In 'something else', you have the option of where to install grub.

Like in anything, once you depart from a wizard there is a learning curve. Do not be afraid to mess up. One can always wipe/remove/delete whatever, and start all over again with what you have learned from the failure.

To be on the safe side, one can disconnect the windows' hard drive, and install using a DVD. Then grub has no other option than to install correctly .
As a safety net, one can always use a liveDVD and install grub where ever one wants it .[INDENT][INDENT]safety is no accident
[/INDENT]
[/INDENT]


In that case I'll try it manually [following this guide]("https://help.ubuntu.com/community/Grub2/Installing") with my Windows drives plugged in. I'm reinstalling them anyways, so it isn't like I'll lose anything important. :) First step is to completely delete the drives though.

Thank you again! I'll be sure to come back when it is successful and explain what I did just in case another person finds this thread and needs help! :razz:

EDIT

If anyone is reading this...I want to give you a warning: [COLOR=#ff0000][SIZE=1]DO NOT USE WINUSB ON UBUNTU! IF IT FREEZES AND YOU FORCE QUIT IT YOU WILL BREAK YOUR USB[/SIZE][/COLOR]. I thought it was just coincedence but I have two more USBs and I tried it on each. Froze each time and then now they are recongizable, unformattable and just complete paperweight. I killed a 16gb Toshiha and two Kingston 8gbs and 1 16gb Kingston. But if you do not believe me...fine. Try it. Just don't say you weren't warned!

EDIT 2

I decided to just take the risk. I made my swap the same as my ram (8gb) and am installing now. Will report back success/failure! 
EDIT 3

Failure.

Nothing is working right. I decided to reinstall again and now I have a fresh install of Windows 7. I didn't get a chance to format it or anything, so it is currently NTFS and when I click properties on the drive, it reports it as MBR. How do I proceed to install Ubuntu now? I'm really lost. I've tried two different methods and the grub menu gets borked, making Windows unable to be logged into because the USB ports stop working.

I have my BIOS set to "Legacy+UEFI" (No "UEFI" option) and then I boot my DVD from the UEFI DVD Drive, and begin installing. But then it complains that my Windows drive has information of GPT but not a valid fake mdos so it makes my drive appear empty. :(

---

### Post by Lightning Dragon on 2015-08-04
UPDATE!

I love Ubuntu so much! Whereas Windows will tear you down and 90% of the time refuse to help you up, Ubuntu will always help you!

Okay, so the previous problems I had? I think everything was related to my BIOS! I had multiple entries everywhere and finally, after googling and googling (and pulling out my hair) as to why Windows 7 USB ports stop working after installing Ubuntu, I loaded default values in my BIOS (by pressing F6 *will be different for others*) and then I rebooted and I got the grub screen. But I was still unsure it fixed my issue...until Windows 7 loaded and the lights on my keyboard went on! Success!

So here's what I tried prior ro resetting my BIOS to default settings:

[LIST=1]
[*]I dug through my BIOS for anything in relation to IOMMU, USB Legacy, xCHI settings and UEFI settings as well as turning on and off (again and again) Win8 features. (I did not have to turn off the Intel Smart thing) 
[*]I tried loading Windows through UEFI and standard (the one without UEFI in the title) but nope, nothing. 
[*]I tried installing Windows, disconnecting that drive and installing Ubuntu on the 2nd drive, reconnect and repair if necessary with Boot-Repair. Nope. A massive failure. Same problem. 
[*]I tried installing Ubuntu first, but nope. Same problem. 
[*]I even tried different keyboards and mice, and different USB ports. But nope! 
[*] 
[/LIST]
[CENTER][COLOR=#ff0000][SIZE=5]Let me start from the begining though! [/SIZE][/COLOR]
_[COLOR=#ff0000]*the above will not work for you if you do it out of order*[/COLOR]_
[/CENTER]

So I was about to give up. 

I installed Windows 7 again, because it got borked the last time. Once it finished and I let some drivers install by itself (note: my keyboard and mouse drivers never seemed to install so that isn't the fix), I rebooted with my UbuntuLiveDVD. I started up the installer and saw that my Windows drive came up empty. Curious, I went into the testing environment. I opened Gparted to see what it was going on. Upon scanning, it gave me a gpt warning, stating that it found some bits of gpt but the rest was mdos. Here is the actual error report when opening Gparted:

> /dev/sdb contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?

This got me googling again, because I believed this was far more serious than it appeared and I didn't want to erase the fourth Windows 7 install I did tonight.

That's when I got pretty frustrated as it is 4:31AM here and google gave me nothing. But then I come across two golden piles of beautiful information on "askubuntu". Those links:

[http://askubuntu.com/questions/249642/gpt-partition-table-warning-message-during-install-of-ubuntu](http://askubuntu.com/questions/249642/gpt-partition-table-warning-message-during-install-of-ubuntu)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-startup-boot-option)

The first linked helped me get rid of that pesky GPT error/warning! The instructions I followed that worked like a charm:

> 
  NO NEED FOR A EMERGENCY DISK!!
  Simply boot with ubuntu live CD or USB (I did with USB).
  Then open the Terminal. Type: sudo gdisk (hit enter) Type: /dev/sda (change /dev/sda to whatever is appropriate to access your hard disk, if necessary). Then you will probably see that there are MBR and GPT. **Tell the computer you want to use the MBR (by pressing 1)** Then: At the Command prompt, type x to enter the experts' menu. At the Expert command prompt, type z to "zap" (destroy) the GPT data. Type y in response to the confirmation about destroying the GPT. Type n in response to the query about blanking the MBR. [COLOR=#ff0000]**Caution: If you answer y here, you'll destroy your Windows partition(s)!**[/COLOR]

     



After that, I reloaded Gparted and my WIndows drive appeared! Wahoo! So next I went into the installer to start the process. Next I followed LINK 2, particularly everything after "**Easiest one" **but stopped at **"Another Way"**. That is to say, I followed this:

> **Easiest one**
  
[LIST]
[*]Create a partition on 2nd disk. 
[*]Install ubuntu on that parition & install GRUB on 2nd disk's  mbr not on first disk's mbr. Be careful here. See below image (just for  demo purpose), you need to do everything in **(probably) sdb**. 
[*]You select your **already created sdb partition**, edit, assign mount point /, and file system type ext4 
[*]Select boot loader location as sdb , not sda (see red colored section)
[IMG]http://i.stack.imgur.com/we9t2.png[/IMG]
[LIST]
[*]Once done, reboot and you will be booted to windows 7. 
[/LIST]
  It happens because, your **boot disk priority says to boot from first harddisk** (Where we didn't change anything).
  So open BIOS, **change boot disk priority so that the disk containg ubuntu comes first.** 
[*]This time, GRUB will be loaded. And you can boot either OS. 
[*]Remove the disk, windows 7 will boot directly. 
[*]Again plugin the 2nd disk, verify boot order from BIOS so that 2nd disk comes first. You can now boot any OS again. 
[/LIST]


**Some notes:** For me, my Ubuntu drive was *sda* and I placed the boot loader on *sda*, not *sdaXY *where I made the partition for Ubuntu. Before I made the partition for Ubuntu, I made a swap area at _***4000***_ as trying to go forward without it resulted in a warning. So once that was done, I made my partition for Ubuntu, giving it all of the space leftover. I made sure boot loader was selected on* /dev/sda*, not */dev/sdaXY* or */dev/sdb* or */dev/sdaXY*, as the later was my Windows drive (I'm being detailed for newbies, not you awesome experts ;) ). I pressed the glorious ***Install Now*** button and waited for it to finish.

I rebooted. It loaded into Windows like the above said it would. However...to my horror I still had the keyboard/mouse/usb problem. That's when I did the above, messing around in my BIOS again until I finally RESET TO DEFAULT with F6. I rebooted after taking screenshots of my CPU overclock (because loading my OC profile brough the BIOS all back to the problem; skip this if you don't OC) and I got the beautiful Grub menu!

I haven't seen the menu look like this before. It fit my resolution size perfectly (1920x1080), the font was clear and crisp and I had my entries for Windows and Ubuntu. (Even better upon boot my internet loaded instantly, instead of taking 10 seconds exactly to load, and I also didn't have that stupid "VOLUME IS FULL" problem) So wondering if it did the job, I selected WIndows 7 to see if the keyboard would work.

It did! :guitar:

So this is my story of my first successful install of Ubuntu without thousands of entries, boot-repair or any clutter. I now have my system up again! For any newbies out there experiancing my problems and see this, I hope it helps. If you need help with something I said or did, message me, I will always answer.

To @Bashing-om: Thank you for everything! Without you I would have lost everything I had! Thank you so very much! :D

[CENTER][I](now I just have to install Windows 10! Hopefully that will be just as easy!)

EDIT

[/I][COLOR=#ff0000]After installing my second Windows 7 (meant for upgrade to 10) I found it was the only one that didn't allow USB ports to work,  but Ubuntu and my first Win7 install did. I then turned off my PC, unplugged my USB and mouse, pressed the CMOS button on my board (others might not have this; in that case, remove the CMOS battery), flipped the switch to the PSU and then held my power button down for ten seconds with everything off. Next I flipped the switch on my PSU back on, got a backup keyboard (a generic HP or Acer will do; you can try without this part) and plugged that into my front port, 2.0. Next I powered on my system and saw the Setup screen, a black screen with white text. I pressed F1 to initiate the setup and it took me into my BIOS. I made sure Win8 features were off and then saved and rebooted. I was brought to my grub....BUT WAIT. Look at your generic keyboard and make sure that NUM LOCK is not on (led must be off). Then I selected the OS in question that had the problem and loaded in. I watched my LEDs to make sure NUM LOCK remained off until I got to the log in screen. Now your generic keyboard may or may not work here (mine did but only when NUM LOCK was ON) but this is when I plugged in my good keyboard (Cooler Master Storm Devastator Comb) into the back of my PC and it immediately started working! Yay! Once I was in the OS, I made sure to install every single driver my motherboard needed, included the Intel 3.0 USB driver.

So....hopefully all of my post will help someone with the same problem! Good luck![/COLOR]
[COLOR=#008000]Successfully triple booting now![/COLOR]
[/CENTER]

---

