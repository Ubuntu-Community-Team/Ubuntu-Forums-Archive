---
title: "Where has my diskspace gone?"
date: 2018-09-12
forum: General Help
---

### Post by The_Apprentice on 2018-09-12
Firstly, apologies that this seems a really common question, and yes I did Google it.  :)

I just can not work out where the space has gone.

I have 3 HDs  1x500Gb and 2x2Tb
There is no way the Ubuntu disk should be running out of space.

Any thoughts would be much appreciated.

Here is a bunch of info:
```

sean@bubble:~$ lsb_release -a
LSB Version:    core-9.20160110ubuntu0.2-amd64 : core-9.20160110ubuntu0.2-noarch : printing-9.20160110ubuntu0.2-amd64 : printing-9.20160110ubuntu0.2-noarch : security-9.20160110ubuntu0.2-amd64 : security-9.20160110ubuntu0.2-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:        16.04
Codename:       xenial

```
```

sean@bubble:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465.8G  0 disk
&#9500;&#9472;sda1   8:1    0 457.9G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part
&#9492;&#9472;sda5   8:5    0   7.9G  0 part [SWAP]
sdb      8:16   0   1.8T  0 disk
&#9492;&#9472;sdb1   8:17   0   1.8T  0 part /media/data
sdc      8:32   0   1.8T  0 disk
&#9492;&#9472;sdc1   8:33   0   1.8T  0 part /media/backups
```

```

sean@bubble:~$ df -h
Filesystem              Size  Used Avail Use% Mounted on
udev                    3.8G     0  3.8G   0% /dev
tmpfs                   786M  9.0M  777M   2% /run
/dev/sda1               451G  449G     0 100% /
tmpfs                   3.9G  4.0K  3.9G   1% /dev/shm
tmpfs                   5.0M     0  5.0M   0% /run/lock
tmpfs                   3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sdc1               1.8T  804G  937G  47% /media/backups
/dev/sdb1               1.9T  1.1T  747G  60% /media/data
//192.168.0.103/public  1.9T  1.3T  604G  68% /media/wd_nas
tmpfs                   786M     0  786M   0% /run/user/1000
```


```
sean@bubble:~$ sudo du -h / --max-depth=1
3.0G    /lib
44K     /tmp
13M     /sbin
9.4M    /etc
2.6G    /var
4.0K    /dev
0       /sys
3.2T    /media
16K     /lost+found
4.0K    /mnt
4.0K    /lib64
639M    /boot
9.0M    /run
16M     /bin
104M    /home
56K     /root
8.0K    /snap
4.0K    /srv
588K    /opt
3.1G    /usr
```


```
sean@bubble:~$ sudo du -h /media --max-depth=1
4.0K    /media/storage
1.3T    /media/wd_nas
4.0K    /media/cdrom
804G    /media/backups
1.1T    /media/data
3.2T    /media
```

---

### Post by The_Apprentice on 2018-09-12
Sorted it.

I unmounted all the drives, and saw that /media/wd_nas was still showing as having data.
I double checked by mounting it again, creating something in a subdirectory, and then unmounting.  The new file was not there.

So, whilst unmounted, I deleted everything in /media/wd_nas, and confirmed there was no extra data.
Then remounted everything.

Not sure what the root cause was, as this seems to have happened over time.
There are 3 cron jobs that back up stuff, but should never have created a "shadow" in .media/wd_nas.

Hay ho, we will see what happens.

---

