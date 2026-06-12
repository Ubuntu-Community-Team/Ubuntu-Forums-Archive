---
title: "Need Help Mounting a Partition"
date: 2022-09-09
forum: General Help
---

### Post by Quarkrad on 2022-09-09
I have **/** on dev/nvme0np2 and other directories like **/home** **/media/etc..** on other physical media and partitions.  I'm getting the FileSystem root massage having 0 bytes remaining message.  I would like to use Disk Analyser to see where the issue is (probably var) but / looks at everything that is physically spread across a number of physical drives. From what I've read it looks like I could mount dev/nvme0np2 on a new folder and then use other tools (terminal or Disk Analyser) to look at the contents of that folder.  Is it as simple as something like:

sudo mkdir /home/dad/tmp
sudo mount dev/nvme0np2 /home/dad/tmp

and then when finished

sudo rm -d /home/dad/tmp?

---

### Post by TheFu on 2022-09-09
du can be used with an option to not cross file systems. The option is in the manpages. I don't remember it.

```
$cd / ;  sudo du --one-file-system -sh * |sort -h |less
...
8.0K    media
8.0K    mnt
12K     Data
16K     lost+found
72K     snap
128K    tmp
272K    opt
1.2M    run
9.9M    root
19M     etc
213M    boot
4.6G    var
7.3G    usr
11G     home
```
is very useful. Human readable, sorted, output prevents wasting time on unimportant areas.

Of course, df will show the mounted file systems, so you can manually remove du output for file systems you don't care about.

My first look is usually for huge files:
```
$ find . -type f -size +3G -exec ls -lh {} \;
```

Tweak the size lower and lower as you find and deal with larger files.  
/var is 4.6G on that system.  
```
sudo du --one-file-system -sh /var/lib/* |sort -h |less
...
328K    menu-xdg
608K    usbutils
672K    systemd
1.8M    fwupd
3.1M    command-not-found
4.1M    aspell
17M     mlocate
90M     dpkg
196M    apt
2.4G    snapd

```
Ah ... snaps are the problem. Not surprising.  Going down into the snapd/ directory, 
```
2.0M    assertions
97M     seed
1.1G    snaps
1.2G    cache

```
Sorting really helps.  Appears that the extra copies of snaps is the issue.  I really hate the design of snap packages.  So wasteful.
1.2G isn't nothing on a system with 16G total storage.  2.3G is even worse.

---

### Post by Quarkrad on 2022-09-10
I'm sinking with this one.  The output of the command *cd / ;  sudo du --one-file-system -sh * |sort -h |less* is:

```
0       bin
0       dev
0       lib
0       lib32
0       lib64
0       libx32
0       proc
0       sbin
0       sys
4.0K    cdrom
4.0K    mnt
4.0K    srv
16K     lost+found
32K     media
44K     snap
108K    tmp
2.0M    run
27M     root
33M     etc
254M    boot
1004M   opt
3.6G    var
4.2G    swapfile
8.2G    usr
12G     home
~

```

This confuses me in the sense that the 12G **/home** directory is located on /*dev/nmme0n1p3* but the partition which is full is* /dev/nvme0n1p2* where **/** is mounted.  Undoubtedly I'm wrong but I would like to see the contents of */dev/nvme0n1p2* only and be able to drill down and find out why it is full.  Perhaps you cannot do this on Linux or this is the wrong way of looking at it.  I have attached a very poor screen picture of my SSD as I now cannot take a screen shot - perhaps a result of **/** being full

The snap packages on my system is:

```
dad@dadubuntu:~$ snap list
Name                       Version           Rev    Tracking         Publisher      Notes
bare                       1.0               5      latest/stable    canonical&#10003;     base
core20                     20220826          1623   latest/stable    canonical&#10003;     base
gnome-3-38-2004            0+git.891e5bc     115    latest/stable/…  canonical&#10003;     -
gtk-common-themes          0.1-81-g442e511   1535   latest/stable/…  canonical&#10003;     -
snapd                      2.56.2            16292  latest/stable    canonical&#10003;     snapd
snapd-desktop-integration  0.1               14     latest/stable/…  canonical&#10003;     -
software-boutique          0+git.0fdcecc     57     latest/stable/…  flexiondotorg  classic
ubuntu-mate-welcome        22.04.0-5b7bef38  709    latest/stable/…  flexiondotorg  classic

```

