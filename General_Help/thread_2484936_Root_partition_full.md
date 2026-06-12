---
title: "Root partition full"
date: 2023-03-14
forum: General Help
---

### Post by john-m-kane on 2023-03-14
Hi,
since some time my root partition on Ubuntu is continuously getting full with no apparent reason ( I'm not installing new software ). I looked online but I found only some fixes like to clean the apt cache but it does not seem to work.
I had some problem a time ago with a log file that was getting enormous (8GB). I don't know how to fix this problem, could some body help me please.


I leave here the output of some commands that may be useful.


```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           1,2G  2,6M  1,2G   1% /run
/dev/nvme0n1p4   33G   31G   86M 100% /
tmpfs           5,8G  509M  5,3G   9% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
/dev/nvme0n1p2   96M   18M   79M  18% /boot/efi
/dev/nvme0n1p6   59G   35G   21G  63% /home
tmpfs           1,2G  268K  1,2G   1% /run/user/1000
/dev/sda2        81G   81G     0 100% /run/timeshift/backup



```


```
$ df -h /
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p4   33G   31G   83M 100% /
```


```
$ sudo du -hsx /* | sort -rh | head -n 40
[sudo] password for patronus: 
du: cannot read directory '/proc/1620/task/1620/net': Invalid argument
du: cannot read directory '/proc/1620/net': Invalid argument
du: cannot access '/proc/194556/task/194556/fd/4': No such file or directory
du: cannot access '/proc/194556/task/194556/fdinfo/4': No such file or directory
du: cannot access '/proc/194556/fd/3': No such file or directory
du: cannot access '/proc/194556/fdinfo/3': No such file or directory
35G    /home
19G    /var
9,4G    /usr
1,3G    /opt
263M    /boot
24M    /root
16M    /etc
2,6M    /run
376K    /tmp
112K    /snap
16K    /user
16K    /lost+found
8,0K    /media
4,0K    /srv
4,0K    /mnt
4,0K    /cdrom
0    /sys
0    /sbin
0    /proc
0    /libx32
0    /lib64
0    /lib32
0    /lib
0    /dev
0    /bin



```


In the logs app on ubuntu i have quite a lot of errors listed:

feb 14 02:44:48 kernel: Bluetooth: hci0: Suspend notifier action (3) failed: -110
feb 13 15:34:46 kernel: nvidia-modeset: ERROR: GPU:0: Idling display engine timed out: 0x0000927c:0:0:1128
feb 13 15:34:30 kernel: [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000100] Failed to grab modeset ownership
feb 13 15:34:30 gdm-session-wor: GLib-GObject: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
feb 13 15:34:30 kernel: [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000100] Failed to grab modeset ownership
feb 13 15:34:30 kernel: nvidia-modeset: ERROR: GPU:0: Idling display engine timed out: 0x0000927c:0:0:1128
feb 13 15:34:20 systemd: Failed to start Application launched by gnome-session-binary.
feb 13 15:34:18 kernel: nvidia-modeset: ERROR: GPU:0: Idling display engine timed out: 0x0000927c:0:0:1128
feb 13 15:34:13 systemd: Failed to start Application launched by gnome-session-binary.
feb 13 15:34:06 gdm-session-wor: gkr-pam: unable to locate daemon control file
feb 13 15:33:53 kernel: nvidia-modeset: ERROR: GPU:0: Idling display engine timed out: 0x0000927c:0:0:1128
feb 13 15:33:43 gnome-session-b: GLib-GIO-CRITICAL: g_bus_get_sync: assertion 'error == NULL || *error == NULL' failed
feb 13 15:33:39 canonical-livep: Task "refresh" returned an error: livepatch check failed: POST request to "https://livepatch.canonical.com/v1/client/b7e53a7ae4aa49659be80ea030d73828/updates" failed, retrying in 30s.
feb 13 15:33:36 kernel: 
feb 13 15:33:35 kernel: ACPI Error: Aborting method \_PR.CPU7._CPC due to previous error (AE_NOT_FOUND) (20210730/psparse-529)
feb 13 15:33:35 kernel: x86/cpu: SGX disabled by BIOS.



Hope some one can help me :)

---

### Post by Bashing-om on 2023-03-14
Hello john-m-kane

