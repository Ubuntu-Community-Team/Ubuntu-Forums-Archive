---
title: "Root drive full"
date: 2015-07-20
forum: General Help
---

### Post by r102 on 2015-07-20
Hello. I am pretty new to Linux distros, and Xubuntu, so i didn't try something, because i don't know what to try.

On Friday i wanted to save something, and i received the message that the drive is full. I thought that is some kind of error, because i didn't download something there, but i see that the problem persists. I tried to delete some files (around 160 mb), but after 1 minute i checked the space available, and it says only 6.2 mb, and that the drive is 99% full, so something is using the space, but i don't know how to detect this

LE: Maybe this helps:

sudo du -h /var/log
908K    /var/log/installer
4.0K    /var/log/speech-dispatcher
224K    /var/log/apt
4.0K    /var/log/samba/cores/nmbd
4.0K    /var/log/samba/cores/winbindd
4.0K    /var/log/samba/cores/smbd
16K    /var/log/samba/cores
44K    /var/log/samba
16K    /var/log/cups
4.0K    /var/log/unattended-upgrades
12K    /var/log/fsck
700K    /var/log/upstart
4.0K    /var/log/dist-upgrade
48K    /var/log/lightdm
4.0K    /var/log/hp/tmp
8.0K    /var/log/hp
9.6M    /var/log

---

### Post by plucky on 2015-07-20
Post output for ```
df -h
df -i
lsb_release -a
```

Good Luck

Welcome to the Forum

---

### Post by coffeecat on 2015-07-20
Welcome to the forum.

The command you used assumes the problem is in /var/log, which is sometimes the case, but I can see nothing remarkable there. Let's step back a bit.

Run this command and post the output to confirm that the problem is in the root partition, and also to tell us about your mounted filesystems:

```
df -h
```

And now this one - post the output - to tell us how much space is being used in each top-level folder in the root filesystem:

```
sudo du -h --max-depth=1 /
```

---

### Post by r102 on 2015-07-20
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        21G   19G  1.2G  95% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  8.0K  1.9G   1% /dev
tmpfs           382M  1.4M  381M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  348K  1.9G   1% /run/shm
none            100M   24K  100M   1% /run/user



df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda5      1384448 269031 1115417   20% /
none            488664      2  488662    1% /sys/fs/cgroup
udev            485991    517  485474    1% /dev
tmpfs           488664    539  488125    1% /run
none            488664      3  488661    1% /run/lock
none            488664      7  488657    1% /run/shm
none            488664     21  488643    1% /run/user



 lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty



 sudo du -h --max-depth=1 /
14M    /etc
du: cannot access ‘/run/user/1000/gvfs’: Permission denied
1.7M    /run
du: cannot access ‘/proc/3878/task/3878/fd/4’: No such file or directory
du: cannot access ‘/proc/3878/task/3878/fdinfo/4’: No such file or directory
du: cannot access ‘/proc/3878/fd/4’: No such file or directory
du: cannot access ‘/proc/3878/fdinfo/4’: No such file or directory
0    /proc
152M    /opt
8.0K    /media
125M    /boot
12M    /sbin
40K    /root
148K    /tmp
9.7M    /bin
8.0K    /dev
4.1G    /usr
3.5M    /lib32
16K    /lost+found
4.0K    /cdrom
4.0K    /mnt
4.0K    /lib64
4.0K    /srv
968M    /lib
660M    /var
13G    /home
0    /sys
19G    /

---

### Post by r102 on 2015-07-20
Now it was resolved. I found out that .thunderbird was the problem, when i wanted to sync my email and i selected IMAP, so it downloaded everything to my pc. I deleted it, and now is ok.

---

### Post by coffeecat on 2015-07-20
I'm glad you've found the source of the problem.

Going through your du -h --max-depth=1 / output, I don't see anything unusual for the system folders, but your home folder had the lion's share of the used space, which fits in with Thunderbird using too much space. There was 13G in the home folder - even allowing for the other stuff you have there, that must have been a lot of emails!

A thought for you. You have a 21GB / partition which also contains home. That's usable so long as you are careful with how much you store in your home folder. Do you have a separate data partition?

---

### Post by r102 on 2015-07-20
Yes, i have another partition for data. Do you think that it would be better to try and resize the home partition? The data partition has the 223gb capacity, but i have there around 70 gb empty space, so it would not be a problem to shrink it

Also, i have another question. I did something, and now in file manager i don't have the buttons "File", "Edit", "View", etc. How can i make them reappear?

[http://imgur.com/SgVo15h](http://imgur.com/SgVo15h)

---

### Post by sudodus on 2015-07-20
Yes, that is possible, and a good idea, if you want to keep copies of your emails 'at home'.

---

### Post by coffeecat on 2015-07-20
> **r102 said:**
> Yes, i have another partition for data. Do you think that it would be better to try and resize the home partition? The data partition has the 223gb capacity, but i have there around 70 gb empty space, so it would not be a problem to shrink it

You don't have a home partition - you have a home folder in your root partition.

If you have a separate data partition, I would not bother setting up a separate home partition. You can symlink everything you need from your data partition to your home folder. You can even do this with Thunderbird. Thunderbird keep all its data and configurations in ~/.thunderbird. What I have done is to have a .thunderbird folder in my data partition, with a symlink called .thunderbird in home pointing to the .thunderbird in the data partition. So long as I mount my data partition to the same mountpoint on bootup - which I do using /etc/fstab - then everything works just fine. But this all sounds like the subject of a separate thread if you want to start one.

I can't help you with Thunar (your file manager) problems as I have only a passing acquaintance with the Xfce desktop. I'm sure an Xubuntu user will be able to help.

---

### Post by pqwoerituytrueiwoq on 2015-07-20
you may want to set thunderbird to not download mail > X Kb (edit -> account settings -> synchronization and storage)
another thing you can do is make ~/.thunderbird a symlink to your data partition eg:
```
mv ~/.thunderbird /mnt/data/r102/ # assuming you use /etc/fstab to mount your ext4 data storage to /mnt/data
ln -s /mnt/data/r102/.thunderbird/ ~/.thunderbird
```

open thunar and press ctrl+m or hit F10 and click view -> menu bar

---