Over the years this i the second time I've had this issue - the first time I resolved it my re-installing **/**.  Is there anything I can do to stop **/** growing and growing?  I know using LXD type environments, that can dynamically change partition sizes, is a solution but I've yet attempt such a move.  It seems a pity **/** appears to inherently grow and no matter what size partition you initially allocate it will fill up. 

note:  cannot upload screen shot(?) - apologies

---

### Post by The Cog on 2022-09-10
If you want to use your original suggested trick of mounting the root partition elsewhere as well, I think this should do it:
```
sudo mkdir /tmp/rootbind
sudo mount --bind / /tmp/rootbind
```
ref: [https://superuser.com/questions/358501/mount-linux-drive-in-two-places](https://superuser.com/questions/358501/mount-linux-drive-in-two-places)

---

### Post by mIk3_08 on 2022-09-10
> **Quarkrad said:**
> I have **/** on dev/nvme0np2 and other directories like **/home** **/media/etc..** on other physical media and partitions.  I'm getting the FileSystem root massage having 0 bytes remaining message.  I would like to use Disk Analyser to see where the issue is (probably var) but / looks at everything that is physically spread across a number of physical drives. From what I've read it looks like I could mount dev/nvme0np2 on a new folder and then use other tools (terminal or Disk Analyser) to look at the contents of that folder.  Is it as simple as something like:

sudo mkdir /home/dad/tmp
sudo mount dev/nvme0np2 /home/dad/tmp

and then when finished
sudo rm -d /home/dad/tmp?

If there in nothing important file on the disk space  you can easily do the command belelow:
```
mkfs.ntfs /dev/sdxx
```

And mine works with the following command below: Regards and cheers
```
mkdir /media/Extended
```
```
mount /dev/sdxx /media/Extended
```

---

### Post by Quarkrad on 2022-09-10
Something odd to me.  According to Disks and GParted my /dev/nvme0n1p2 partition in 42GB and 98.9% full (which makes sense re 0 bytes message.  But having mounted / at /tmp/rootbind the properties of rootbind say it is 18.3GB on disk.

---

### Post by Quarkrad on 2022-09-10
OK - I wasn't showing hidden files so I emptied it although there was not much in it.  Somehow all is OK - / is not full and I understand where the 18Gb comes from:

```
dad@dadubuntu:~$ df -h /
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p2   39G   18G   20G  48% /

```

 I will mark as Solved but afraid I cannot help other users as I've gone from 98% full to 48% only by emptying the hidden trash folder that did not contain that much data.  Perhaps re boot helped.

---

### Post by TheFu on 2022-09-10
Did you use the df -Th output to know which file systems should be excluded?
Seems the --one-file-system option isn't working (or more likely the -sh options aren't compatible with it).

Also, because the command is sorted, it really isn't necessary to show all the tiny files/directories. Those just cruft up what's important.

20G is small for 18.04 and later releases.  35G is what I setup.
If you use a swapfile, move that to a swap partition. I don't use swapfiles.
I don't understand the comment about lxd at all.  lxd containers use real storage and are typically placed in /var/.  Because lxd is only available as a snap package (damn you Canonical!!!!), we have very little control.
Did you clean up the wasted snaps, and 3 copies of those?  Snaps refuse to allow fewer than 2 copies.  Also, it is possible to force snap updates to only happen once a week, which should be good for system stability, but not so bad for security updates.
Have you limited the size of system log files yet?  500MB should be enough logs for months. There's no reason to allow more, since when that happens, it is due to a run-away log.  There is a journalctl command to immediately reduce logs retained. There are settings to limit total and individual log file sizes.

---