Focusing on the thread title - one thing at a time - your /home and /var directories are huge in comparison to what I show on my sparse system:
> 
1.4G	/home
3.0G	/var


I would in your case be paying attention to what is installed on /home, and if again the logs are running a muck in /var.

[INDENT]7 pounds of sugar in a 5 pound sack ?
[/INDENT]

---

### Post by Impavidus on 2023-03-15
There's a separate /home partition, so that's not the problem. /opt is somewhat large-ish, but not so bad that that would be the problem.

Focus on /var. That's where log files and snaps get stored and both of them can get big. So dig a little deeper into /var. Which directories in /var are so large? Logs are in /var/log, snaps are in /var/lib/snapd/snaps.

---

### Post by ActionParsnip on 2023-03-15
what is the output of:
```

sudo du -sh /var/*

```

---

### Post by TheFu on 2023-03-15
Let's start by seeing how much space logs are using:
```
journalctl --disk-usage   # See log file disk use
sudo journalctl --vacuum-size=200M    # Drop log file size to 200M, if possible.

```
If it is over 500M, use the 2nd command.  This is just a quick fix for logs. It doesn't solve the issue.  To do that, you need to look at the logs to see what's causing the growth.  You can set limits for how large the logs are allowed to grow.


However, 33G is tight for Ubuntu 20.04 and later releases.  35G is my minimal for / on desktops and that has /var and /home on separate partitions. Also, I don't use a swapfile. I use a swap partition.

