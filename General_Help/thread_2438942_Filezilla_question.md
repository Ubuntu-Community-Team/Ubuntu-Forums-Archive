---
title: "Filezilla question"
date: 2020-03-20
forum: General Help
---

### Post by michael351 on 2020-03-20
Suddenly it seems, when I start Filezilla, I can't change to a directory on the local machine which is in a different partition. It doesn't see it. My boot and home directory are on one disk and I have a data directory and filesystem on another disk. It is this data directory which is not visible - I can't change to it. See red highlighted below. When in FileZilla I am unable to change to /data.
I then set a soft link from my /home directory pointing to the /data and Filezilla won't follow the link. I checked permissions and all are set to 775. 

Suggestions?


Filesystem           Size  Used Avail Use% Mounted on
devtmpfs              16G     0   16G   0% /dev
tmpfs                 16G  8.0K   16G   1% /dev/shm
tmpfs                 16G  9.6M   16G   1% /run
tmpfs                 16G     0   16G   0% /sys/fs/cgroup
/dev/mapper/cl-root   50G  7.3G   43G  15% /
/dev/loop2           161M  161M     0 100% /var/lib/snapd/snap/gnome-3-28-1804/116
/dev/loop0            55M   55M     0 100% /var/lib/snapd/snap/core18/1668
/dev/loop3            45M   45M     0 100% /var/lib/snapd/snap/filezilla/17
/dev/loop4            25M   25M     0 100% /var/lib/snapd/snap/snapd/6434
/dev/loop1            45M   45M     0 100% /var/lib/snapd/snap/gtk-common-themes/1440
[COLOR=#ff0000]/dev/sdb1            1.8T  158G  1.6T  10% /data
/dev/mapper/cl-home  1.8T   20G  1.8T   2% /home
/dev/sda1            976M  209M  701M  23% /boot[/COLOR]
tmpfs                3.2G  1.2M  3.2G   1% /run/user/42
tmpfs                3.2G   20K  3.2G   1% /run/user/1000

---

### Post by TheFu on 2020-03-20
is filezilla a snap package?  Snaps only have access to the HOME directory.

To see which pkgs are snaps:
```
$ snap list
```

Besides that guess, no clue.  i don't use filezilla since the built-in file managers all support sftp or I’ll just use the cli version.

Looks like filezilla is a snap.  
[https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022](https://ubuntuforums.org/showthread.php?t=2434651&p=13923022#post13923022)
Perhaps this can help w/ /media/ access, but nowhere else.
```
snap connect filezilla:removable-media
```
The snap package creator has to allow that connect.

---

### Post by HermanAB on 2020-03-22
Hmm, I agree with the above that using Filezilla on Linux is kinda useless, since everything supports FTP/SFTP/SCP... 

In your favourite file browser, look for something like 'Connect to server'.

---

