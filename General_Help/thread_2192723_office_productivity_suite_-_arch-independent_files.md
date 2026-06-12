---
title: "office productivity suite - arch-independent files (libreoffice-common)"
date: 2013-12-09
forum: General Help
---

### Post by tb75252 on 2013-12-09
I am using Ubuntu 12.04 LTS, 64-bit.

Today I was presented with the update mentioned in the subject line.  When Update Manager attempts to process the update, it gives the following error message:

> **Package operation failed.**
The installation or removal of a software package failed.

The error details:
> installArchives() failed: (Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 737454 files and directories currently installed.) 
Preparing to replace libreoffice-common 1:3.5.7-0ubuntu4 (using .../libreoffice-common_1%%3a3.5.7-0ubuntu5_all.deb) ... 
Unpacking replacement libreoffice-common ... 
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%%3a3.5.7-0ubuntu5_all.deb (--unpack): 
 unable to make backup symlink for `./usr/share/icons/hicolor/16x16/mimetypes/application-vnd.oasis.opendocument.master-document.png': No space left on device 
No apport report written because MaxReports is reached already
rmdir: failed to remove `/var/lib/libreoffice/share/prereg/': No such file or directory 
rmdir: failed to remove `/var/lib/libreoffice/share/': Directory not empty 
rmdir: failed to remove `/var/lib/libreoffice/program/': No such file or directory 
rmdir: failed to remove `/var/lib/libreoffice': Directory not empty 
rmdir: failed to remove `/var/lib/libreoffice': Directory not empty 
Processing triggers for shared-mime-info ... 
Processing triggers for man-db ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for gnome-icon-theme ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/libreoffice-common_1%%3a3.5.7-0ubuntu5_all.deb 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

Anyone knows what needs to be done to rectify the problem?  Please note that I am not much of a computer expert, so I probably will need detailed help...

---

### Post by Impavidus on 2013-12-09
> unable to make backup symlink for  `./usr/share/icons/hicolor/16x16/mimetypes/application-vnd.oasis.opendocument.master-document.png':  **No space left on device**This seems to indicate a full partition. Run ```
df -Th
df -i
``` in a terminal to find out if that's indeed the case. Have a look at [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670) for some ideas to find the offending directories.

---

### Post by tb75252 on 2013-12-09
> **Impavidus said:**
> This seems to indicate a full partition. Run ```
df -Th
df -i
``` in a terminal to find out if that's indeed the case. Have a look at [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670) for some ideas to find the offending directories.
The solutions presented under sect. 6e in the link you gave me seem to have solved the problem.  I was able to install the "libreoffice-common" files.

*df -Th* now reports:
> $ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda1      ext4       12G  8.2G  2.7G  76% /
udev           devtmpfs  1.5G   12K  1.5G   1% /dev
tmpfs          tmpfs     599M  844K  598M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.5G  396K  1.5G   1% /run/shm
/dev/sda5      ext4       12G  830M   10G   8% /home
and *df -i*:
> $ df -i
Filesystem     Inodes  IUsed  IFree IUse% Mounted on
/dev/sda1      753664 729283  24381   97% /
udev           380960    558 380402    1% /dev
tmpfs          383163    471 382692    1% /run
none           383163      3 383160    1% /run/lock
none           383163      8 383155    1% /run/shm
/dev/sda5      753664   4242 749422    1% /home
Whereas *sudo find -size +1G /* suggested in 6d gives the following error:  (_how do I notify the author of the guide?_)
> $ sudo find -size +1G /
find: paths must precede expression: /
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]


To me a 97% usage of / (as reported by *df -i*) is suspicious, particularly because I have a standard installation of 12.04 LTS.  But I am having troubles pinpointing what takes up so much space...

---

### Post by Impavidus on 2013-12-09
You're using 76% of available disk space in / and 97% of available inodes, which is the maximum number of files and directories. One thing to look at is old header packages, they tend to consume a lot of inodes. Those packages are named linux-headers-<some version>. The old ones can be uninstalled using the package manager.

But the real problem is that your partition is rather small and has only few inodes available. I don't think it's easy to fix without reinstalling. With only 24GB in total I wouldn't make a separate /home partition. As you see, your / is almost full and you have a lot of space in /home. You'll have to keep an eye on it to keep it running, but it's doable.

---

### Post by tb75252 on 2013-12-09
> **Impavidus said:**
> You're using 76% of available disk space in / and 97% of available inodes, which is the maximum number of files and directories. One thing to look at is old header packages, they tend to consume a lot of inodes. Those packages are named linux-headers-<some version>. The old ones can be uninstalled using the package manager.

But the real problem is that your partition is rather small and has only few inodes available. I don't think it's easy to fix without reinstalling. With only 24GB in total I wouldn't make a separate /home partition. As you see, your / is almost full and you have a lot of space in /home. You'll have to keep an eye on it to keep it running, but it's doable.
Yes, I agree that old kernel files are part of the problem.
After doing some search online, I found this command line that deletes old kernels:
```
sudo apt-get remove --purge $(dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d')
```
After running the command, I am down to 47% used space.  Quite a gain!

Thanks for your help.  I am marking this thread as solved.

---

### Post by Iowan on 2013-12-09
[This]("http://ubuntuforums.org/showthread.php?t=2191894&page=4&p=12866952#post12866952") thread/post has a similar (slightly modified) version of that command.

---