And if you use lots of snap packages, these can take up huge amounts of storage in /var/.  3 copies of each snap are retained, by default.  You can remove the unused snaps that would free 2/3rds of the snap storage used.
```
sudo snap set system refresh.retain=2

```  [Https://www.linuxuprising.com/2019/04/how-to-remove-old-snap-versions-to-free.html](Https://www.linuxuprising.com/2019/04/how-to-remove-old-snap-versions-to-free.html)

If you use lxd/lxc containers or libvirt virtual machines, by default those get placed in /var/.  The way I solve those issues is by adding extra storage specific to each to the directories where they store their huge stuff.
```
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-lxd--lv     ext4   59G   14G   42G  25% /var/lib/lxd
/dev/mapper/hadar--vg-libvirt--lv ext4  173G  131G   33G  81% /var/lib/libvirt
```
See the far right column?  That is where the storage is mounted directly.

just a few things for your consideration.  Hopefully, it is just the log files in your situation.

---

### Post by john-m-kane on 2023-03-16
> **ActionParsnip said:**
> what is the output of:
```

sudo du -sh /var/*

```


```
sudo du -sh /var/*[sudo] password for patronus: 
13M    /var/backups
194M    /var/cache
4,0K    /var/crash
16K    /var/ipp-usb
16G    /var/lib
4,0K    /var/local
0    /var/lock
2,6G    /var/log
4,0K    /var/mail
4,0K    /var/metrics
4,0K    /var/opt
0    /var/run
7,3M    /var/snap
52K    /var/spool
212M    /var/tmp



```

I just run ```
sudo journalctl --vacuum-size=200M
``` and ```
[COLOR=#000000][FONT=&amp]sudo snap set system refresh.retain=2[/FONT][/COLOR]
``` and also i ran the script at the link suggested by > **TheFu said:**
> Https://www.linuxuprising.com/2019/0...s-to-free.html and the output has changed to:
```
sudo du -sh /var/*13M    /var/backups
194M    /var/cache
4,0K    /var/crash
16K    /var/ipp-usb
14G    /var/lib
4,0K    /var/local
0    /var/lock
285M    /var/log
4,0K    /var/mail
4,0K    /var/metrics
4,0K    /var/opt
0    /var/run
7,2M    /var/snap
52K    /var/spool
212M    /var/tmp



```

I checked in Virtualbox and I had a VM so I deleted it and it's files just to be sure but nothing changed.

Now my disk situation is:

```

df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           1,2G  2,7M  1,2G   1% /run
/dev/nvme0n1p4   33G   27G  4,6G  86% /
tmpfs           5,8G  476M  5,4G   9% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
/dev/nvme0n1p2   96M   18M   79M  18% /boot/efi
/dev/nvme0n1p6   59G   29G   27G  52% /home
tmpfs           1,2G  244K  1,2G   1% /run/user/1000
/dev/sda2        81G   81G     0 100% /run/timeshift/backup

```

```
df -h /
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p4   33G   27G  4,6G  86% /

```

```
sudo du -hsx /* | sort -rh | head -n 40
du: cannot read directory '/proc/1620/task/1620/net': Invalid argument
du: cannot read directory '/proc/1620/net': Invalid argument
du: cannot access '/proc/210645/task/210645/fd/4': No such file or directory
du: cannot access '/proc/210645/task/210645/fdinfo/4': No such file or directory
du: cannot access '/proc/210645/fd/3': No such file or directory
du: cannot access '/proc/210645/fdinfo/3': No such file or directory
29G    /home
15G    /var
9,4G    /usr
1,3G    /opt
263M    /boot
24M    /root
16M    /etc
2,7M    /run
384K    /tmp
112K    /snap
16K    /user
16K    /lost+found
8,0K    /media
4,0K    /srv
4,0K    /mnt
4,0K    /cdrom
0    /sys
0    /sbin
0    /proc
0    /libx32
0    /lib64
0    /lib32
0    /lib
0    /dev
0    /bin

```


Is it normal that Ubuntu 22.04.2 LTS needs so much space?

---

### Post by TheFu on 2023-03-16
sorted ... btw, just pipe the output through '| sort -h'  next time, so we aren't wasting time looking for unimportant stuff.

```
0    /var/lock
0    /var/run
16K    /var/ipp-usb
4,0K    /var/crash
4,0K    /var/local
4,0K    /var/mail
4,0K    /var/metrics
4,0K    /var/opt
52K    /var/spool
13M    /var/backups
7,3M    /var/snap
194M    /var/cache
212M    /var/tmp
[B]16G    /var/lib
2,6G    /var/log[/B]
```
So, only the last 2 lines matter; they are GB sized, not MB or KB.  Did you run the log vacuum command suggested?  2.5G is a bit large for logs.  /var/lib/ can hold all sorts of things.  Run
```
du -sh /var/lib/* | sort -h
```
to see what's important down there.

---

### Post by john-m-kane on 2023-03-16
I updated my previous reply and now it has the before and after of the vacuume command suggested by you, thank you very much now I will be able to shut down my PC knowing that it will come back alive (before i had 0Bytes free so i had to keep my PC in Suspend mode).

the output of the command requested by you is:
```
du -sh /var/lib/* | sort -h
du: cannot read directory '/var/lib/AccountsService/users': Permission denied
du: cannot read directory '/var/lib/apt/lists/partial': Permission denied
du: cannot read directory '/var/lib/avahi-autoipd': Permission denied
du: cannot read directory '/var/lib/bluetooth/34:41:5D:29:76:82': Permission denied
du: cannot read directory '/var/lib/fprint': Permission denied
du: cannot read directory '/var/lib/fwupd/gnupg': Permission denied
du: cannot read directory '/var/lib/gdm3': Permission denied
du: cannot read directory '/var/lib/NetworkManager': Permission denied
du: cannot read directory '/var/lib/openvpn/chroot': Permission denied
du: cannot read directory '/var/lib/polkit-1': Permission denied
du: cannot read directory '/var/lib/private': Permission denied
du: cannot read directory '/var/lib/saned': Permission denied
du: cannot read directory '/var/lib/snapd/cookie': Permission denied
du: cannot read directory '/var/lib/snapd/void': Permission denied
du: cannot read directory '/var/lib/snapd/cache': Permission denied
du: cannot read directory '/var/lib/snapd/snapshots': Permission denied
du: cannot read directory '/var/lib/ubuntu-advantage/apt-esm/var/lib/apt/lists/partial': Permission denied
du: cannot read directory '/var/lib/ubuntu-advantage/private': Permission denied
du: cannot read directory '/var/lib/udisks2': Permission denied
du: cannot read directory '/var/lib/update-notifier/package-data-downloads/partial': Permission denied
0    /var/lib/app-info
0    /var/lib/shells.state
4,0K    /var/lib/acpi-support
4,0K    /var/lib/avahi-autoipd
4,0K    /var/lib/BrlAPI
4,0K    /var/lib/dbus
4,0K    /var/lib/dhcp
4,0K    /var/lib/fprint
4,0K    /var/lib/gdm3
4,0K    /var/lib/geoclue
4,0K    /var/lib/git
4,0K    /var/lib/hp
4,0K    /var/lib/man-db
4,0K    /var/lib/misc
4,0K    /var/lib/NetworkManager
4,0K    /var/lib/polkit-1
4,0K    /var/lib/private
4,0K    /var/lib/python
4,0K    /var/lib/saned
4,0K    /var/lib/snmp
4,0K    /var/lib/tpm
4,0K    /var/lib/ubuntu-release-upgrader
4,0K    /var/lib/udisks2
4,0K    /var/lib/update-manager
4,0K    /var/lib/usb_modeswitch
8,0K    /var/lib/apport
8,0K    /var/lib/bluetooth
8,0K    /var/lib/boltd
8,0K    /var/lib/ispell
8,0K    /var/lib/logrotate
8,0K    /var/lib/msttcorefonts
8,0K    /var/lib/openvpn
8,0K    /var/lib/os-prober
8,0K    /var/lib/power-profiles-daemon
8,0K    /var/lib/sudo
8,0K    /var/lib/ubiquity
8,0K    /var/lib/unattended-upgrades
8,0K    /var/lib/vim
8,0K    /var/lib/whoopsie
8,0K    /var/lib/xfonts
8,0K    /var/lib/xkb
12K    /var/lib/locales
12K    /var/lib/plymouth
12K    /var/lib/sgml-base
12K    /var/lib/ubuntu-drivers-common
16K    /var/lib/grub
16K    /var/lib/libreoffice
24K    /var/lib/emacsen-common
24K    /var/lib/shim-signed
24K    /var/lib/update-notifier
28K    /var/lib/alsa
28K    /var/lib/pam
28K    /var/lib/xml-core
32K    /var/lib/dictionaries-common
36K    /var/lib/ghostscript
56K    /var/lib/colord
344K    /var/lib/PackageKit
364K    /var/lib/AccountsService
408K    /var/lib/upower
704K    /var/lib/usbutils
740K    /var/lib/systemd
888K    /var/lib/fwupd
2,6M    /var/lib/dkms
3,3M    /var/lib/command-not-found
3,5M    /var/lib/ucf
3,6M    /var/lib/ubuntu-advantage
4,1M    /var/lib/aspell
15M    /var/lib/aptitude
21M    /var/lib/swcatalog
85M    /var/lib/dpkg
209M    /var/lib/apt
4,7G    /var/lib/snapd
6,4G    /var/lib/flatpak

```

Sorry I think I didn't quite get how to make the ' | sort -h' part work :(

---

### Post by john-m-kane on 2023-03-16
I don't know how but after running the suggested commands and getting 4,9 GB of free space on my root partition I noticed that in the logs app there are a lot less errors in the important category.
I'm not sure if it is caused by the fact that I deleted some 2,2 GB of logs or if they where caused by the lack of root storage and now they're fixed :)?

