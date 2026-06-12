---
title: "/dev/sda2/ is 100% full (root)"
date: 2019-09-26
forum: General Help
---

### Post by prince-korvin on 2019-09-26
Hi guys,

Ubuntu mini (command line only).

One of our guys wanted to copy /Servers/ folder from root directory to his home directory and executed wrong command:
sudo cp -R /Servers/ ~/Servers/

and after few moments got many errors like:
cp: error writing '/root/Servers/Folder/File-104.20190828-File1.txt': No space left on device

The thing is that /Servers/ folder already was in root, but now directory is 100% full and we unable to install anything:

df -h

Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           394M   41M  354M  11% /run
/dev/sda2        20G   20G     0 100% /
tmpfs           2.0G     0  2.0G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/sda3       1.4T  554G  830G  41% /Servers
tmpfs           394M     0  394M   0% /run/user/1007

fdisk -l
Disk /dev/sda: 1.4 TiB, 1532998189056 bytes, 2994137088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000296cd

Device     Boot    Start        End    Sectors  Size Id Type
/dev/sda1           2048    4208639    4206592    2G 82 Linux swap / Solaris
/dev/sda2  *     4208640   46153727   41945088   20G 83 Linux
/dev/sda3       46153728 2994137087 2947983360  1.4T 83 Linux


du -h --max-depth=1 / | grep '[0-9]G\>'
554G    /Servers
16G    /root
1.2G    /usr
1.3G    /lib
574G    /

What actually happened, why we can see that /Servers/ can have up to 1.4Tb and at the same time it is in /root/ which is 100% full? How can we fix this without deleting /Servers/ folder?

---

### Post by HermanAB on 2019-09-26
The destination directory ~/Servers/ is the problem and it is in the home directory of either the 1d10t admin who executed the command "/home/1d10t/Servers", or in "/root/Servers" - it is NOT "/Servers" the source.

So, do a quick check and delete wherever that destination directory is.  As a test, only delete one big file, and check what is going on, before doing a rm -rf thing.

---

### Post by prince-korvin on 2019-09-26
You are absolutely right. The folder was copied in "/root/Servers", and after checking/deleting with one big file I have completely removed wrong folder. Issue resolved!

df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           394M   41M  354M  11% /run
/dev/sda2        20G  3.7G   15G  20% /
tmpfs           2.0G     0  2.0G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/sda3       1.4T  553G  830G  40% /Servers
tmpfs           394M     0  394M   0% /run/user/1007

Thank you so much for the help, Herman! :)

---

