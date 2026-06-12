---
title: "Root Drive Full"
date: 2020-04-10
forum: General Help
---

### Post by mapota on 2020-04-10
Hi all,

Have looked at some of the other posts here like this but I think mine looks a bit different, happy to be corrected though.

lsb_release -a

gives me

```
******@Master-Backend:/$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:    16.04
Codename:    xenial
```



df -h gives me

```
andrew@Master-Backend:/$ df -h
Filesystem                Size  Used Avail Use% Mounted on
udev                      3.9G     0  3.9G   0% /dev
tmpfs                     794M  9.7M  784M   2% /run
/dev/sdb5                  54G   52G     0 100% /
/dev/sdb8                  46G  2.6G   41G   6% /usr
tmpfs                     3.9G  140K  3.9G   1% /dev/shm
tmpfs                     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                     3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda1                 3.7T  3.6T  117G  97% /storage3
/dev/sdb6                 4.5G   68M  4.2G   2% /boot
/dev/sdb10                 24G   44M   23G   1% /tmp
/dev/sdb9                  46G  3.9G   40G   9% /var
/dev/sdb7                  46G  4.4G   40G  10% /home
/dev/sdc1                 1.9T  1.8T   56G  98% /storage
/dev/sdd1                 3.7T  3.6T   56G  99% /storage2
//192.168.178.200/Public   14T  8.8T  5.3T  63% /mnt/NAS/Public
tmpfs                     794M   16K  794M   1% /run/user/1000



```


The issue is with /dev/sda5 mounted as /

df -i gives me 

```

******@Master-Backend:/$ df -i
Filesystem                  Inodes  IUsed     IFree IUse% Mounted on
udev                       1009613    652   1008961    1% /dev
tmpfs                      1015066    973   1014093    1% /run
/dev/sdb5                  3589264  12346   3576918    1% /
/dev/sdb8                  3055616 131239   2924377    5% /usr
tmpfs                      1015066      4   1015062    1% /dev/shm
tmpfs                      1015066      8   1015058    1% /run/lock
tmpfs                      1015066     16   1015050    1% /sys/fs/cgroup
/dev/sda1                245257416   3114 245254302    1% /storage3
/dev/sdb6                   305216    298    304918    1% /boot
/dev/sdb10                 1605632     32   1605600    1% /tmp
/dev/sdb9                  3055616  10979   3044637    1% /var
/dev/sdb7                  3055616  23911   3031705    1% /home
/dev/sdc1                233935104   6687 233928417    1% /storage
/dev/sdd1                234316944   3308 234313636    1% /storage2
//192.168.178.200/Public         0      0         0     - /mnt/NAS/Public
tmpfs                      1015066     16   1015050    1% /run/user/1000

```

So inodes look OK

sudo du --max-depth=1 -xh /  

gives me


```
*****@Master-Backend:/$ sudo du --max-depth=1 -xh /
8.0K    /media
4.0K    /cdrom
9.6M    /etc
13M    /sbin
561M    /lib
8.0K    /snap
16K    /lost+found
4.0K    /srv
112K    /root
24K    /mnt
13M    /bin
4.0K    /lib64
596M    /



```

Which seems to indicate only about 600M, not the 50G I expected to see.

If I leave out the X of course it traverses other filesystems.

I have tried Disk_usage_analyzer and it shows the same sort of result
If I start it using  sudo baobab
I get  a start screen that shows Master-Backend /   55.8GB/57.8GB. But when I click the greater than sign to investigate further it only shows 624.4Mb used.


I am obviously missing something vital

---

### Post by mapota on 2020-04-10
Have tried 
sudo apt-get clean
 It just returns now with no response, no errors either.


dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

returns with 

```
:/$ dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purgeReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 118 not upgraded.

```

I have tried clearing old kernels using the following commands

uname -r to get latest
then 
dpkg --list | grep linux-image

and using 
sudo apt-get purge linux-image-*.*.*.*-generic and
sudo apt-get purge linux-image-extra-*.*.*.*-generic

to delete until I received the following

from uname -r

4.4.0-170-generic

then from 

dpkg --list | grep linux-image
```
:/$ dpkg --list | grep linux-image
ii  linux-image-4.4.0-170-generic         4.4.0-170.199                                    amd64        Signed kernel image generic
ii  linux-image-generic                   4.4.0.170.178                                    amd64        Generic Linux kernel image

```

then from df I still see

```
df -h
Filesystem                Size  Used Avail Use% Mounted on
udev                      3.9G     0  3.9G   0% /dev
tmpfs                     794M  9.7M  784M   2% /run
/dev/sdb5                  54G   52G     0 100% /
/dev/sdb8                  46G  2.6G   41G   6% /usr
tmpfs                     3.9G  140K  3.9G   1% /dev/shm
tmpfs                     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                     3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda1                 3.7T  3.6T  117G  97% /storage3
/dev/sdb6                 4.5G   68M  4.2G   2% /boot
/dev/sdb10                 24G   44M   23G   1% /tmp
/dev/sdb9                  46G  3.9G   40G   9% /var
/dev/sdb7                  46G  4.4G   40G  10% /home
/dev/sdc1                 1.9T  1.8T   56G  98% /storage
/dev/sdd1                 3.7T  3.6T   56G  99% /storage2
//192.168.178.200/Public   14T  8.8T  5.3T  63% /mnt/NAS/Public
tmpfs                     794M   12K  794M   1% /run/user/1000



```

---

### Post by deadflowr on 2020-04-11
A possibly would be that some of the sub-directories normally on other disks/partitions didn't properly mount and instead they were,
at one point in time, mounted within/under the main root volume.
In this case the used space of those sub-directories would be lost in the ether since those are now properly mounted in other partitions.
Might be good to check the partitions using a live session.
just a thought.

---

### Post by mapota on 2020-04-11
OK will try a live disk and see what is going on. Thanks

---

### Post by Impavidus on 2020-04-11
You used a somewhat uncommon way to partition your storage. You've got separate partitions for /usr, /var, /tmp, /boot and /home, which are about all the top-level directories that can be on a separate partition, and using less-than-ideal sizes. A separate /home is often recommended (I've got one too), a separate /boot is needed in some cases (but not in your case), the others only complicate matters, except in some very special circumstances.

As deadflowr suggests, the most likely scenario is that there are files in the directories you used as mountpoints, now hidden underneath the data from the other partitions. In addition to a live disk, you can also investigate using recovery mode->drop to a root shell, but you may prefer the GUI you get in a live session.

---

### Post by mapota on 2020-04-11
OK managed to get a live system up, df still showing same results, ie 100% full on /dev/sdb5

Mounted it and then checked and found it was the NAS mounting. Lots of backups going to the /mnt/NAS/Public directory on sdb5 rather than the actual NAS filesystem.

Deleted those and now / is down to 17%.

Thanks for your help.

I do still have an issue that was the original symptom. My troubleshoioting of that brought the root directory size to my attention, bu the issue is still there.

Will check for solutions and raise a different thread if required.

---

### Post by mörgæs on 2020-04-12
Now you at least have a system from which you are able to salvage your user files. 

In stead of trying to fix errors you could let it limp along rest of the month and do a fresh install of 20.04 when it's released.

---

