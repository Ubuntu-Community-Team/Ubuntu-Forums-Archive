---
title: "the volume, &quot;filesystemroot&quot; has only ....."
date: 2017-12-15
forum: General Help
---

### Post by Richard-S on 2017-12-15
Since yesterday's update, I get this message when I boot Ubuntu 16.04.

**_The volume_**, **_"filesystemroot"_** has only 840.6 MB disk space remaining

I had this happen once before and I found that there were some huge temp files somewhere but I don't recall what they were or where they were located.

Richard

---

### Post by Cavsfan on 2017-12-15
> **Richard-S said:**
> Since yesterday's update, I get this message when I boot Ubuntu 16.04.

**_The volume_**, **_"filesystemroot"_** has only 840.6 MB disk space remaining

I had this happen once before and I found that there were some huge temp files somewhere but I don't recall what they were or where they were located.

Richard

Mabye this will help: **sudo apt install bleachbit**. You don't need to run the root one, just the regular one and select this:

[ATTACH=CONFIG]277849[/ATTACH]

---

### Post by ajgreeny on 2017-12-15
Take care with bleachbit; it has been known, when used incorrectly, to damage the OS to the point that it needs reinstalling, though if you follow Cavsfan's suggestion you should be fine.

It would however, be more useful to find out what exactly is using your disk space, and to know more about your partition layout etc etc, so before you start running bleachbit blind, let's see what we are dealing with.

Show us the output from command **df --hT**
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by Dennis N on 2017-12-15
I suggest using **Disk Usage Analyzer**. It includes a nice rings chart graphical representation of file system usage - root, home, or select specific folder to analyze.

---

### Post by Yellow Pasque on 2017-12-15
This should free up enough space to make the warning go away temprorarily:
```
sudo apt-get clean
```

You still should figure out what's using your disk space though.

> I suggest using Disk Usage Analyzer.
...
```
sudo apt-get install baobab
baobab
```

---

### Post by Cavsfan on 2017-12-16
> **ajgreeny said:**
> Show us the output from command **df --hT**
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

Yes, the reason needs to be determined before anything else should be done. 

I never use Bleachbit as root, just mainly to clean up browser cache etc.
Not even on my /tmp folder as that is where conky data is stored.

That command needs a single dash I found out (this is on my small Bionic development partition):

```
cavsfan@cavsfan-Le-Beast:~$ df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  2.0G     0  2.0G   0% /dev
tmpfs          tmpfs     395M  6.2M  389M   2% /run
/dev/sda6      ext4       14G  6.2G  7.2G  47% /
tmpfs          tmpfs     2.0G  6.8M  2.0G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
tmpfs          tmpfs     395M   16K  395M   1% /run/user/1000
```

