---
title: "Desktop Linux PC running out of partition space....again..will not boot...help!"
date: 2022-02-10
forum: General Help
---

### Post by ozark_hillbilly on 2022-02-10
Two weeks ago my Desktop PC running Ubuntu 20.04 LTS ran out of storage space on a critical partition, shutdown, and refused to reboot.
It had started to give me warning errors while running the Chrome browser about low memory. Things quickly became wonky and it crashed.

I have since reinstalled the OS after re-partitioning the two physical hard drives: a  250 GB  (sda) and 150 GB (sdb).
I have attached screenshots of the gparted windows showing the partitions on sda.

There is the 250 GB drive that has the boot partition (sda1) and two additional partitions: sda5 and sda2.
What confuses me is that sda5 (ext4) shows a size of 232.8 GB and sda2 (extended) also shows the same 232.8 GB size. 
How can each partition be that large on a 250 GB hard drive? 

Because sda5 only has 4 GB left (96% full) I believe this is causing the system to crash. What is weird is that I have only
put a 6 GB Deja Dup backup on that partition. But it shows being nearly full. ???

So I screwed up somewhere re-partitioning this hard drive. 

What are my options? Should I delete the extended partition (sda2)  and upsize the ext4 partition (sda5)? I need to know why
the OS is thinking this partition is getting filled up.  

Any help would be greatly appreciated. I am booting off a USB drive with 20.04 LTS currently and do have a /home backup but
dread having to do a fresh install and and reload all those software packages from scratch.

Again, attached are the screenshots showing the gparted info.

---

### Post by deadflowr on 2022-02-10
> Should I delete the extended partition (sda2) and upsize the ext4 partition (sda5)? 
Impossible as they are the same thing, basically.
/dev/sda5 is a logical partition inside of the extended /dev/sda2 partition,
so deleting /dev/sda2 will delete everything inside it including /dev/sda5.