In the logs app under the important category there are this log listed:
```

mar 16 23:13:20 kernel: nvidia-modeset: ERROR: GPU:0: Idling display engine timed out: 0x0000927c:0:0:1128mar 16 23:12:13 kernel: [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000100] Failed to grab modeset ownership
mar 16 23:12:13 kernel: [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000100] Failed to grab modeset ownership
mar 16 23:12:13 kernel: [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000100] Failed to grab modeset ownership
mar 16 23:12:13 kernel: [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000100] Failed to grab modeset ownership
mar 16 23:12:13 kernel: [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000100] Failed to grab modeset ownership
mar 16 23:10:52 gdm3: GLib: Source ID 243 was not found when attempting to remove it
mar 16 23:10:52 systemd: Failed to start Refresh fwupd metadata and update motd.

```

---

### Post by TheFu on 2023-03-16
Put **sudo** in front of the **du** command and try again. My bad.

```
4,7G    /var/lib/snapd
6,4G    /var/lib/flatpak
```
With what we can see so far, it appears you have a bunch of snap and flatpak packages loaded. These are usually 4-20x larger than the native debian packages, so you might want to reconsider using those new packaging tools.  Think I posted about snap packages using more storage above.  Re-read that section and decide if you want to be more aggressive about having fewer copies.