This works too **sudo du -h --max-depth=1 /** (if the directory is unknown)
```
cavsfan@cavsfan-Le-Beast:~$ sudo du -h --max-depth=1 /
173M    /opt
12M    /bin
4.0K    /lib64
12M    /sbin
492M    /lib
du: cannot read directory '/proc/2071/task/2071/net': Invalid argument
du: cannot read directory '/proc/2071/net': Invalid argument
du: cannot access '/proc/13057/task/13057/fd/4': No such file or directory
du: cannot access '/proc/13057/task/13057/fdinfo/4': No such file or directory
du: cannot access '/proc/13057/fd/3': No such file or directory
du: cannot access '/proc/13057/fdinfo/3': No such file or directory
0    /proc
4.0K    /mnt
404K    /root
3.3M    /tmp
0    /dev
3.8G    /usr
0    /sys
8.0K    /media
16K    /lost+found
4.0K    /srv
5.7M    /lib32
814M    /var
4.0K    /snap
4.0K    /cdrom
du: cannot access '/run/user/1000/gvfs': Permission denied
6.2M    /run
779M    /home
70M    /boot
15M    /etc
6.2G    /

```

---

### Post by Richard-S on 2017-12-18
> Show us the output from command **df --hT**
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**I have been unable to get the command df-hT to do anything. And a lot of variations. All say "command not found"

---

### Post by DuckHook on 2017-12-18
> **Richard-S said:**
> I have been unable to get the command df-hT to do anything. And a lot of variations. All say "command not found"
You need a space between "df" and "-hT". The command is df. The <space> separates command from options. The "-" is the option delimiter. The "hT" are the options. Correctly typed, it looks like this:```
df -hT
```

---

### Post by Richard-S on 2017-12-19
> Show us the output from command **df --hT**
```

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     789M  9.5M  780M   2% /run
/dev/sda2      ext4       19G   17G  524M  98% /
tmpfs          tmpfs     3.9G   43M  3.9G   2% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda1      vfat      510M  3.6M  507M   1% /boot/efi
/dev/sda4      ext4      1.8T   15G  1.7T   1% /home
tmpfs          tmpfs     789M   60K  789M   1% /run/user/1000
/dev/sdb1      vfat      3.8G  432K  3.8G   1% /media/ricardo/SPINRITE V6

```

---

### Post by leunam12 on 2017-12-19
run ```
sudo apt autoremove
```that will free up some space, after that, open the disk usage analyzer to see what's taking up so much space on your root partition

---

### Post by Richard-S on 2017-12-19
The Disk Analyzer indicates that the /usr/src folder contains over 774,000 items and is 2.5 GB in size. It consists soley of folders named "linux-headers-xxx...

---

### Post by ajgreeny on 2017-12-19
Linux headers use a lot of inodes rather than actual space, but to see what we're dealing with let's see the output of ```
dpkg -l linux-headers* linux-image*
```
Please use **Code-Tags** for the terminal output.

---

### Post by Cavsfan on 2017-12-19
> **Richard-S said:**
> The Disk Analyzer indicates that the /usr/src folder contains over 774,000 items and is 2.5 GB in size. It consists soley of folders named "linux-headers-xxx...

Sounds like you have a lot of kernels.

I use this alias in ~/.bashrc:
```
alias list-kernels='dpkg -l | grep -e "linux-generic" -e "linux-headers" -e "linux-image"'
```

Then type **list-kernels** in terminal. (you have to close terminal once after you have added an alias if terminal is how you added it)

It lists all the kernels on the system.
I then purge all but the most recent 2 kernels. If you autoremove them, it leaves the config files (shows with rc instead if ii below).

Myself, I have a text file with the kernels listed, when one is installed, I delete the 3rd one back before rebooting.

Since I'm on Xubuntu 18.04 I only have one:
```
cavsfan@cavsfan-Le-Beast:~$ list-kernels
ii  linux-generic                            4.13.0.17.18                             amd64        Complete Generic Linux kernel and headers
ii  [COLOR=#ff0000]linux-headers-4.13.0-17[/COLOR]                  4.13.0-17.20                             all          Header files related to Linux kernel version 4.13.0
ii  [COLOR=#ff0000]linux-headers-4.13.0-17-generic[/COLOR]          4.13.0-17.20                             amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                    4.13.0.17.18                             amd64        Generic Linux kernel headers
ii  [COLOR=#ff0000]linux-image-4.13.0-17-generic[/COLOR]            4.13.0-17.20                             amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  [COLOR=#ff0000]linux-image-extra-4.13.0-17-generic[/COLOR]      4.13.0-17.20                             amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-generic                      4.13.0.17.18                             amd64        Generic Linux kernel image
```

But, on a previous install I would do this if the 3rd kernel were installed:
```
sudo apt purge linux-headers-4.13.0-16 linux-headers-4.13.0-16-generic linux-image-4.13.0-16-generic linux-image-extra-4.13.0-16-generic

```

You only want to purge the components that are red, the others parts are permanent and get modified when a new one is installed.

Edit: Sorry ajgreeny, I was a little slow.

---

### Post by Richard-S on 2017-12-19
> Linux headers use a lot of inodes rather than actual space, but to see what we're dealing with let's see the output of  	Code:
 	dpkg -l linux-headers* linux-image* 

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-headers  <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
ii  linux-headers- 4.4.0-101.12 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-101.12 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-103.12 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-103.12 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-104.12 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-104.12 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-31.50  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-31.50  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-45.66  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-45.66  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-47.68  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-47.68  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-51.72  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-51.72  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-53.74  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-53.74  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-57.78  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-57.78  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-59.80  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-59.80  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-62.83  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-62.83  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-63.84  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-63.84  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-64.85  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-64.85  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-66.87  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-66.87  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-70.91  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-70.91  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-72.93  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-72.93  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-75.96  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-75.96  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-78.99  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-78.99  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-79.100 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-79.100 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-81.104 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-81.104 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-83.106 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-83.106 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-87.110 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-87.110 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-89.112 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-89.112 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-91.114 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-91.114 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-92.115 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-92.115 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-93.116 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-93.116 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-96.119 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-96.119 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-97.120 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-97.120 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-98.121 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-98.121 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0.104.10 amd64        Generic Linux kernel headers
un  linux-image    <none>       <none>       (no description available)
ii  linux-image-4. 4.4.0-101.12 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-103.12 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-104.12 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-31.50  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-45.66  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-47.68  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-51.72  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-53.74  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-57.78  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-59.80  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-62.83  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-63.84  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-64.85  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-66.87  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-70.91  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-72.93  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-75.96  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-78.99  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-79.100 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-81.104 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-83.106 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-87.110 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-89.112 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-91.114 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-92.115 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-93.116 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-96.119 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-97.120 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-98.121 amd64        Linux kernel image for version 4.
ii  linux-image-ex 4.4.0-101.12 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-103.12 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-104.12 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-31.50  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-45.66  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-47.68  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-51.72  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-53.74  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-57.78  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-59.80  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-62.83  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-63.84  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-64.85  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-66.87  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-70.91  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-72.93  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-75.96  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-78.99  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-79.100 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-81.104 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-83.106 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-87.110 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-89.112 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-91.114 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-92.115 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-93.116 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-96.119 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-97.120 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-98.121 amd64        Linux kernel extra modules for ve
ii  linux-image-ge 4.4.0.104.10 amd64        Generic Linux kernel image
ricardo@ricardo-Aspire-TC-710:~$ 

```

---

### Post by Cavsfan on 2017-12-19
> **Richard-S said:**
> ```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-headers  <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
ii  linux-headers- 4.4.0-101.12 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-101.12 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-103.12 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-103.12 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-104.12 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-104.12 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-31.50  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-31.50  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-45.66  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-45.66  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-47.68  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-47.68  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-51.72  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-51.72  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-53.74  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-53.74  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-57.78  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-57.78  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-59.80  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-59.80  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-62.83  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-62.83  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-63.84  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-63.84  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-64.85  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-64.85  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-66.87  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-66.87  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-70.91  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-70.91  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-72.93  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-72.93  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-75.96  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-75.96  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-78.99  all          Header files related to Linux ker
ii  linux-headers- 4.4.0-78.99  amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-79.100 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-79.100 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-81.104 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-81.104 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-83.106 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-83.106 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-87.110 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-87.110 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-89.112 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-89.112 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-91.114 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-91.114 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-92.115 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-92.115 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-93.116 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-93.116 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-96.119 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-96.119 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-97.120 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-97.120 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-98.121 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-98.121 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0.104.10 amd64        Generic Linux kernel headers
un  linux-image    <none>       <none>       (no description available)
ii  linux-image-4. 4.4.0-101.12 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-103.12 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-104.12 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-31.50  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-45.66  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-47.68  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-51.72  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-53.74  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-57.78  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-59.80  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-62.83  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-63.84  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-64.85  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-66.87  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-70.91  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-72.93  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-75.96  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-78.99  amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-79.100 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-81.104 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-83.106 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-87.110 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-89.112 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-91.114 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-92.115 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-93.116 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-96.119 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-97.120 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-98.121 amd64        Linux kernel image for version 4.
ii  linux-image-ex 4.4.0-101.12 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-103.12 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-104.12 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-31.50  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-45.66  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-47.68  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-51.72  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-53.74  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-57.78  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-59.80  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-62.83  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-63.84  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-64.85  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-66.87  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-70.91  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-72.93  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-75.96  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-78.99  amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-79.100 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-81.104 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-83.106 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-87.110 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-89.112 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-91.114 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-92.115 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-93.116 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-96.119 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-97.120 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-98.121 amd64        Linux kernel extra modules for ve
ii  linux-image-ge 4.4.0.104.10 amd64        Generic Linux kernel image
ricardo@ricardo-Aspire-TC-710:~$ 

```

You could purge all of them except the 2 latest kernels.

That *is* the cause of your space problem.

---

### Post by Cavsfan on 2017-12-19
These 2 should be the only 2 kernels on your system.

```
cavsfan@cavsfan-Le-Beast:~$ dpkg -l | grep -e "linux-generic" -e "linux-headers" -e "linux-image"
ii  linux-generic                               4.4.0.104.109                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-101                     4.4.0-101.124                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-101-generic             4.4.0-101.124                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-104                     4.4.0-104.127                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-104-generic             4.4.0-104.127                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                       4.4.0.104.109                                amd64        Generic Linux kernel headers
ii  linux-image-4.4.0-101-generic               4.4.0-101.124                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-104-generic               4.4.0-104.127                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-101-generic         4.4.0-101.124                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-104-generic         4.4.0-104.127                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                         4.4.0.104.109                                amd64        Generic Linux kernel image

```

---

### Post by Yellow Pasque on 2017-12-19
These kernels should be removed automatically in 16.04 if you didn't disable automatic updates: [https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

[QUOTE=Cavsfan]That is the cause of your space problem.[/QUOTE]

Getting rid of the old kernels will certainly help, but the root partition may simply be undersized depending on how many and what programs the user installed. User has a giant 1.8TB /home partition with hardly any space used. I would try and enlarge the root partition if possible (making sure everything important is backed up, of course).
```

/dev/sda2      ext4       19G   17G  524M  98% /
/dev/sda4      ext4      1.8T   15G  1.7T   1% /home
```

---

### Post by Richard-S on 2017-12-19
> These kernels should be removed automatically in 16.04 if you didn't disable automatic updates
Updates is set to "Display Immediately"

I ran the following:

```
sudo apt-get autoremove --purge
```

It showed this:

```

richard@ricardo-Aspire-TC-710:~$ sudo apt-get autoremove --purge
[sudo] password for richard: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gdebi-core* gimp-help-common* gtk2-engines-pixbuf* kde-l10n-engb*
  kde-l10n-es* libboost-serialization1.58.0* libgoocanvas-common*
  libgoocanvas3* libmircommon5* librlog5v5* linux-headers-4.4.0-101*
  linux-headers-4.4.0-101-generic* linux-headers-4.4.0-31*
  linux-headers-4.4.0-31-generic* linux-headers-4.4.0-45*
  linux-headers-4.4.0-45-generic* linux-headers-4.4.0-47*
  linux-headers-4.4.0-47-generic* linux-headers-4.4.0-51*
  linux-headers-4.4.0-51-generic* linux-headers-4.4.0-53*
  linux-headers-4.4.0-53-generic* linux-headers-4.4.0-57*
  linux-headers-4.4.0-57-generic* linux-headers-4.4.0-59*
  linux-headers-4.4.0-59-generic* linux-headers-4.4.0-62*
  linux-headers-4.4.0-62-generic* linux-headers-4.4.0-63*
  linux-headers-4.4.0-63-generic* linux-headers-4.4.0-64*
  linux-headers-4.4.0-64-generic* linux-headers-4.4.0-66*
  linux-headers-4.4.0-66-generic* linux-headers-4.4.0-70*
  linux-headers-4.4.0-70-generic* linux-headers-4.4.0-72*
  linux-headers-4.4.0-72-generic* linux-headers-4.4.0-75*
  linux-headers-4.4.0-75-generic* linux-headers-4.4.0-78*
  linux-headers-4.4.0-78-generic* linux-headers-4.4.0-79*
  linux-headers-4.4.0-79-generic* linux-headers-4.4.0-81*
  linux-headers-4.4.0-81-generic* linux-headers-4.4.0-83*
  linux-headers-4.4.0-83-generic* linux-headers-4.4.0-87*
  linux-headers-4.4.0-87-generic* linux-headers-4.4.0-89*
  linux-headers-4.4.0-89-generic* linux-headers-4.4.0-91*
  linux-headers-4.4.0-91-generic* linux-headers-4.4.0-92*
  linux-headers-4.4.0-92-generic* linux-headers-4.4.0-93*
  linux-headers-4.4.0-93-generic* linux-headers-4.4.0-96*
  linux-headers-4.4.0-96-generic* linux-headers-4.4.0-97*
  linux-headers-4.4.0-97-generic* linux-headers-4.4.0-98*
  linux-headers-4.4.0-98-generic* linux-image-4.4.0-101-generic*
  linux-image-4.4.0-31-generic* linux-image-4.4.0-45-generic*
  linux-image-4.4.0-47-generic* linux-image-4.4.0-51-generic*
  linux-image-4.4.0-53-generic* linux-image-4.4.0-57-generic*
  linux-image-4.4.0-59-generic* linux-image-4.4.0-62-generic*
  linux-image-4.4.0-63-generic* linux-image-4.4.0-64-generic*
  linux-image-4.4.0-66-generic* linux-image-4.4.0-70-generic*
  linux-image-4.4.0-72-generic* linux-image-4.4.0-75-generic*
  linux-image-4.4.0-78-generic* linux-image-4.4.0-79-generic*
  linux-image-4.4.0-81-generic* linux-image-4.4.0-83-generic*
  linux-image-4.4.0-87-generic* linux-image-4.4.0-89-generic*
  linux-image-4.4.0-91-generic* linux-image-4.4.0-92-generic*
  linux-image-4.4.0-93-generic* linux-image-4.4.0-96-generic*
  linux-image-4.4.0-97-generic* linux-image-4.4.0-98-generic*
  linux-image-extra-4.4.0-101-generic* linux-image-extra-4.4.0-31-generic*
  linux-image-extra-4.4.0-45-generic* linux-image-extra-4.4.0-47-generic*
  linux-image-extra-4.4.0-51-generic* linux-image-extra-4.4.0-53-generic*
  linux-image-extra-4.4.0-57-generic* linux-image-extra-4.4.0-59-generic*
  linux-image-extra-4.4.0-62-generic* linux-image-extra-4.4.0-63-generic*
  linux-image-extra-4.4.0-64-generic* linux-image-extra-4.4.0-66-generic*
  linux-image-extra-4.4.0-70-generic* linux-image-extra-4.4.0-72-generic*
  linux-image-extra-4.4.0-75-generic* linux-image-extra-4.4.0-78-generic*
  linux-image-extra-4.4.0-79-generic* linux-image-extra-4.4.0-81-generic*
  linux-image-extra-4.4.0-83-generic* linux-image-extra-4.4.0-87-generic*
  linux-image-extra-4.4.0-89-generic* linux-image-extra-4.4.0-91-generic*
  linux-image-extra-4.4.0-92-generic* linux-image-extra-4.4.0-93-generic*
  linux-image-extra-4.4.0-96-generic* linux-image-extra-4.4.0-97-generic*
  linux-image-extra-4.4.0-98-generic* linux-signed-image-4.4.0-101-generic*
  linux-signed-image-4.4.0-31-generic* linux-signed-image-4.4.0-45-generic*
  linux-signed-image-4.4.0-47-generic* linux-signed-image-4.4.0-51-generic*
  linux-signed-image-4.4.0-53-generic* linux-signed-image-4.4.0-57-generic*
  linux-signed-image-4.4.0-59-generic* linux-signed-image-4.4.0-62-generic*
  linux-signed-image-4.4.0-63-generic* linux-signed-image-4.4.0-64-generic*
  linux-signed-image-4.4.0-66-generic* linux-signed-image-4.4.0-70-generic*
  linux-signed-image-4.4.0-72-generic* linux-signed-image-4.4.0-75-generic*
  linux-signed-image-4.4.0-78-generic* linux-signed-image-4.4.0-79-generic*
  linux-signed-image-4.4.0-81-generic* linux-signed-image-4.4.0-83-generic*
  linux-signed-image-4.4.0-87-generic* linux-signed-image-4.4.0-89-generic*
  linux-signed-image-4.4.0-91-generic* linux-signed-image-4.4.0-92-generic*
  linux-signed-image-4.4.0-93-generic* linux-signed-image-4.4.0-96-generic*
  linux-signed-image-4.4.0-97-generic* linux-signed-image-4.4.0-98-generic*
  python-httplib2* python-mlt* python-pygoocanvas* python-xdg*
0 upgraded, 0 newly installed, 149 to remove and 0 not upgraded.
After this operation, 8,066 MB disk space will be freed.
Do you want to continue? [Y/n] 

```
I did not continue as there are some things at the top of the list that I don't think I want to remove, and it is also going to remove the 4.4.0-101 kernel, which CavsFan said above I should keep.

---

### Post by Yellow Pasque on 2017-12-19
There is probably nothing wrong with removing those packages (and you can reinstall them if needed), but if you are trying to be safe, you can use this command to remove only the old kernels. I left -101 kernel on so you have a backup kernel.

```
sudo apt-get purge linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-headers-4.4.0-45 linux-headers-4.4.0-45-generic linux-headers-4.4.0-47 linux-headers-4.4.0-47-generic linux-headers-4.4.0-51 linux-headers-4.4.0-51-generic linux-headers-4.4.0-53 linux-headers-4.4.0-53-generic linux-headers-4.4.0-57 linux-headers-4.4.0-57-generic linux-headers-4.4.0-59 linux-headers-4.4.0-59-generic linux-headers-4.4.0-62 linux-headers-4.4.0-62-generic linux-headers-4.4.0-63 linux-headers-4.4.0-63-generic linux-headers-4.4.0-64 linux-headers-4.4.0-64-generic linux-headers-4.4.0-66 linux-headers-4.4.0-66-generic linux-headers-4.4.0-70 linux-headers-4.4.0-70-generic linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic linux-headers-4.4.0-75 linux-headers-4.4.0-75-generic linux-headers-4.4.0-78 linux-headers-4.4.0-78-generic linux-headers-4.4.0-79 linux-headers-4.4.0-79-generic linux-headers-4.4.0-81 linux-headers-4.4.0-81-generic linux-headers-4.4.0-83 linux-headers-4.4.0-83-generic linux-headers-4.4.0-87 linux-headers-4.4.0-87-generic linux-headers-4.4.0-89 linux-headers-4.4.0-89-generic linux-headers-4.4.0-91 linux-headers-4.4.0-91-generic linux-headers-4.4.0-92 linux-headers-4.4.0-92-generic linux-headers-4.4.0-93 linux-headers-4.4.0-93-generic linux-headers-4.4.0-96 linux-headers-4.4.0-96-generic linux-headers-4.4.0-97 linux-headers-4.4.0-97-generic linux-headers-4.4.0-98 linux-headers-4.4.0-98-generic linux-image-4.4.0-31-generic linux-image-4.4.0-45-generic linux-image-4.4.0-47-generic linux-image-4.4.0-51-generic linux-image-4.4.0-53-generic linux-image-4.4.0-57-generic linux-image-4.4.0-59-generic linux-image-4.4.0-62-generic linux-image-4.4.0-63-generic linux-image-4.4.0-64-generic linux-image-4.4.0-66-generic linux-image-4.4.0-70-generic linux-image-4.4.0-72-generic linux-image-4.4.0-75-generic linux-image-4.4.0-78-generic linux-image-4.4.0-79-generic linux-image-4.4.0-81-generic linux-image-4.4.0-83-generic linux-image-4.4.0-87-generic linux-image-4.4.0-89-generic linux-image-4.4.0-91-generic linux-image-4.4.0-92-generic linux-image-4.4.0-93-generic linux-image-4.4.0-96-generic linux-image-4.4.0-97-generic linux-image-4.4.0-98-generic linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-45-generic linux-image-extra-4.4.0-47-generic linux-image-extra-4.4.0-51-generic linux-image-extra-4.4.0-53-generic linux-image-extra-4.4.0-57-generic linux-image-extra-4.4.0-59-generic linux-image-extra-4.4.0-62-generic linux-image-extra-4.4.0-63-generic linux-image-extra-4.4.0-64-generic linux-image-extra-4.4.0-66-generic linux-image-extra-4.4.0-70-generic linux-image-extra-4.4.0-72-generic linux-image-extra-4.4.0-75-generic linux-image-extra-4.4.0-78-generic linux-image-extra-4.4.0-79-generic linux-image-extra-4.4.0-81-generic linux-image-extra-4.4.0-83-generic linux-image-extra-4.4.0-87-generic linux-image-extra-4.4.0-89-generic linux-image-extra-4.4.0-91-generic linux-image-extra-4.4.0-92-generic linux-image-extra-4.4.0-93-generic linux-image-extra-4.4.0-96-generic linux-image-extra-4.4.0-97-generic linux-image-extra-4.4.0-98-generic linux-signed-image-4.4.0-31-generic linux-signed-image-4.4.0-45-generic linux-signed-image-4.4.0-47-generic linux-signed-image-4.4.0-51-generic linux-signed-image-4.4.0-53-generic linux-signed-image-4.4.0-57-generic linux-signed-image-4.4.0-59-generic linux-signed-image-4.4.0-62-generic linux-signed-image-4.4.0-63-generic linux-signed-image-4.4.0-64-generic linux-signed-image-4.4.0-66-generic linux-signed-image-4.4.0-70-generic linux-signed-image-4.4.0-72-generic linux-signed-image-4.4.0-75-generic linux-signed-image-4.4.0-78-generic linux-signed-image-4.4.0-79-generic linux-signed-image-4.4.0-81-generic linux-signed-image-4.4.0-83-generic linux-signed-image-4.4.0-87-generic linux-signed-image-4.4.0-89-generic linux-signed-image-4.4.0-91-generic linux-signed-image-4.4.0-92-generic linux-signed-image-4.4.0-93-generic linux-signed-image-4.4.0-96-generic linux-signed-image-4.4.0-97-generic linux-signed-image-4.4.0-98-generic
sudo df -hT
```

---

### Post by Cavsfan on 2017-12-19
Autoremove will not remove anything that it should not remove.

```
sudo apt-get autoremove --purge
```

Will do the trick. It will likely take some time but, it will do what you need.

---

### Post by Cavsfan on 2017-12-19
> **Temüjin said:**
> These kernels should be removed automatically in 16.04 if you didn't disable automatic updates: [https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

Automatic updates do not remove kernels. If you do not pay any attention to them they will build up like the OP has.
The autoremove command run in terminal, especially with the --purge to remove the config files is what is necessary.

Synaptic is another option but, much more difficult.

I do all of my updates through terminal and know when a new kernel is installed. I keep a text file with a list of the kernels and I keep only two.

As many have done, I purge unattended-upgrades almost immediately after installation.
```
cavsfan@cavsfan-Le-Beast:~$ apt-cache policy unattended-upgrades
unattended-upgrades:
  Installed: (none)
  Candidate: 0.90ubuntu0.8
  Version table:
     0.90ubuntu0.8 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
     0.90ubuntu0.1 500
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages
     0.90 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
```

```
autoremove
       autoremove is used to remove packages that were automatically installed to satisfy dependencies for other packages and are now no longer needed.



```

This is from the man page.

Edit: add last item.

---

### Post by ajgreeny on 2017-12-19
That autoremove command is not going to remove the 4.4.0-101 kernel, only the headers and image extra of that version are to be removed, and as that version kernel will remain only as a fallback in case of problems with 4.4.0-104, you need not worry too much; it will still boot without headers or image-extra packages.

Like Cavsfan, I keep a close watch on the kernels being installed during updates, and as soon as a new one has been added and is known to boot without a problem, I purge the oldest version on my system leaving just two versions.  I also remove all headers packages except the latest version, ie, the same version as my running kernel.

Similarly, I do not personally allow unattended-upgrades on my systems; in fact I remove the package and do it all manually, though I accept that for most users it makes a great deal of sense to keep it enabled, making sure all security upgrades are installed without the user needing to do anything.  I simply prefer having control of my system and knowing exactly what is happening all the time.

---

### Post by Richard-S on 2017-12-19
I ran
```

sudo apt-get autoremove --purge
```
It cleaned out a vast amount of stuff, and now I have plenty of disk space.

Thank you a lot for your help.

Richard

---

### Post by Richard-S on 2017-12-19
And to complete things, the system still boots up. You always wonder a little.

Richard

---

### Post by ajgreeny on 2017-12-20
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

