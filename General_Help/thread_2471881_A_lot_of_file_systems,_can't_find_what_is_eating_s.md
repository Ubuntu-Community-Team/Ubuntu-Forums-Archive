---
title: "A lot of file systems, can't find what is eating space"
date: 2022-02-11
forum: General Help
---

### Post by ihorr on 2022-02-11
Hi, I'm new here, just looking for some help in investigation of where is all my space disappeared. ):P

udev             32G     0   32G   0% /dev
tmpfs           6.3G  1.9M  6.3G   1% /run
/dev/sda2        64G   61G     0 100% /
tmpfs            32G     0   32G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs            32G     0   32G   0% /sys/fs/cgroup
/dev/loop0       56M   56M     0 100% /snap/core18/2253
/dev/loop2       62M   62M     0 100% /snap/core20/1328
/dev/loop1       56M   56M     0 100% /snap/core18/2284
/dev/loop3       68M   68M     0 100% /snap/lxd/21835
/dev/loop4       44M   44M     0 100% /snap/snapd/14295
/dev/loop5       44M   44M     0 100% /snap/snapd/14549
/dev/loop6       62M   62M     0 100% /snap/core20/1270
/dev/loop7       68M   68M     0 100% /snap/lxd/21803
tmpfs           6.3G     0  6.3G   0% /run/user/1000

Why there is so messy here, I can't install any major package under /home directory!? And how can I "clean up a little bit"? What does all this snap mean? Thanks a lot, really need you right now

---

### Post by TheFu on 2022-02-11
Please run these 2 commands and post the output wrapped in code tags.  Code tags are very important, so the columns line up correctly.
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```
and
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

Those commands remove all the junk and some very important information that is needed. Different file systems have different tools, so we need to see which are being used.  Facts are the best way.  With those facts, we can suggest other tools to locate where the space is being used.

Code-tags how-to: [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)

>  Why there is so messy here, I can't install any major package under /home directory!? And how can I "clean up a little bit"? What does all this snap mean? Thanks a lot, really need you right now 
In Linux, packages aren't installed to an individual's HOME. If you want to do that, then first, you'll need a separate storage mount for /home/. I'm not seeing that in the provided output, so everything in /home is shared with everything in /var, /usr and everything else on the system.

Snap packages are a huge topic. I'd encourage you to learn about those and come to your own conclusions. There are 20+ threads here about snap packages with multiple arguments for and against them. Let your feeling on snap packages be known. Use the Ubuntu Discord channel. That's where the developers hang out, not here.

---

### Post by GhX6GZMB on 2022-02-11
Cr*p - sorry, snap is messy. It's not very easy to analyze all the "loops". "Snap" is the new installation regime in Ubuntu. It's there to ease the life of developers and Canonical to get into the smartphone market. It's in no way helpful to normal users (quite the opposite), but who cares?
Cr*p (sorry, Snap) has added yet another abstraction layer on top of what's already ihere, making it even more difficult to interact with your own hardware/software.

My suggestuion is a reinstall, with program installation using only PPAs.

---

### Post by grahammechanical on 2022-02-11
If you use to file manager to open /dev you will see files there for loop0, loop1 and so on. Look at the properties of these files and you will find that they are bloc devices with a file size of zero bytes.

The actual snap applications that were installed by default (snapd for example) and those installed by you (lxd for example) do have files sizes of many bytes and are taking up space in your hard drive. LXD is 80 MB,

Regards

---

### Post by Holger_Gehrke on 2022-02-11
snap is a new(-ish) package format. A snap packs everything a program needs into one file - a file system image stored as a compressed squashfs. This means installed snaps are mounted through a loop back device. It also means snaps are **big**. To bring the size down a bit there are snaps used as dependencies for other snaps to use (the various core?? snaps in your list; there are also snaps of various versions of Gnome and KDE).

The various tmpfs file systems in the list are basically dynamic RAM-disks. The capacity given for them is the size they can maximally grow to, but they only use as much RAM as is needed to store whatever is in them.

udev is not a real file system either, it's a pseudo file system in which the device files 'live'.

The only real file system in your list is /dev/sda2 which is mounted as / (the root file system) and that is almost full - you've used 61 GB of 64 GB and should have some serious trouble up to the point where the system can't boot because it can't write to it's logs.

In your situation (/home/ not mounted from a separate file system) installing programs into $HOME would not be helpful ... Also programs installed through the package manager are meant to be used by all users of the system and are therefore installed into fixed well-known directories (search for Linux Filesystem Hierachie Standard to find out what they are and how this is meant to work ...).

To find what is using up your disk```
du -x -h --max-depth=1 /
```might be helpful. (du=Disk used, -x do not cross into other file systems, -h human readable sizes (rounded and with units instead of giving the precise number of bytes, --max-depth=1 list one level of the directory hierarchy). Find the big directories with that and dig down by repeating the command replacing the path to a directory for '/'.

Holger

---

### Post by ihorr on 2022-02-13
```
@01:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda2      ext4   64G   61G     0 100% /
```

```
@01:~$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME    SIZE TYPE FSTYPE MOUNTPOINT
sda    74.5G disk
&#9500;&#9472;sda1    1M part
&#9500;&#9472;sda2 65.5G part ext4   /
&#9492;&#9472;sda3    9G part swap   [SWAP]