Long term, I'd say that you might want to connect extra storage specifically for /var/lib/snapd and /var/lib/flatpak.  I showed how I do it for LXD containers and for virtual machines in a post above.  It is a bit nerdy to do that, but sometimes there aren't any great choices.

Just FYI, I use a few aliases in my ~/.bashrc file to make checking out storage easier.
```
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'
alias dut='du -sh'
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'

```
If you add those to the bottom of your ~/.bashrc file, including 1 extra line after, then logout and login, you'll have the aliases available too. The dft and lsblkt commands hide "fake" storage - things that would show up in normal output, but aren't really using any storage.  Seeing only what actually matters is helpful, so we don't waste time looking at unimportant stuff.

---

### Post by john-m-kane on 2023-03-16
The output with sudo added is:
```

sudo du -sh /var/lib/* | sort -h
[sudo] password for patronus: 
0    /var/lib/app-info
0    /var/lib/shells.state
4,0K    /var/lib/acpi-support
4,0K    /var/lib/avahi-autoipd
4,0K    /var/lib/BrlAPI
4,0K    /var/lib/dbus
4,0K    /var/lib/dhcp
4,0K    /var/lib/fprint
4,0K    /var/lib/geoclue
4,0K    /var/lib/git
4,0K    /var/lib/hp
4,0K    /var/lib/man-db
4,0K    /var/lib/misc
4,0K    /var/lib/private
4,0K    /var/lib/python
4,0K    /var/lib/saned
4,0K    /var/lib/snmp
4,0K    /var/lib/tpm
4,0K    /var/lib/ubuntu-release-upgrader
4,0K    /var/lib/udisks2
4,0K    /var/lib/update-manager
4,0K    /var/lib/usb_modeswitch
8,0K    /var/lib/apport
8,0K    /var/lib/boltd
8,0K    /var/lib/ispell
8,0K    /var/lib/logrotate
8,0K    /var/lib/msttcorefonts
8,0K    /var/lib/os-prober
8,0K    /var/lib/power-profiles-daemon
8,0K    /var/lib/sudo
8,0K    /var/lib/ubiquity
8,0K    /var/lib/unattended-upgrades
8,0K    /var/lib/vim
8,0K    /var/lib/whoopsie
8,0K    /var/lib/xfonts
8,0K    /var/lib/xkb
12K    /var/lib/locales
12K    /var/lib/openvpn
12K    /var/lib/plymouth
12K    /var/lib/sgml-base
12K    /var/lib/ubuntu-drivers-common
16K    /var/lib/grub
16K    /var/lib/libreoffice
24K    /var/lib/emacsen-common
24K    /var/lib/shim-signed
24K    /var/lib/update-notifier
28K    /var/lib/alsa
28K    /var/lib/pam
28K    /var/lib/xml-core
32K    /var/lib/dictionaries-common
36K    /var/lib/ghostscript
56K    /var/lib/colord
60K    /var/lib/polkit-1
104K    /var/lib/NetworkManager
344K    /var/lib/PackageKit
368K    /var/lib/AccountsService
408K    /var/lib/upower
704K    /var/lib/usbutils
740K    /var/lib/systemd
908K    /var/lib/fwupd
2,6M    /var/lib/dkms
2,7M    /var/lib/bluetooth
3,3M    /var/lib/command-not-found
3,5M    /var/lib/ucf
3,7M    /var/lib/ubuntu-advantage
4,1M    /var/lib/aspell
15M    /var/lib/aptitude
15M    /var/lib/gdm3
21M    /var/lib/swcatalog
85M    /var/lib/dpkg
233M    /var/lib/apt
6,4G    /var/lib/flatpak
6,7G    /var/lib/snapd

```

I will try to gradually switch to flatpack and extend my root partition given that if I have understood correctly my current is quite small.

Thank you very much for your help. If you think some thing more can be done let me know otherwise i'll mark the thread as solved :)

---

### Post by TheFu on 2023-03-17
"Quite small" is subjective.  For a desktop, since 20.04, the OS has become massively bloated due to some choices Canonical has made. I can understand why they would make those choices, even if I disagree and prefer to have a system that runs well on 8GB of storage. Sadly, newer == more bloated almost always. Ubuntu isn't any different than other OSes in that regard.