You should run a disk usage command to determine where you've grown and proceed from there.
I'd recommend following CharlesA's two commands here as a start: [https://ubuntuforums.org/showthread.php?t=2463845&p=14044359#post14044359]("https://ubuntuforums.org/showthread.php?t=2463845&p=14044359#post14044359")

---

### Post by linux-sysop on 2022-02-10
I am not familar with Deja Dup.  I use Timeshift for backup and turn off scheduled backups.   if you are scheduling backups often, keeping them, you could have several unwanted copies on your drive.  Boot a live CD/USB and look on your HDD where Deja Dup keeps the backups.  According to the man pages Deja-Dup is suppose to keep your backups off site over a network or on an external drive.  I keep my backups on a USB thumb drive.  If you are saving them to a 250 GB drive and 10GB is used for the OS, then 20 backups later and your HD is full.  It could be exponential growth if you are backing up all those backups too.  First backup use 10 GB, second is 20 GB, third back up is 40 GB, 80, 160, etc..  

Look at file sizes.  At the terminal in the Live boot;

Go to the mounted HD in terminal window start in the home directory and type;  
$ du | sort -n
du is disk usage and sort -n will place the largest files at the end.  If you need a hard copy to browse;
$ du | sort -n > files.txt
will create the text document.  

The setup looks odd by the way.  I have a 240 GB SSD and mine is partition as;
$ lsblk
sdc      8:32   0 232.9G  0 disk 
&#9500;&#9472;sdc1   8:33   0   200M  0 part 
&#9500;&#9472;sdc2   8:34   0   100G  0 part 
&#9500;&#9472;sdc3   8:35   0   500M  0 part [SWAP]
&#9492;&#9472;sdc4   8:36   0 132.2G  0 part /media/sysop/Galaxy
sr0     11:0    1  1024M  0 rom  


As you can see the OS is only on sdc2 at 100 GB, with 62 GB of free space, and sdc4 "Galaxy" is extra work space where I keep important work files. I know I am old school with the swap area, but did the system create the extended partition or was this your custom format?

---

### Post by ozark_hillbilly on 2022-02-10
deadflowr,

I ran those commands you suggested. Attached is the screenshot.
It looks like the /loop# are all full. Not sure what they are for.

???

```
root@ubuntu:/dev# sudo df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           390M  1.6M  389M   1% /run
/dev/sdc1       7.5G  3.9G  3.6G  52% /cdrom
/dev/loop0      2.1G  2.1G     0 100% /rofs
/cow            2.0G  232M  1.7G  12% /
tmpfs           2.0G     0  2.0G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           2.0G     0  2.0G   0% /sys/fs/cgroup
tmpfs           2.0G  500K  2.0G   1% /tmp
/dev/loop1       56M   56M     0 100% /snap/core18/2128
/dev/loop5       66M   66M     0 100% /snap/gtk-common-themes/1515
/dev/loop4       51M   51M     0 100% /snap/snap-store/547
/dev/loop3       33M   33M     0 100% /snap/snapd/12704
/dev/loop2      219M  219M     0 100% /snap/gnome-3-34-1804/72
tmpfs           390M   88K  390M   1% /run/user/999
```

With Deja Dup,  which is the standard backup utility that comes w/ 20.04 LTS, I have only
performed manual backups. And sda5 only has had two backups applied to it.

What concerns me is /rofs and /snap showing 100%.

```
root@ubuntu:/dev# sudo df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           390M  1.6M  389M   1% /run
/dev/sdc1       7.5G  3.9G  3.6G  52% /cdrom
/dev/loop0      2.1G  2.1G     0 100% /rofs
/cow            2.0G  232M  1.7G  12% /
tmpfs           2.0G     0  2.0G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           2.0G     0  2.0G   0% /sys/fs/cgroup
tmpfs           2.0G  500K  2.0G   1% /tmp
/dev/loop1       56M   56M     0 100% /snap/core18/2128
/dev/loop5       66M   66M     0 100% /snap/gtk-common-themes/1515
/dev/loop4       51M   51M     0 100% /snap/snap-store/547
/dev/loop3       33M   33M     0 100% /snap/snapd/12704
/dev/loop2      219M  219M     0 100% /snap/gnome-3-34-1804/72
tmpfs           390M   88K  390M   1% /run/user/999
```

I am going to sit tight and not attempt any root commands regarding deleting/resizing /partitions, /folders, or files until someone gives me some advice. Hello!!!!

More drive info:

```
root@ubuntu:/dev# sudo parted -l
Model: ATA WDC WD2500AAKS-0 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  538MB  537MB  primary   fat32        boot
 2      539MB   250GB  250GB  extended
 5      539MB   250GB  250GB  logical   ext4


Model: ATA WDC WD1600AAJS-0 (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  78.0GB  78.0GB  primary   ext4
 3      78.0GB  78.5GB  537MB   primary   linux-swap(v1)
 2      78.5GB  160GB   81.5GB  extended
 5      78.5GB  158GB   79.4GB  logical   ext4
 6      158GB   160GB   2110MB  logical   linux-swap(v1)


Model: SanDisk Cruzer (scsi)
Disk /dev/sdc: 8000MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  7998MB  7998MB  primary  fat32        boot, lba
```

*********************************************************************
```
root@ubuntu:/dev# uname -a
Linux ubuntu 5.11.0-27-generic #29~20.04.1-Ubuntu SMP Wed Aug 11 15:58:17 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
root@ubuntu:/dev# 
```

*********************************************************************
```
root@ubuntu:/dev# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.3 LTS
Release:	20.04
Codename:	focal
root@ubuntu:/dev#
```

---

### Post by deadflowr on 2022-02-10
So you ran it from a Live usb/cdrom instead the actual installed system?
You needed to have the  file system mounted in order for it to be helpful.

I guess you can mount it like
```
sudo mount /dev/sda5 /mnt
```
That will mount the file system into the /mnt directory, you could then re-run the df -h command 
and then run second command with a slight modification like
```
sudo du --human-readable --max-depth=1 --exclude /dev --exclude /proc --exclude /sys /mnt/*
```
> What concerns me is /rofs and /snap showing 100%.

It's not concerning.
See: [https://askubuntu.com/questions/26722/device-type-loop-in-mount-command]("https://askubuntu.com/questions/26722/device-type-loop-in-mount-command")
for a basic idea about loop mounts.

---

### Post by ozark_hillbilly on 2022-02-10
I ran the commands u suggested. /mnt/var & /mnt/var/log are huge!!!

```
root@ubuntu:/# sudo mount /dev/sda5 /mnt
root@ubuntu:/# sudo du --human-readable --max-depth=1 --exclude /dev --exclude /proc --exclude /sys /mnt/*
7.1G	/mnt/Ubuntu Home Backup
4.3G	/mnt/backup/deja_dup
4.3G	/mnt/backup
0	/mnt/bin
7.1M	/mnt/boot/grub
4.0K	/mnt/boot/efi
153M	/mnt/boot
4.0K	/mnt/cdrom
4.0K	/mnt/dev/shm
4.0K	/mnt/dev/pts
12K	/mnt/dev
20K	/mnt/etc/cron.weekly
8.0K	/mnt/etc/thermald
12K	/mnt/etc/chromium
4.0K	/mnt/etc/rc5.d
8.0K	/mnt/etc/cracklib
432K	/mnt/etc/X11
12K	/mnt/etc/rsyslog.d
112K	/mnt/etc/dbus-1
8.0K	/mnt/etc/cron.hourly
16K	/mnt/etc/lighttpd
36K	/mnt/etc/dpkg
136K	/mnt/etc/grub.d
132K	/mnt/etc/speech-dispatcher
20K	/mnt/etc/apm
12K	/mnt/etc/ubuntu-advantage
52K	/mnt/etc/cron.daily
3.8M	/mnt/etc/brltty
72K	/mnt/etc/sgml
8.0K	/mnt/etc/gtk-2.0
36K	/mnt/etc/profile.d
16K	/mnt/etc/apparmor
8.0K	/mnt/etc/snmp
4.0K	/mnt/etc/rc4.d
4.0K	/mnt/etc/dictionaries-common
184K	/mnt/etc/systemd
168K	/mnt/etc/console-setup
8.0K	/mnt/etc/ldap
276K	/mnt/etc/ImageMagick-6
16K	/mnt/etc/opt
12K	/mnt/etc/vim
32K	/mnt/etc/logcheck
56K	/mnt/etc/iproute2
4.0K	/mnt/etc/rcS.d
48K	/mnt/etc/fwupd
12K	/mnt/etc/groff
4.0K	/mnt/etc/rc1.d
96K	/mnt/etc/cups
8.0K	/mnt/etc/selinux
8.0K	/mnt/etc/ca-certificates
8.0K	/mnt/etc/geoclue
28K	/mnt/etc/gnome
60K	/mnt/etc/acpi
4.0K	/mnt/etc/tmpfiles.d
72K	/mnt/etc/gdm3
12K	/mnt/etc/libnl-3
44K	/mnt/etc/wpa_supplicant
4.0K	/mnt/etc/update-notifier
612K	/mnt/etc/ssl
44K	/mnt/etc/modprobe.d
168K	/mnt/etc/apt
60K	/mnt/etc/security
4.0K	/mnt/etc/rc0.d
40K	/mnt/etc/dhcp
12K	/mnt/etc/apache2
8.0K	/mnt/etc/ifplugd
16K	/mnt/etc/ld.so.conf.d
8.0K	/mnt/etc/netplan
20K	/mnt/etc/mysql
16K	/mnt/etc/chatscripts
16K	/mnt/etc/pm
8.0K	/mnt/etc/python3
12K	/mnt/etc/ssh
4.0K	/mnt/etc/sensors.d
40K	/mnt/etc/apport
4.0K	/mnt/etc/libpaper.d
16K	/mnt/etc/vulkan
8.0K	/mnt/etc/terminfo
28K	/mnt/etc/pulse
52K	/mnt/etc/xml
12K	/mnt/etc/emacs
40K	/mnt/etc/sysctl.d
4.0K	/mnt/etc/binfmt.d
16K	/mnt/etc/libreoffice
12K	/mnt/etc/firefox
672K	/mnt/etc/apparmor.d
4.0K	/mnt/etc/rc2.d
56K	/mnt/etc/ufw
28K	/mnt/etc/dconf
8.0K	/mnt/etc/sudoers.d
12K	/mnt/etc/alsa
8.0K	/mnt/etc/modules-load.d
12K	/mnt/etc/PackageKit
16K	/mnt/etc/bash_completion.d
8.0K	/mnt/etc/UPower
52K	/mnt/etc/NetworkManager
68K	/mnt/etc/initramfs-tools
260K	/mnt/etc/xdg
56K	/mnt/etc/update-motd.d
464K	/mnt/etc/fonts
12K	/mnt/etc/cron.monthly
8.0K	/mnt/etc/glvnd
20K	/mnt/etc/compizconfig
12K	/mnt/etc/perl
84K	/mnt/etc/udev
36K	/mnt/etc/ghostscript
128K	/mnt/etc/default
20K	/mnt/etc/cron.d
20K	/mnt/etc/update-manager
344K	/mnt/etc/sane.d
8.0K	/mnt/etc/insserv.conf.d
36K	/mnt/etc/pki
20K	/mnt/etc/avahi
60K	/mnt/etc/logrotate.d
12K	/mnt/etc/alternatives
8.0K	/mnt/etc/calendar
28K	/mnt/etc/networkd-dispatcher
12K	/mnt/etc/libblockdev
80K	/mnt/etc/ppp
40K	/mnt/etc/polkit-1
120K	/mnt/etc/pam.d
8.0K	/mnt/etc/gss
48K	/mnt/etc/network
16K	/mnt/etc/openvpn
12K	/mnt/etc/environment.d
8.0K	/mnt/etc/pcmcia
8.0K	/mnt/etc/python3.8
8.0K	/mnt/etc/init
8.0K	/mnt/etc/udisks2
12K	/mnt/etc/gtk-3.0
4.0K	/mnt/etc/rc6.d
4.0K	/mnt/etc/rc3.d
16K	/mnt/etc/cupshelpers
180K	/mnt/etc/init.d
8.0K	/mnt/etc/depmod.d
16K	/mnt/etc/skel
8.0K	/mnt/etc/hp
16K	/mnt/etc/bluetooth
52K	/mnt/etc/kernel
8.0K	/mnt/etc/gdb
8.0K	/mnt/etc/newt
12M	/mnt/etc
15G	/mnt/home/ed
15G	/mnt/home
0	/mnt/lib
0	/mnt/lib32
0	/mnt/lib64
0	/mnt/libx32
4.0K	/mnt/media/ed
8.0K	/mnt/media
4.0K	/mnt/mnt
278M	/mnt/opt/google
278M	/mnt/opt
4.0K	/mnt/proc
9.2M	/mnt/root/.cache
48K	/mnt/root/.synaptic
24K	/mnt/root/.config
12K	/mnt/root/.dbus
16K	/mnt/root/snap
124K	/mnt/root/.local
9.5M	/mnt/root
12K	/mnt/run/lock
4.0K	/mnt/run/sendsigs.omit.d
4.0K	/mnt/run/speech-dispatcher
48K	/mnt/run/systemd
4.0K	/mnt/run/dnsmasq
8.0K	/mnt/run/sudo
4.0K	/mnt/run/lvm
4.0K	/mnt/run/log
4.0K	/mnt/run/mount
4.0K	/mnt/run/user
4.0K	/mnt/run/hplip
112K	/mnt/run
0	/mnt/sbin
12K	/mnt/snap/gnome-3-34-1804
8.0K	/mnt/snap/gnome-3-38-2004
4.0K	/mnt/snap/bin
12K	/mnt/snap/core18
8.0K	/mnt/snap/snap-store
12K	/mnt/snap/snapd
12K	/mnt/snap/core20
8.0K	/mnt/snap/bare
12K	/mnt/snap/gtk-common-themes
96K	/mnt/snap
4.0K	/mnt/srv
2.1G	/mnt/swapfile
4.0K	/mnt/sys
8.0K	/mnt/tmp/systemd-private-148613510a8040f899cc98f8c16643e9-systemd-resolved.service-bYTa9g
8.0K	/mnt/tmp/systemd-private-148613510a8040f899cc98f8c16643e9-systemd-timesyncd.service-8WBAIh
8.0K	/mnt/tmp/systemd-private-148613510a8040f899cc98f8c16643e9-upower.service-WFi7Ye
8.0K	/mnt/tmp/systemd-private-148613510a8040f899cc98f8c16643e9-switcheroo-control.service-y6S93f
8.0K	/mnt/tmp/systemd-private-148613510a8040f899cc98f8c16643e9-systemd-logind.service-EpDdti
8.0K	/mnt/tmp/systemd-private-148613510a8040f899cc98f8c16643e9-systemd-timedated.service-MG7N8g
60K	/mnt/tmp
4.0K	/mnt/usr/lib64
185M	/mnt/usr/bin
33M	/mnt/usr/sbin
13M	/mnt/usr/libexec
716K	/mnt/usr/games
4.0K	/mnt/usr/lib32
15M	/mnt/usr/local
989M	/mnt/usr/share
25M	/mnt/usr/include
278M	/mnt/usr/src
3.1G	/mnt/usr/lib
4.0K	/mnt/usr/libx32
4.6G	/mnt/usr
4.0K	/mnt/var/opt
4.0K	/mnt/var/metrics
4.0K	/mnt/var/local
52K	/mnt/var/spool
189G	/mnt/var/log
1008K	/mnt/var/snap
149M	/mnt/var/cache
46M	/mnt/var/crash
4.4M	/mnt/var/backups
1.9G	/mnt/var/lib
52K	/mnt/var/tmp
4.0K	/mnt/var/mail
191G	/mnt/var
root@ubuntu:/#
```
Terminal:

```
root@ubuntu:/mnt# cd var
root@ubuntu:/mnt/var# ls
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  snap  spool  tmp
root@ubuntu:/mnt/var# cd backups
root@ubuntu:/mnt/var/backups# ls
alternatives.tar.0        apt.extended_states.2.gz  dpkg.arch.2.gz        dpkg.diversions.2.gz    dpkg.statoverride.2.gz  dpkg.status.2.gz
alternatives.tar.1.gz     apt.extended_states.3.gz  dpkg.arch.3.gz        dpkg.diversions.3.gz    dpkg.statoverride.3.gz  dpkg.status.3.gz
alternatives.tar.2.gz     apt.extended_states.4.gz  dpkg.arch.4.gz        dpkg.diversions.4.gz    dpkg.statoverride.4.gz  dpkg.status.4.gz
alternatives.tar.3.gz     apt.extended_states.5.gz  dpkg.arch.5.gz        dpkg.diversions.5.gz    dpkg.statoverride.5.gz  dpkg.status.5.gz
alternatives.tar.4.gz     apt.extended_states.6.gz  dpkg.arch.6.gz        dpkg.diversions.6.gz    dpkg.statoverride.6.gz  dpkg.status.6.gz
apt.extended_states.0     dpkg.arch.0               dpkg.diversions.0     dpkg.statoverride.0     dpkg.status.0
apt.extended_states.1.gz  dpkg.arch.1.gz            dpkg.diversions.1.gz  dpkg.statoverride.1.gz  dpkg.status.1.gz
```



```
root@ubuntu:/mnt/var/backups# cd ..
root@ubuntu:/mnt/var# ls
backups  cache  crash  lib  local  lock  log  mail  metrics  opt  run  snap  spool  tmp
root@ubuntu:/mnt/var# cd log
root@ubuntu:/mnt/var/log# ls
Xorg.0.log          auth.log       bootstrap.log  dmesg.3.gz       installer          syslog                      ubuntu-advantage-timer.log.1
Xorg.0.log.old      auth.log.1     btmp           dmesg.4.gz       journal            syslog.1                    ubuntu-advantage.log
alternatives.log    auth.log.2.gz  btmp.1         dpkg.log         kern.log           syslog.2.gz                 ubuntu-advantage.log.1
alternatives.log.1  boot.log       cups           dpkg.log.1       kern.log.1         syslog.3.gz                 unattended-upgrades
apport.log          boot.log.1     dist-upgrade   faillog          kern.log.2.gz      syslog.4.gz                 wtmp
apport.log.1        boot.log.2     dmesg          fontconfig.log   lastlog            syslog.5.gz
apport.log.2.gz     boot.log.3     dmesg.0        gdm3             openvpn            syslog.6.gz
apport.log.3.gz     boot.log.4     dmesg.1.gz     gpu-manager.log  private            syslog.7.gz
apt                 boot.log.5     dmesg.2.gz     hp               speech-dispatcher  ubuntu-advantage-timer.log
root@ubuntu:/mnt/var/log#
```

---

### Post by deadflowr on 2022-02-10
Wow, your logs are huge so something in those are problematic.
Let's see what those are
```
sudo du --human-readable --max-depth=1 /mnt/var/log/* | sort -h
```
I've added the sort command as that should make the output more discernible.

EDIT:
Also please see this about how to use code tags: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by ozark_hillbilly on 2022-02-10
Terminal output:
```

root@ubuntu:/mnt/var/log# sudo du --human-readable --max-depth=1 /mnt/var/log/* | sort -h
0	/mnt/var/log/Xorg.0.log
0	/mnt/var/log/btmp
0	/mnt/var/log/btmp.1
0	/mnt/var/log/ubuntu-advantage.log
4.0K	/mnt/var/log/alternatives.log
4.0K	/mnt/var/log/apport.log.1
4.0K	/mnt/var/log/apport.log.2.gz
4.0K	/mnt/var/log/apport.log.3.gz
4.0K	/mnt/var/log/gdm3
4.0K	/mnt/var/log/gpu-manager.log
4.0K	/mnt/var/log/hp/tmp
4.0K	/mnt/var/log/openvpn
4.0K	/mnt/var/log/private
4.0K	/mnt/var/log/speech-dispatcher
4.0K	/mnt/var/log/ubuntu-advantage-timer.log
4.0K	/mnt/var/log/ubuntu-advantage-timer.log.1
4.0K	/mnt/var/log/ubuntu-advantage.log.1
4.0K	/mnt/var/log/unattended-upgrades
8.0K	/mnt/var/log/faillog
8.0K	/mnt/var/log/hp
12K	/mnt/var/log/auth.log.2.gz
12K	/mnt/var/log/boot.log.1
12K	/mnt/var/log/boot.log.2
12K	/mnt/var/log/boot.log.3
12K	/mnt/var/log/boot.log.4
12K	/mnt/var/log/fontconfig.log
20K	/mnt/var/log/dmesg.1.gz
20K	/mnt/var/log/dmesg.2.gz
20K	/mnt/var/log/dmesg.3.gz
20K	/mnt/var/log/dmesg.4.gz
28K	/mnt/var/log/wtmp
32K	/mnt/var/log/alternatives.log.1
36K	/mnt/var/log/apport.log
40K	/mnt/var/log/boot.log.5
40K	/mnt/var/log/dist-upgrade
44K	/mnt/var/log/dpkg.log
44K	/mnt/var/log/lastlog
48K	/mnt/var/log/auth.log
60K	/mnt/var/log/Xorg.0.log.old
72K	/mnt/var/log/auth.log.1
72K	/mnt/var/log/boot.log
76K	/mnt/var/log/dmesg
80K	/mnt/var/log/dmesg.0
104K	/mnt/var/log/bootstrap.log
108K	/mnt/var/log/syslog.2.gz
132K	/mnt/var/log/syslog.5.gz
136K	/mnt/var/log/kern.log.2.gz
152K	/mnt/var/log/apt
220K	/mnt/var/log/syslog.3.gz
220K	/mnt/var/log/syslog.7.gz
276K	/mnt/var/log/syslog.6.gz
316K	/mnt/var/log/syslog.4.gz
524K	/mnt/var/log/kern.log
596K	/mnt/var/log/kern.log.1
684K	/mnt/var/log/syslog.1
1.1M	/mnt/var/log/installer
1.3M	/mnt/var/log/dpkg.log.1
4.1M	/mnt/var/log/syslog
753M	/mnt/var/log/journal
753M	/mnt/var/log/journal/2eb19d023ec24eea985a37d183b1a168
188G	/mnt/var/log/cups
root@ubuntu:/mnt/var/log#

```

---

### Post by deadflowr on 2022-02-10
See the added link in post#7 and edit your post#8.


That said, wow, cups is huge.
Look at the cups logs
```
ls -lah /mnt/var/log/cups
```
to see what logfile is running away.

Most likely it's the error.log file.

---

### Post by ozark_hillbilly on 2022-02-10
```

root@ubuntu:/mnt/var/log/cups# sudo du --human-readable --max-depth=1 /mnt/var/log/cups/* | sort -h
4.0K	/mnt/var/log/cups/access_log.1
4.0K	/mnt/var/log/cups/access_log.2.gz
4.0K	/mnt/var/log/cups/access_log.3.gz
4.0K	/mnt/var/log/cups/access_log.4.gz
4.0K	/mnt/var/log/cups/access_log.5.gz
4.0K	/mnt/var/log/cups/access_log.6.gz
4.0K	/mnt/var/log/cups/access_log.7.gz
4.0K	/mnt/var/log/cups/error_log.1
4.0K	/mnt/var/log/cups/error_log.2.gz
4.0K	/mnt/var/log/cups/error_log.3.gz
4.0K	/mnt/var/log/cups/error_log.4.gz
4.0K	/mnt/var/log/cups/error_log.5.gz
4.0K	/mnt/var/log/cups/error_log.6.gz
4.0K	/mnt/var/log/cups/error_log.7.gz
8.0K	/mnt/var/log/cups/access_log
188G	/mnt/var/log/cups/error_log
root@ubuntu:/mnt/var/log/cups#

```

---

### Post by ozark_hillbilly on 2022-02-10
```

root@ubuntu:/mnt/var/log/cups# sudo du --human-readable --max-depth=1 /mnt/var/log/cups/* | sort -h
4.0K	/mnt/var/log/cups/access_log.1
4.0K	/mnt/var/log/cups/access_log.2.gz
4.0K	/mnt/var/log/cups/access_log.3.gz
4.0K	/mnt/var/log/cups/access_log.4.gz
4.0K	/mnt/var/log/cups/access_log.5.gz
4.0K	/mnt/var/log/cups/access_log.6.gz
4.0K	/mnt/var/log/cups/access_log.7.gz
4.0K	/mnt/var/log/cups/error_log.1
4.0K	/mnt/var/log/cups/error_log.2.gz
4.0K	/mnt/var/log/cups/error_log.3.gz
4.0K	/mnt/var/log/cups/error_log.4.gz
4.0K	/mnt/var/log/cups/error_log.5.gz
4.0K	/mnt/var/log/cups/error_log.6.gz
4.0K	/mnt/var/log/cups/error_log.7.gz
8.0K	/mnt/var/log/cups/access_log
188G	/mnt/var/log/cups/error_log
root@ubuntu:/mnt/var/log/cups#

```
***************************************************
```

root@ubuntu:/mnt/var/log/cups# ls -lah /mnt/var/log/cups
total 188G
drwxrwxr-x  2 root root   4.0K Feb  8 00:00 .
drwxrwxr-x 13 root syslog 4.0K Feb  9 23:05 ..
-rw-rw-r--  1 root adm    4.7K Feb  8 20:22 access_log
-rw-rw-r--  1 root adm    3.4K Feb  8 00:00 access_log.1
-rw-rw-r--  1 root adm     344 Feb  7 13:39 access_log.2.gz
-rw-rw-r--  1 root adm     568 Feb  6 10:11 access_log.3.gz
-rw-rw-r--  1 root adm     349 Feb  5 00:00 access_log.4.gz
-rw-rw-r--  1 root adm     470 Feb  4 00:00 access_log.5.gz
-rw-rw-r--  1 root adm     424 Feb  3 08:14 access_log.6.gz
-rw-rw-r--  1 root adm     461 Feb  2 08:02 access_log.7.gz
-rw-r-----  1 root adm    188G Feb  9 23:06 error_log
-rw-rw-r--  1 root adm     319 Feb  7 17:12 error_log.1
-rw-rw-r--  1 root adm     210 Feb  5 22:37 error_log.2.gz
-rw-rw-r--  1 root adm     171 Feb  2 22:35 error_log.3.gz
-rw-rw-r--  1 root adm     196 Feb  1 21:41 error_log.4.gz
-rw-rw-r--  1 root adm     170 Jan 31 15:52 error_log.5.gz
-rw-rw-r--  1 root adm     197 Jan 29 15:58 error_log.6.gz
-rw-rw-r--  1 root adm     222 Jan 27 15:56 error_log.7.gz
root@ubuntu:/mnt/var/log/cups#

```

---

### Post by ozark_hillbilly on 2022-02-10
I am unable to access sda5 partition; which is the one with no storage space left.
Attached are gPARTED screenshot showing it IS mounted and 
DISKS utility screenshot shows it is NOTmounted and will not allow me to mount it.

??? 

Is it safe to delete the error_log? Or can I even read a file that large?


Is this ok: 

[https://askubuntu.com/questions/923406/error-log-file-size-from-var-log-cups-is-increasing-so-much-70gb](https://askubuntu.com/questions/923406/error-log-file-size-from-var-log-cups-is-increasing-so-much-70gb)

```

sudo service cups stop
sudo rm /etc/cups/subscriptions.conf*
sudo rm -r /var/cache/cups
sudo service cups start

```
edit -

I went ahead and did this:

```

root@ubuntu:/mnt/var/log/cups# sudo service cups stop
Warning: Stopping cups.service, but it can still be activated by:
  cups.path
  cups.socket
root@ubuntu:/mnt/var/log/cups# sudo rm /etc/cups/subscriptions.conf*
root@ubuntu:/mnt/var/log/cups# sudo rm -r /var/cache/cups
root@ubuntu:/mnt/var/log/cups# sudo service cups start

root@ubuntu:/mnt/var/log/cups# 
root@ubuntu:/mnt/var/log/cups# ls
access_log    access_log.2.gz  access_log.4.gz  access_log.6.gz  error_log    error_log.2.gz  error_log.4.gz  error_log.6.gz
access_log.1  access_log.3.gz  access_log.5.gz  access_log.7.gz  error_log.1  error_log.3.gz  error_log.5.gz  error_log.7.gz
root@ubuntu:/mnt/var/log/cups# rm error_log
root@ubuntu:/mnt/var/log/cups# ls
access_log    access_log.2.gz  access_log.4.gz  access_log.6.gz  error_log.1     error_log.3.gz  error_log.5.gz  error_log.7.gz
access_log.1  access_log.3.gz  access_log.5.gz  access_log.7.gz  error_log.2.gz  error_log.4.gz  error_log.6.gz
root@ubuntu:/mnt/var/log/cups# 

```
Getting ready to reboot....?????

---

### Post by ozark_hillbilly on 2022-02-10
System came up after reboot!

But I am concerned after running that series of commands mentioned in my previous response 
 that this error_log will start its crap again. Can I disable it even if it affects my printing abilities?

I am getting error messages on the desktop that asks if I want to report them. Is there a way
to see what these messages are?

That file is growing again:
```

ed@ed-G41MT-S2PT:/var/log/cups$ ls -lah
total 4.1G
drwxrwxr-x  2 root root   4.0K Feb 10 13:33 .
drwxrwxr-x 13 root syslog 4.0K Feb 10 13:33 ..
-rw-rw-r--  1 root adm    4.7K Feb  8 20:22 access_log
-rw-rw-r--  1 root adm    3.4K Feb  8 00:00 access_log.1
-rw-rw-r--  1 root adm     344 Feb  7 13:39 access_log.2.gz
-rw-rw-r--  1 root adm     568 Feb  6 10:11 access_log.3.gz
-rw-rw-r--  1 root adm     349 Feb  5 00:00 access_log.4.gz
-rw-rw-r--  1 root adm     470 Feb  4 00:00 access_log.5.gz
-rw-rw-r--  1 root adm     424 Feb  3 08:14 access_log.6.gz
-rw-rw-r--  1 root adm     461 Feb  2 08:02 access_log.7.gz
-rw-r-----  1 root adm    4.1G Feb 10 13:53 error_log
-rw-rw-r--  1 root adm     319 Feb  7 17:12 error_log.1
-rw-rw-r--  1 root adm     210 Feb  5 22:37 error_log.2.gz
-rw-rw-r--  1 root adm     171 Feb  2 22:35 error_log.3.gz
-rw-rw-r--  1 root adm     196 Feb  1 21:41 error_log.4.gz
-rw-rw-r--  1 root adm     170 Jan 31 15:52 error_log.5.gz
-rw-rw-r--  1 root adm     197 Jan 29 15:58 error_log.6.gz
-rw-rw-r--  1 root adm     222 Jan 27 15:56 error_log.7.gz
ed@ed-G41MT-S2PT:/var/log/cups$ 

```

 What the heck? This is a real PITA....

edit:

tried to run those same commands again but this time they were aborted:
```

ed@ed-G41MT-S2PT:/var/log/cups$ sudo rm /etc/cups/subscriptions.conf*
sudo: error in /etc/sudo.conf, line 0 while loading plugin "sudoers_policy"
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins
ed@ed-G41MT-S2PT:/var/log/cups$

```
edit 2:

now I cannot execute nautilus as superuser:
```

ed@ed-G41MT-S2PT:/var/log/cups$ sudo nautilus
sudo: error in /etc/sudo.conf, line 0 while loading plugin "sudoers_policy"
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins
ed@ed-G41MT-S2PT:/var/log/cups$ 

```
????

---

### Post by deadflowr on 2022-02-10
Try disable logging in /etc/cups/cupsd.conf
Change the LogLevel from warn to none

Then restart cups, perhaps reboot the system.

After that you can look at the logs that have been generated to determine what was happening.

Probably run
```
tail /var/log/cups/error.log
```
tail will output the last 10 lines, if you need more run
```
tail -n 100 /var/log/cups/error.log
```
which will output the last 100 lines which is probably enough to truly understand what was happening.


Please go back and edit your posts and follow the link I posted in post #7.

---

### Post by ozark_hillbilly on 2022-02-10
Sorry I am a neophyte at Linux:

"Try disable logging in /etc/cups/cupsd.conf"

How is that achieved?

Here is what is filling up error_log unbelievably fast:
```

File \ "usr/lib/cups/notifier/dbus\ " has insecure permissions (0100775/uid = 0/ gid=0."

```

All previous posts are now [code] correct. Sorry 'bout that.

---

### Post by deadflowr on 2022-02-10
Seems oddly common with a simple solution to change the permissions like so
```
sudo chmod 755 /usr/lib/cups/notifier/dbus
```
and double check that it's owned by root with root group, or run just a chown like
```
sudo chown root:root /usr/lib/cups/notifier/dbus
```

See if that helps. 
Although, if you disable logging or set to none it should have already stopped.

---

### Post by ozark_hillbilly on 2022-02-10
```

ed@ed-G41MT-S2PT:/var/log/cups$ sudo rm error_log
sudo: error in /etc/sudo.conf, line 0 while loading plugin "sudoers_policy"
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins
ed@ed-G41MT-S2PT:/var/log/cups$ sudo chmod 755 /usr/lib/cups/notifier/dbus
sudo: error in /etc/sudo.conf, line 0 while loading plugin "sudoers_policy"
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins
ed@ed-G41MT-S2PT:/var/log/cups$

```

Without superuser permissions I cannot do any of these suggestions you are providing.
This is very frustrating.
And how do I disable logging?
I am desperate without su abilities. Can I remove CUPS with synaptic as a temporary fix to keep this file from growing?
Error log is now 25 G.... its a ravenous monster. I guess I need to shut down the computer soon.

edit -

```

ed@ed-G41MT-S2PT:/var/log/cups$ su root
Password: 
root@ed-G41MT-S2PT:/var/log/cups# sudo chmod 755 /usr/lib/cups/notifier/dbus
sudo: error in /etc/sudo.conf, line 0 while loading plugin "sudoers_policy"
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins
root@ed-G41MT-S2PT:/var/log/cups# 

```

edit 2:

/etc/sudo.conf file is not shown in folder:

```

root@ed-G41MT-S2PT:/etc# ls
acpi                           gtk-3.0              perl
adduser.conf                   hddtemp.db           pki
alsa                           hdparm.conf          pm
alternatives                   host.conf            pnm2ppa.conf
anacrontab                     hostid               polkit-1
apache2                        hostname             popularity-contest.conf
apg.conf                       hosts                ppp
apm                            hosts.allow          profile
apparmor                       hosts.deny           profile.d
apparmor.d                     hp                   protocols
apport                         ifplugd              pulse
appstream.conf                 ImageMagick-6        python3
apt                            init                 python3.8
avahi                          init.d               rc0.d
bash.bashrc                    initramfs-tools      rc1.d
bash_completion                inputrc              rc2.d
bash_completion.d              insserv.conf.d       rc3.d
bindresvport.blacklist         inxi.conf            rc4.d
binfmt.d                       iproute2             rc5.d
bluetooth                      issue                rc6.d
brlapi.key                     issue.net            rcS.d
brltty                         kernel               resolv.conf
brltty.conf                    kernel-img.conf      rmt
ca-certificates                kerneloops.conf      rpc
ca-certificates.conf           ldap                 rsyslog.conf
ca-certificates.conf.dpkg-old  ld.so.cache          rsyslog.d
calendar                       ld.so.conf           rygel.conf
chatscripts                    ld.so.conf.d         sane.d
chromium                       legal                security
compizconfig                   libao.conf           selinux
console-setup                  libaudit.conf        sensors3.conf
cracklib                       libblockdev          sensors.d
cron.d                         libnl-3              services
cron.daily                     libpaper.d           sgml
cron.hourly                    libreoffice          shadow
cron.monthly                   lighttpd             shadow-
crontab                        locale.alias         shells
cron.weekly                    locale.gen           skel
cups                           localtime            snmp
cupshelpers                    logcheck             speech-dispatcher
dbus-1                         login.defs           ssh
dconf                          logrotate.conf       ssl
debconf.conf                   logrotate.d          subgid
debian_version                 lsb-release          subgid-
default                        ltrace.conf          subuid
deluser.conf                   machine-id           subuid-
depmod.d                       magic                sudoers
dhcp                           magic.mime           sudoers.d
dictionaries-common            mailcap              sysctl.conf
dpkg                           mailcap.order        sysctl.d
e2scrub.conf                   manpath.config       systemd
emacs                          mime.types           terminfo
environment                    mke2fs.conf          thermald
environment.d                  modprobe.d           timezone
ethertypes                     modules              tmpfiles.d
firefox                        modules-load.d       ubuntu-advantage
fonts                          mtab                 ucf.conf
fprintd.conf                   mtools.conf          udev
fstab                          mysql                udisks2
fuse.conf                      nanorc               ufw
fwupd                          netplan              update-manager
gai.conf                       network              update-motd.d
gamemode.ini                   networkd-dispatcher  update-notifier
gdb                            NetworkManager       UPower
gdm3                           networks             usb_modeswitch.conf
geoclue                        newt                 vim
ghostscript                    nsswitch.conf        vtrgb
glvnd                          openvpn              vulkan
gnome                          opt                  wgetrc
groff                          os-release           wpa_supplicant
group                          PackageKit           X11
group-                         pam.conf             xattr.conf
grub.d                         pam.d                xdg
gshadow                        papersize            xml
gshadow-                       passwd               zsh_command_not_found
gss                            passwd-
gtk-2.0                        pcmcia
root@ed-G41MT-S2PT:/etc# 

```

???

---

### Post by #&amp;thj^% on 2022-02-10
[QUOTE=ozark_hillbilly;14080479
now I cannot execute nautilus as superuser:
```

ed@ed-G41MT-S2PT:/var/log/cups$ sudo nautilus
sudo: error in /etc/sudo.conf, line 0 while loading plugin "sudoers_policy"
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins
ed@ed-G41MT-S2PT:/var/log/cups$ 

```
????[/QUOTE]

I'm sure you know this is a very very bad thing:
```
sudo nautilus
```
I suspect this has something to do with your lack of permissions now. :(
If GUI is needed then a proper way would be with "sudo -H application"
```
ls -a
.              .cache     Downloads      .local    .profile                   .Xauthority
..             .config    .gnupg         .mozilla  Public                     .Xdefaults
.bash_history  Desktop    .gtkrc-2.0     Music     .sudo_as_admin_successful  .xscreensaver
.bash_logout   .dmrc      .ICEauthority  Pictures  Templates                  .xsession-errors
.bashrc        Documents  .kde           .pki      Videos                     .xsession-errors.old
]
```
And:
```
$ stat .Xauthority
  File: .Xauthority
  Size: 76              Blocks: 8          IO Block: 4096   regular file
Device: 803h/2051d      Inode: 786466      Links: 1
Access: (0600/-rw-------)  Uid: ( 1000/      me)   Gid: ( 1000/      me)
Access: 2022-02-10 13:45:40.216000000 -0700
Modify: 2022-02-10 13:45:40.116000000 -0700
Change: 2022-02-10 13:45:40.116000000 -0700
 Birth: 2022-02-10 13:45:40.116000000 -0700

```
Maybe give them a check.
Late for the party here so sorry if I missed something already posted.

---

### Post by ozark_hillbilly on 2022-02-10
I am pretty pissed with Linux/Ubuntu right now. I am unsure why I should stick with it; MicroSoft while inferior does not require near the attention nor expertise. I just did my 2nd fresh install in two weeks and hope my backup is still there.
Due to no fault of my own there is a monster residing in the OS generating an error message at the rate of about 2 GB per hour. And I cannot stop it despite my best efforts. If it starts again with this install I am done with Linux. How the developers expect average computer users to deal with these mysterious issues that require an indepth understanding of Linux file structures and numerous terminal commands is beyond me. I am frustrated because I want to do other things with the computer besides babysit processes gone wild. And I know this is an ongoing issue because others have had the same experience.
Sorry to unload on you.
Now I have to start checking for that error_log file to see if it is going to go beserk again. I do not understand why a straight forward fix action is not available. I thought deleting CUPS through Synaptic Package Manager would stop it but I still had the sudo access problem. I can't win.
If you have straightforward advice on killing these error messages (that got to 189 GIGABYTE in size) for good I am all ears. Why would developers not stop a process like that that jepoardizes system functionality? It makes no sense.

I need a big glass of wine...lol

---

### Post by #&amp;thj^% on 2022-02-10
We Have all been here, I can relate to your frustration, and I come in peace. :)
Show us this please:
```
systemctl status cups

```
Mine:
```
$ systemctl status cups
&#9679; cups.service - CUPS Scheduler
     Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2022-02-10 13:45:29 MST; 2h 10min ago
TriggeredBy: &#9679; cups.path
             &#9679; cups.socket
       Docs: man:cupsd(8)
   Main PID: 647 (cupsd)
     Status: "Scheduler is running..."
      Tasks: 1 (limit: 4702)
     Memory: 8.3M
        CPU: 39ms
     CGroup: /system.slice/cups.service
             &#9492;&#9472;647 /usr/sbin/cupsd -l

Feb 10 13:45:29 me-Standard-PC-i440FX-PIIX-1996 systemd[1]: Starting CUPS Scheduler...
Feb 10 13:45:29 me-Standard-PC-i440FX-PIIX-1996 systemd[1]: Started CUPS Scheduler.

```
If running you will need to stop or disable it to remove anything related to CUPS.
Now after:
```
systemctl stop cups
``` 
Result:
```
$ systemctl status cups
&#9675; cups.service - CUPS Scheduler
     Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: enabled)
     Active: inactive (dead) since Thu 2022-02-10 15:59:56 MST; 6s ago
TriggeredBy: &#9675; cups.path
             &#9675; cups.socket
       Docs: man:cupsd(8)
    Process: 647 ExecStart=/usr/sbin/cupsd -l (code=exited, status=0/SUCCESS)
   Main PID: 647 (code=exited, status=0/SUCCESS)
     Status: "Scheduler is running..."
        CPU: 45ms

Feb 10 13:45:29 me-Standard-PC-i440FX-PIIX-1996 systemd[1]: Starting CUPS Scheduler...
Feb 10 13:45:29 me-Standard-PC-i440FX-PIIX-1996 systemd[1]: Started CUPS Scheduler.
Feb 10 15:59:56 me-Standard-PC-i440FX-PIIX-1996 systemd[1]: Stopping CUPS Scheduler...
Feb 10 15:59:56 me-Standard-PC-i440FX-PIIX-1996 systemd[1]: cups.service: Deactivated successfully.
Feb 10 15:59:56 me-Standard-PC-i440FX-PIIX-1996 systemd[1]: Stopped CUPS Scheduler.
me@me-Standard-PC-i440FX-PIIX-1996:~$ 

```
Good Luck

---

### Post by ozark_hillbilly on 2022-02-10
I am still restoring my system with Deja Dup. I will check those items you asked about. Check back in a little while please. Thanks.


edit - I believe all this crap started when I printed out a C++ file to a Brother wifi printer four or five days ago. Is this possible?

---

### Post by #&amp;thj^% on 2022-02-10
> **ozark_hillbilly said:**
> I am still restoring my system with Deja Dup. I will check those items you asked about. Check back in a little while please. Thanks.





That's Ok I'm charging you by the minute....:lolflag:
> **ozark_hillbilly said:**
> 
edit - I believe all this crap started when I printed out a C++ file to a Brother wifi printer four or five days ago. Is this possible?



Heavens Yes, I think you found your gremlin.:KS

---

### Post by ozark_hillbilly on 2022-02-10
I wanted to install chromium but the install hung up with that SNAP crap.....just stopped. Now I am trying to get rid of it and start anew.....sheesh... I guess I will use my wifes notebook and try to check what you want and leave chromium til another day....

---

### Post by ozark_hillbilly on 2022-02-10
How do I avoid this printer error generation problem going forward? Can I stop the  logging of those messages into error_log? 
. I have no need for it anyway. Is there a way to load Chromium w/o involving SNAP?

Per request:

```

ed@ed-G41MT-S2PT:~$ ls -a
 .                        .bashrc      .gnupg                                   .oracle_jre_usage           Templates
 ..                       .cache       google-chrome-stable_current_amd64.deb   Pictures                    .thunderbird
 AAArduino                .config      .java                                    .pki                       'UNO Web Client Sketch'
 A.arduino15              .cups        Jokes                                    .profile                    Videos
 Arduino                  Desktop      .jssc                                    Public                      .wget-hsts
'Arduino install error'   Documents    .local                                  'Raspberry Pi'
'Arduino Install Point'   Downloads    .mozilla                                 snap
 .bash_history            get-pip.py   Music                                    .ssh
 .bash_logout             .gnome      'Old Misc Files & Folders'                .sudo_as_admin_successful
ed@ed-G41MT-S2PT:~$ stat .Xauthority
stat: cannot stat '.Xauthority': No such file or directory
ed@ed-G41MT-S2PT:~$ 


```

---

### Post by #&amp;thj^% on 2022-02-10
Please see post #20
Then I would clear any pending print jobs.
FWIW >>> **_systemctl stop cups_** will only last until a reboot.
If you need more than 'Stop' then use 'disable'
EG:
```
systemctl disable cups
```
after you have your problem fixed:
 ```
systemctl enable cups
```
To have your print service again.
EDIT: for your other problem
```
$ apt search** chromium-browser**
Sorting... Done
Full Text Search... Done
chromium-browser/impish 1:85.0.4183.83-0ubuntu2 amd64
  Transitional package - chromium-browser -> chromium snap

chromium-browser-l10n/impish,impish 1:85.0.4183.83-0ubuntu2 all
  Transitional package - chromium-browser-l10n -> chromium snap

```
So:
```
sudo apt install chromium-browser

```
If it locks again try:
```
sudo service snapd restart

```

---

### Post by ozark_hillbilly on 2022-02-10
Thanks for CUPS stop info.!!!  So do I need to watch any particular files to know if an error_log is building up a large file w/o my knowledge? There are no files currently under /var/log/cups.


Any ideas why Chromium-browser refuses to load:

```

ed@ed-G41MT-S2PT:~$ sudo apt install chromium-browser
[sudo] password for ed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  chromium-browser
0 upgraded, 1 newly installed, 0 to remove and 213 not upgraded.
Need to get 0 B/48.3 kB of archives.
After this operation, 164 kB of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 180560 files and directories currently installed.)
Preparing to unpack .../chromium-browser_1%3a85.0.4183.83-0ubuntu0.20.04.2_amd64.deb ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing archive /var/cache/apt/archives/chromium-browser_1%3a85.0.4183.83-0ubuntu0.20.04.2_amd64.deb (--unpack):
 new chromium-browser package pre-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/chromium-browser_1%3a85.0.4183.83-0ubuntu0.20.04.2_amd6
4.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ed@ed-G41MT-S2PT:~$ 

```

---

### Post by TheFu on 2022-02-10
Errors being logged is a hint that something is very wrong.  Fix the error.
If you don't want to do that, disable cups.
```

sudo systemctl stop cups
sudo systemctl disable cups
sudo systemctl mask cups
```

Those three commands will 
stop it, prevent it from restarting, then make it so it won't restart at boot.
Now, go look at the cups error.log and figure out what the issue is.

Snaps tend to be bloated. You many not want to use those unless you specifically WANT to use one or 5 of them.  In the software install application, I understand the icon or something there is a little different for Snap packages.  By default, I think 3 copies of every snap application are retained.  You can change that to 1 extra using a command like this:
```
sudo snap set system refresh.retain=2
```

You can also prevent the snap system from checking for updates 4x a day by using this command:
```
sudo snap set system refresh.timer=sat
```

To remove all the old versions of snaps (these aren't being used), 
```
#!/bin/bash
# Removes old revisions of snaps
# CLOSE ALL SNAPS BEFORE RUNNING THIS
set -eu

snap list --all | awk '/disabled/{print 1, 3}' |
while read snapname revision; do 
   [COLOR="#FF0000"]echo[/COLOR] sudo snap remove "snapname" --revision="revision"
done 
```
That's a script, so you'll want to copy it somewhere to be run, chmod +x that script file, then run it.  It will print out some commands that you can run to remove specific snaps.  If you just want it to remove them already, remove the "echo" (in red)

For log files, we can control how large they can get using some settings. Those are in: /etc/systemd/journald.conf
There is a manpage for journald.conf which explains every setting in that file. Use **sudoedit /etc/systemd/journald.conf** to edit systems files, like journald.conf.  I limit file sized, the number of files and how quickly entries can be added using journald.conf settings.  This is one area where the defaults really aren't sufficient post-install.

How large all the log files are allowed to become can be controlled. Here's mine on a pseudo-desktop: 
```
$ journalctl --disk-usage
Archived and active journals take up 1.5G in the file system.

```

As 1fallen says, using sudo to run a GUI program is dangerous and bad form. There are usually unintended side-effects. Mostly because GUI programs like to write to config files without asking first, so if the files don't exist and perhaps the directory for those files doesn't exist either, the program will happily create the directories and files as needed ... with root:root as the owner and group.  Now, your normal userid will try to access those files, but be denied. No settings and many Gnome programs will just crash.  So, if the DE startup is trying to read those files ... and cannot ... expect to be kicked out of the login process.  In short, it isn't good. The easy answer is "don't use sudo with GUI programs", so that is what we preach.

---

### Post by #&amp;thj^% on 2022-02-10
> **TheFu said:**
> The easy answer is "don't use sudo with GUI programs", so that is what we preach.

Can I hear a Amen. :popcorn:
Another nice post, with clarity.

---

### Post by TheFu on 2022-02-10
> **1fallen said:**
> Can I hear a Amen. :popcorn:

Testify!

---

### Post by #&amp;thj^% on 2022-02-10
> **ozark_hillbilly said:**
> Thanks for CUPS stop info.!!!  So do I need to watch any particular files to know if an error_log is building up a large file w/o my knowledge? There are no files currently under /var/log/cups.


Any ideas why Chromium-browser refuses to load:

```

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing archive /var/cache/apt/archives/chromium-browser_1%3a85.0.4183.83-0ubuntu0.20.04.2_amd64.deb (--unpack):
 new chromium-browser package pre-installation script subprocess returned error exit status 1
[COLOR="#FF0000"]Errors were encountered while processing:
 /var/cache/apt/archives/chromium-browser_1%3a85.0.4183.83-0ubuntu0.20.04.2_amd6
4.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
ed@ed-G41MT-S2PT:~$ 

```
 Not sure but try:
```
sudo apt -f install
```

---

### Post by ozark_hillbilly on 2022-02-10
Appreciate all the helpful info. !!!!

Should the CUPS error log always be generated under /var/log/cups?
Currently there is not one which I hope remains true. That error_log (189 GB) cost me a fresh install (twice) 
as I am a just a Linux neophyte who was too ignorant to know where to look for a problem. :(

---

### Post by #&amp;thj^% on 2022-02-10
CUPS creates a few log files in the default logs directory (normally /var/log/cups/ for Ubuntu, Debian)
Don't beat yourself, happens to best of us, different problems are always New and unknown to us, until our ability's grow there remains a certain frustration level in the learning curve.
 Regards

---

### Post by ozark_hillbilly on 2022-02-10
Chromium did download after snap restart command you suggested but when you click on icon 
the small movement icon spins for a few secs and stops without browser coming up.

```

ed@ed-G41MT-S2PT:/$ chromium
ERROR: not connected to the gnome-3-38-2004 content interface.
ed@ed-G41MT-S2PT:/$ 


```

---

### Post by TheFu on 2022-02-10
> **ozark_hillbilly said:**
> Appreciate all the helpful info. !!!!

Should the CUPS error log always be generated under /var/log/cups?
Currently there is not one which I hope remains true. That error_log (189 GB) cost me a fresh install (twice) 
as I am a just a Linux neophyte who was too ignorant to know where to look for a problem. :(

If you learn to use journalctl, you don't need to know where the logs are.  Systemd's Journal logging is 1 of the bright things that systemd did.  You can ask journalclt to show log information - 1 subsystem, all errors, last boot, 5 boots ago ... lots of ways to ask questions, if you learn how.  If you are new, I'd jump to learning journalctl and not bother with the older logs which are actually replicated out of the systemd logging system for the old-timers like me to use.

You can limit how large a log is allowed to be. See my post above for hints.

---

### Post by ozark_hillbilly on 2022-02-10
Thanks! I will definitely explore journalctl as I had no idea about its use. Is there a good Linux book that cover the common pitfalls neophytes users like myself experience.
I operate in the Linux environment by treading water and lack the considerable skills someone like a systems analyst would possess. Most ordinary computer users would never
venture into terminal mode but I have to try up to a point. I will be 65 in a few weeks so I know about old timers and my first Sinclair Z-80 back in the 80s. Lol.

---

### Post by TheFu on 2022-02-10
You aren't that much older than I and lots of the people here are older than you.  BTW, I lived 6 yrs in Ark - NE on the fault for 3 and N. LR for the other 3.

The reason we use CLI commands so much in these forums is because there are lots of different GUIs and capturing all the different screen shots, then posting them and linking them all together with words for what to see and what to click is much harder than providing a command that will always work on any Ubuntu desktop or server, 100%.

Not everything that Canonical has decided to do is good for new users ... or long-time admins either.  I think snaps are an abomination. Their goals were good, but the implementation isn't a good as the 2 competing solutions.  Read that Lubuntu is not using snaps and has selected one of the competing solutions for that specific problem. I never had any issues that the snap-hammer would solve better, so I avoid them almost always. I've also found that on the 1 or 2 systems where I allow snaps to be used, about 80% of the time, snap packages refuse to work. I have some setups that Canonical would call "non-standard.", but they are very much how an enterprise would setup desktops where users can sit at any seat, then login and have the computer appear to be "theirs", just by logging in. For decades, this has worked fine. It is only the snap packages which don't work.  Still, not a typical home, desktop, user, so Canonical does have a point.

My next desktop install won't be Ubuntu. It is that bad for me.  For servers, I'm still deciding. Fortunately, with Linux, we have lots and lots of choice.

As for a beginner friendly book ... there are lots.  Don't buy anything. These are all free.  

Find the **Ubuntu Desktop Guide**. This will mostly be about GUI point-n-click stuff. Find the version for your OS release (lsb_release -a) and the DE (Desktop Environment) you prefer.  There are about 10 popular DEs.  **inxi -Fzz** will show an overview of your system as it is today. Including the DE, GPU, HDDs, CPU, RAM, ... that is handy information to know.  Saying "20.04" isn't exact enough if you want GUI instructions. Different DEs have different GUI programs.  Plus, I think GUI programs only provide access to about 20% of the OS. The real power comes from the CLI and from automating things or taking things you do over and over, putting them into a script.  Now when you want these 10 things to happen, you just cause 1 script to run.

Always remember that the GUI is just another program. It is nothing special in Unix-like systems. GUIs follow the same UNIX permissions model that every other program has to follow. While it may appear that sudo is like the "elevate privilege" on MS-Windows, but it is not. The way to learn this is to pull back the GUI stuff and learn the CLI.

The other way to gain knowledge is to get the basic understanding from a non-GUI standpoint.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a reasonable book to learn the underlying way the OS is setup, organized and why things work in specific ways.  There is a simple elegance to the UNIX permissions model. It is all based on file permissions.  In all UNIX-like OSes, there are only 2 type of things.  Processes and files.  You may have heard that "everything is a file", which isn't strictly true, but almost everything is a file, unless it is a process.  All files have an owner, a group, and permissions.  That is the basis for all UNIX security and access rights.  

A file is a file.
A directory is a file.
The keyboard is a file.
The disk partition is a file.
The disk is a file.
The monitor is a file.
All connected devices to the computer are files.
And we've learned that access to read, write and execute files all comes from the owner, group and permissions on those files.

Processes originate by running a file. When a process is started, there is an effective userid and an effective groupid.  Those 2 things determine which "files" the process can access and how that access may or may not be limited.  When a normal user runs a program, that program inherits their userid and groupid just after being loaded into allocated into memory and finally the instruction pointer is set to the 1st instruction of the program and told "run".  That process can only access stuff that the userid and groupid they are running under.

Anyway, I'm sure the book that I put in the link above will explain it better.  Work through 1 chapter each week and in 2 months, things will be easier and connections will start "clicking" for why things work the way they do.  Then you'll be able to use your brain to know which things are a bad idea.  But nothing can replace experience.

---

### Post by linux-sysop on 2022-02-11
Ouch! Snap is just  horrid to smallish hard drives.  I never use it and it is one of the first apps I remove from any distribution.  

Both Snapcraft and Flatpak are billed as ***package managers***, but I call them bloatware.  I suggest you open filemanager and go to the folder /snap  and right click to view the folder size.  I bet this is pretty huge?  Snap downloads the OS and other dependencies for the program you request.  Nothing wrong with being complete, correct?  Wrong, here is why.

Using; **snap install hedgewars **
This also installed a core18 and a KDE frame work. Total 2 GB of files.


Using; **apt install hedgewars**
Need to get 158 MB of archives.
After this operation, 202 MB of additional disk space will be used.

 Adding a tiny 202 MB game, Snap consumed 1.8 more GB of resources from the hard drive just to be sure it didn't forget something.

---

### Post by TheFu on 2022-02-11
Snaps do take more space, but they do share the core libraries, so we don't need to have 5 copies of Qt or GTK+ libraries if there are 5 snaps using them.  They will share the same version.  But we don't need 3 copies, just the latest as provided through dependency lists of each snap.

202MB is extreme bloat in my book - forget about all the extra stuff. I suppose large programs need lots of space.
For example, I use freemind. This is a java program. Java is known to be bloated (size and ram) and often runs really slow.
```
$ snap info freemind
```
shows 
```
  latest/stable:    1.1.0-Beta-2 2019-07-12 (4) [COLOR="#FF0000"]165MB[/COLOR] -
```
The entire JRE is included.

```
$ snap info chromium
...
refresh-date: 6 days ago, at 00:03 EST
channels:
  latest/stable:    98.0.4758.80 2022-02-07 (1899) [COLOR="#FF0000"]141MB[/COLOR] -

```
In 20.04, chromium became a snap-only install if the Canonical stuff is used. There are other ways to get Chromium, outside Canonical's repos/snaps.  That takes extra effort.  Also, I've had problems running chromium on remote systems to be displayed on my current workstation and the snap packaging "protections" prevent my ability to use firejail, which I'm not happy about. I find the constraints provided by snaps to be insufficient for my "dangerous use" browser. That's my reason for using Chromium. I need to run it in a mode that doesn't allow any access to any storage. The snap constraints get in the way of the other tool I use, firejail, to gain that functionality.

---

### Post by ozark_hillbilly on 2022-02-11
Again, I appreciate the heads up information you are sharing. I have a friend who uses MX Linux. Are you familiar with that distribution?

---

### Post by TheFu on 2022-02-11
> **ozark_hillbilly said:**
> Again, I appreciate the heads up information you are sharing. I have a friend who uses MX Linux. Are you familiar with that distribution?

Some guys in my LUG use MX and love it.  It is not very popular, so you'll need to get support from that person. I would say it isn't really conducive to learn Linux using, but I could be wrong.

---

### Post by linux-sysop on 2022-02-11
> **ozark_hillbilly said:**
> Again, I appreciate the heads up information you are sharing. I have a friend who uses MX Linux. Are you familiar with that distribution?

Nothing wrong with other distros at all, just like when you go get a new suit, you want the right color, cut, and a good fit.

I always recommend people planning to move into Linux, to tryout a few, and learn by installing them on a virtual machine first.  This way, when you know what you like, you already ahead of the curve on how to install it.  Hands down the hardest to install is Arch, if I were to install a Debian based Linux (MX is Debian) I would shoot for Sparky Linux.  They offer minimal build GUI, minimal build no GUI, they have one called GameOver Edition, which as you can guess is geared for gamers.  The only issue I have with Debian is really a "non-issue", most require some minor tweaking to allow for non-free proprietary software.  Frankly I need my Nvidia drivers from Nvidia and this is why I use Ubuntu over Debian.

 MX Linux is for older machines from what I understand.   If you or your friends need a Ubuntu version, [LXLE]("https://www.lxle.net") is noted for being an extremely light weight OS.   Their webpage motto "Revive that old PC!" about says it all.  Although **I don't know about the support** as they seem to have stalled, and many of the users on their forums are questioning about the future of their 32 bit support.  Everything moves ahead, but really why would you need to upgrade 32 bit machines?  I am finding 64 bit i5-core PCs in the city garbage.

Note: Debian was the root OS for Unbuntu distribution. Debian was named for its creators Deb and her husband Ian Murdock, while Ubuntu is named for a philosophy of South African Bantu people, the belief in a universal bond of sharing connects all of humanity.

---

### Post by ozark_hillbilly on 2022-02-12
Thanks again...

---