```

```
@01:~$ sudo du -x -h --max-depth=1 /
[sudo] password for miner:
7.5M    /etc
302M    /home
27M     /miners
4.0K    /srv
16K     /lost+found
48G     /root
2.1G    /var
28K     /snap
64K     /tmp
4.0K    /opt
302M    /boot
4.0K    /mnt
4.0K    /cdrom
4.0K    /media
3.0G    /usr
61G     /

```

---

### Post by Holger_Gehrke on 2022-02-13
48 Gigabyte in /root ? That's the home directory for the administrative user - who on a standard Ubuntu can't even log in, you temporarily assume root's abilities by using sudo or pkexec - and should normally be almost empty. If I were you I'd take a closer look at that.

Holger

---

### Post by MAFoElffen on 2022-02-13
> **Holger_Gehrke said:**
> 48 Gigabyte in /root ? That's the home directory for the administrative user - who on a standard Ubuntu can't even log in, you temporarily assume root's abilities by using sudo or pkexec - and should normally be almost empty. If I were you I'd take a closer look at that.

Holger

Agreed... The laptop I'm posting this from is my daily that I've used almost constantly, day to day, for over a year, doing some crazy stuff that would make most cringe, and the total size of the '/root' directory on it is 648K...

---

### Post by ihorr on 2022-02-13
How to make just / and swap (/ shared for every directory), and not to reinstalling the system itself?

---

### Post by ihorr on 2022-02-13
From which record did you understand that?

---

### Post by TheFu on 2022-02-13
> **ihorr said:**
> How to make just / and swap (/ shared for every directory), and not to reinstalling the system itself?

Not sure I understand the question.  swap is a different file system than /.  / is ext4.
The files in /root/ are very likely the problem and really there should be almost nothing in /root/.  For 99.9999% of users, those files can be deleted.

Like some others, I use to old information about the system which will be included in my backups.  Things like the disk layout, partition tables, lists of installed packages.  That is mostly text information needed to restore the system should something bad happen.  Even with all that information, it uses just 11MB.

Clean up your /root/ and the problems will go away.

I think your swap is too large. Do you hibernate and have 8GB of RAM?  If not, then it definitely is too large. For all desktops, I make swap 4.1GB.  swap can be a created in many different ways. In your installation, it is a 9G partition - sda3.  To make is smaller, here are the overview steps (I might forget some details):
[LIST=1]
[*]turn the swap off. Cannot modify it if it is being used by the system. **swapoff** is the command, I don't know the options.
[*]Using any partition tool (I like gparted), delete the existing swap partition.
[*]Recreate a new swap partition, placed to the "far right" and sized at 4.1GB. Empty space needs to be next to the / partition, sda2. Actually, that empty space needs to be to the right-side in the Gparted GUI.
[*]At the same time you create the new partition, choose linux-swap as the file system type.
[*]edit the /etc/fstab (use **sudoedit**) and replace the UUID from the old swap partition (there is a line in there just for swap) with the new UUID.  **lsblk -e 7 -o name,size,type,fstype,mountpoint,[COLOR="#FF0000"]uuid[/COLOR]** will show it. There are other commands to see the UUID too. Only the UUID should need to be changed.
[*]turn on the swap using the **swapon** command.
[/LIST]

That's all you can do while running the OS.  You'll need to boot from alternate media - i.e. a Try Ubuntu flash drive to modify sda2.  To add the ~ 5GB storage that we freed from the swap above to /, we need to resize that partition. In gparted, right click on the line with sda2 and choose **resize** ... then drag the right-hand side of the graphical view to the right until it won't go any farther.  The numbers in the "empty sectors AFTER" should be 0.

All of this only adds 5G.  You'll need to delete all the junk in /root/ or move it to a different storage device. If you just did that, it will have more impact on your system than resizing the swap.

---

### Post by TheFu on 2022-02-13
> **ihorr said:**
> From which record did you understand that?

Who?  What?  If you don't quote the person your reply is aimed at, we don't have enough context to understand questions like this.

First, thanks for posting the command output. From that over, we know you are using a fairly standard setup with / using ext4 and a separate swap using 9GB.  The disk isn't all that big, but if you don't keep junk, you can run for years in a system with 64GB of storage.  I do. My desktop has 40GB, but I keep all the junk on network storage, not on my desktop.

Because the system has just 1 file system for programs and data, and that is ext4 (not ZFS or BTRFS), we can use normal storage/space commands to find where all the space is being used.

The **du** output shows that /root/ is using 48GB of storage. This is very odd.

When hunting I like to have the computer sort the output by size, so I'd use a command like this:
```
$ sudo du -sh /* | sort -h
```
That command puts the directories with the largest storage at the bottom of the list. Usually, fewer than 5 directories user more than 1GB of space.  On my desktop, this is the last 6 lines:
```
9.9[COLOR="#00FF00"]M[/COLOR]    /root
19[COLOR="#00FF00"]M[/COLOR]     /etc
219[COLOR="#00FF00"]M[/COLOR]    /boot
3.9G    /snap
5.3G    /var
7.3G    /usr
7.6[COLOR="#FF0000"]G[/COLOR]    /home
```
See how it is sorted?
There are lots of other directories above these, but they use just a few KBs. If I were running out of space, I'd start from the largest directory to see what can be removed. See how my /root uses just 10MB?  How much does yours use?
We can sort yours quickly because you posted text - thanks for that.
```
$ sort -h /tmp/t 
4.0K    /cdrom
4.0K    /media
4.0K    /mnt
4.0K    /opt
4.0K    /srv
16K     /lost+found
28K     /snap
64K     /tmp
7.5M    /etc
27M     /miners
302M    /boot
302M    /home
2.1G    /var
3.0G    /usr
[COLOR="#FF0000"]**48G**     /root
[/COLOR]61G     /
```
It is probably a bad idea to run programs as root that use so much data.

---

### Post by ihorr on 2022-02-13
```
root@01:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
udev             32G     0   32G   0% /dev
tmpfs           6.3G  1.9M  6.3G   1% /run
/dev/sda2        64G   17G   44G  28% /
tmpfs            32G     0   32G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs            32G     0   32G   0% /sys/fs/cgroup
tmpfs           6.3G     0  6.3G   0% /run/user/1000
root@01:~#
```
I've cleared all this **** from /root, but still can't understand why there is 17G of occupied space. Is there any cli graph tool that will "show me" in some kind of "cubes" that will represent the relativity of files?

---

### Post by ihorr on 2022-02-13
Also, I've deleted the swap as was mentioned in thread, anyway I don't know when the system using it. Next, how can I extend the fs by this unpartitioned space ??? 

```
Command (m for help): F
Unpartitioned space /dev/sda: 9 GiB, 9663749632 bytes, 18874511 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes


    Start       End  Sectors Size
137426944 156301454 18874511   9G
```

---

### Post by linux-sysop on 2022-02-13
Try** du | sort -n** from the home; It will sort all the largest to the bottom.
The bottom of my home for example is this...

```
29332    ./.config/vivaldi/Default/Service Worker/CacheStorage/379f1cbab5b08b6fc9e08681e42d8be311441c88/d016318b-887a-4078-93cb-fabe96ef6441
29340    ./.config/vivaldi/Default/Service Worker/CacheStorage/379f1cbab5b08b6fc9e08681e42d8be311441c88
31296    ./.cache/nvidia/GLCache
31300    ./.cache/nvidia
56528    ./.cache/mozilla/firefox/oxecj4uh.default-release/cache2/entries
56584    ./.cache/mozilla/firefox/oxecj4uh.default-release/cache2
58164    ./.config/vivaldi/Default/Service Worker/CacheStorage
61288    ./.config/vivaldi/Default/Service Worker
90700    ./.cache/mozilla/firefox/oxecj4uh.default-release
90708    ./.cache/mozilla/firefox
90712    ./.cache/mozilla
101064    ./.config/vivaldi/Default
165672    ./.config/vivaldi
169300    ./.config
326564    ./.cache/vivaldi/Default/Code Cache/js
326584    ./.cache/vivaldi/Default/Code Cache
338592    ./.cache/vivaldi/Default/Cache
665236    ./.cache/vivaldi/Default
665240    ./.cache/vivaldi
816928    ./.cache

```

This is normal for web browsers to have the largest cache folders, they load up faster this way.  The other item is my Nvidia GPU OpenGL cache. The dot in front of the folder means it is hidden in my home folder.  Also I don't bother listing the floor space on SSD as human readable when sorting.

---

### Post by TheFu on 2022-02-13
Deleting all swap is usually a very bad idea. There are some performance tuning things that require some swap, even 1G is sufficient.
I've explained how to expand storage above already.

There are some GUI tools that do stuff. I don't use them, so I don't know the name. Check the alternativeTo.net website for options.

---