BTW, when you post stuff ... the more junk that gets posted detracts from what's important.  Showing 60 lines of storage amounts when it is sorted detracts from the last 5 lines, which are the only ones that have any bearing at all.  You could have posted something like this:
```
$ sudo du -sh /var/lib/* | sort -h
...
3,7M    /var/lib/ubuntu-advantage
4,1M    /var/lib/aspell
15M    /var/lib/aptitude
15M    /var/lib/gdm3
21M    /var/lib/swcatalog
85M    /var/lib/dpkg
233M    /var/lib/apt
6,4G    /var/lib/flatpak
6,7G    /var/lib/snapd
```
and conveyed more than enough information.
BTW, we can reverse the sort using **sort -rh**. Then the largest would be at the top.  "-h" when it doesn't mean "help" often means "human" ... as in *human readable* or sorted *like a human would*.  *sort -h* tells sort to think of G as larger than M as larger than K - like a human would.  
For the **du** command above, the -h is human readable.  The -s is so only the summary of the directories, not going deeper happens.  All that is covered in the manpage for the respective commands. Worth skimming to see what other options might be useful.

We could have asked for 
```
$ sudo du -sh /var/lib/* | sort -hr |head -n5
```
Could that be useful?

---

### Post by ActionParsnip on 2023-03-17
It's only bloated for the default install. You can easily install server then add a window manager and Web browser to make a small punchy OS :o

---

### Post by TheFu on 2023-03-17
> **ActionParsnip said:**
> It's only bloated for the default install. You can easily install server then add a window manager and Web browser to make a small punchy OS :o

That works for nerdy people, but not typical end users.  Some subsystems are implemented differently in the server install which would perplex normal desktop people.  Try to get wifi working on a server install.  Not that hard, if you know what you are doing, but only the zyx-desktop meta-package install will add the network GUI tool on the toolbar.  There are about 10 other things like that which aren't included with a server install.

But .... APs take is true.
```
$ dft |grep vg00
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg00-root--00                   ext4   35G   11G   22G  33% /
/dev/mapper/vg00-home                       ext4   26G  9.8G   15G  41% /home
/dev/mapper/vg00-var                        ext4   54G   33G   19G  64% /var
/dev/nvme0n1p2                              ext4  574M  278M  254M  53% /boot
/dev/nvme0n1p1                              vfat   50M  6.1M   44M  13% /boot/efi

```
That's a 20.04 server install, in less than 30G used.  /var is only big because there are 5 lxd containers in that system stored in /var/.  The only snap package installed is lxd v5.11.  It wasn't that long ago when 10G total was needed to run a 16.04 server.

---

### Post by john-m-kane on 2023-03-18
> **TheFu said:**
> "Quite small" is subjective.  For a desktop, since 20.04, the OS has become massively bloated due to some choices Canonical has made. I can understand why they would make those choices, even if I disagree and prefer to have a system that runs well on 8GB of storage. Sadly, newer == more bloated almost always. Ubuntu isn't any different than other OSes in that regard.

BTW, when you post stuff ... the more junk that gets posted detracts from what's important.  Showing 60 lines of storage amounts when it is sorted detracts from the last 5 lines, which are the only ones that have any bearing at all.  You could have posted something like this:
```
$ sudo du -sh /var/lib/* | sort -h
...
3,7M    /var/lib/ubuntu-advantage
4,1M    /var/lib/aspell
15M    /var/lib/aptitude
15M    /var/lib/gdm3
21M    /var/lib/swcatalog
85M    /var/lib/dpkg
233M    /var/lib/apt
6,4G    /var/lib/flatpak
6,7G    /var/lib/snapd
```
and conveyed more than enough information.
BTW, we can reverse the sort using **sort -rh**. Then the largest would be at the top.  "-h" when it doesn't mean "help" often means "human" ... as in *human readable* or sorted *like a human would*.  *sort -h* tells sort to think of G as larger than M as larger than K - like a human would.  
For the **du** command above, the -h is human readable.  The -s is so only the summary of the directories, not going deeper happens.  All that is covered in the manpage for the respective commands. Worth skimming to see what other options might be useful.

We could have asked for 
```
$ sudo du -sh /var/lib/* | sort -hr |head -n5
```
Could that be useful?

I'll remember your suggestion if i'll need more help in the future.
Thank you and to everyone else for your help.
Now I'll mark the thread as solved. :)

---

