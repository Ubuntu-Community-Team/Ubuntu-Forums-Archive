---
title: "Why is my root large?"
date: 2014-01-19
forum: General Help
---

### Post by SuperFreak on 2014-01-19
I have read on numerous threads that Root directory does not need to be bigger than 12 GB. I deliberately made my root partition on install large (33 GB) because I had doubts about the 12 GB size from previous installs. Presently my Root folder is nearly 17 GB (see image) and I have a separate home directory. Looking at the disk  utilizer chart (Image 3) the home directory appears to ne counted as part of Root even though I created home in a separate partition. 
Sorry if this seems a little thick headed, perhaps someone can explain why Root on my system is so large

OH I did a clean out with Tweak of unused packages old kernels etc and it dropped the Root partition from 18.5 GB to around 17 GB

---

### Post by TheFu on 2014-01-19
You have control over where things get loaded and how much of "stuff" gets loaded.
If you like to install GUI apps and different desktop environments, then more storage will be needed.
If you use virtualbox and create VMs, the /var will get big - every virtual machine uses 8G+.
It looks like /media has lots of stuff inside it. This appears to be using about 3GB on the / partition.  3GB could be 1 Hidef video file.

Rules of thumb work for most people, not everyone.  My entire desktop that I've been using and migrating since 2008 is 15G. This includes programming projects, emails, and documents.  It does not include video or audio files - those are elsewhere, not part of a desktop. Also, I don't install many programs - I've been using Linux long enough that I know what I like and don't try out every program that I see on a website.

BTW, you seem to be missing a swap partition. Why is that?  [Swap is important]("https://help.ubuntu.com/community/SwapFaq") for desktops.

---

### Post by SuperFreak on 2014-01-19
@ The Fu   Swap partition is on the hard drive; the GParted screenshot was of the SSD. The media partition is actually closer to 3 TB and that is on a separate hard drive not the SSD that Root is on. Presumably it is the same with home; although listed under root it is really a symbolic link? as home is actually on a separate partition.
I think you may have partly answered my question as to why my Root partition is so big as I do have 2 DEs, Unity and Cinnamon

Numbers seem to add up such that root is comprised of home(6.9 GB),usr(4.6GB),var(2.2GB),opt(1 GB) ,lib(565 MB),boot(152 MB) and a bunch of smaller directories( Total of over 15 GB). Why is home part of the total for root if actually a separate partition?

---

### Post by jeanjd63 on 2014-01-20
Hello
You can try the command :
[B]sudo  du  -shx  /*  | sort  -rh
[/B]and so one to find where are bigs files.

---

### Post by SuperFreak on 2014-01-20
> **jeanjd63 said:**
> Hello
You can try the command :
[B]sudo  du  -shx  /*  | sort  -rh
[/B]and so one to find where are bigs files.


Thanks but I am not really interested in which are the larger files, I am more curious about why  home is counted towards the size of Root when it is a separate partition

---

### Post by grahammechanical on 2014-01-20
> [COLOR=#000000]why home is counted towards the size of Root when it is a separate partition[/COLOR]

Because it is mounted as /home? Whether the home folder is a folder/directory on the same partition as root ( / ) or on another partition it is still under the root directory/folder. Otherwise the OS would be broken. When the OS is loading it looks into the /home directory for user configuration files. In your case it gets redirected to the /home partition. It finds the configuration files it is looking for and successfully loads and you see a desktop that you wanted to see. Break the link to the /home partition and the OS will break. It is the way that Linux works.

Regards.

---

### Post by SuperFreak on 2014-01-20
Thanks grahammechanical
I had thought it was some kind of link to home not that home is contained in Root. My confusion stems from adding up the size of large directories to arrive at the total for root (which is 16.70 GB) as I couldn't see how it all added up unless home (7.22GB) was included in the total with all the other large directories (usr(4.6GB),var(2.2GB),opt(1 GB) ,lib(565 MB),boot(152 MB) and a bunch of smaller directories)

---

### Post by tgalati4 on 2014-01-20
"Root" can be used multiple ways.  The top-level directory is called root (/).  The root's home account (/root) is called root and is used extensively in some systems.  The entire directory tree under / is called root--as in your case.  Partitions are physical locations but soft links, hard links, drives and devices mounted in /etc/fstab can become part of root when mounted under /.  

The 12GB suggestion is good for new users (it used to be 5GB!), but as soon as you start compiling your own programs, compile a kernel, build a device module, add a desktop environment, you will quickly exceed the 12GB suggestion.

---

### Post by steeldriver on 2014-01-20
Have you tried the command-line df command? imho its output is less ambiguous than that of the GUI disk usage analyzer

```
df -h
```

---

### Post by SuperFreak on 2014-01-20
> **steeldriver said:**
> Have you tried the command-line df command? imho its output is less ambiguous than that of the GUI disk usage analyzer

```
df -h
```

Thanks. 
```
david@MainSqueeze:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3        33G   17G   15G  53% /
udev            7.7G  8.0K  7.7G   1% /dev
tmpfs           3.1G  1.1M  3.1G   1% /run
none            5.0M  4.0K  5.0M   1% /run/lock
none            7.7G  232K  7.7G   1% /run/shm
/dev/sda4        40G  6.5G   31G  18% /home
/dev/sda1       247M  487K  246M   1% /boot/efi
/dev/sdc1       3.6T  1.9T  1.6T  53% /media/Videos
/dev/sdb1       962G   85G  828G  10% /media/Documents
/dev/sdb2       2.7T  689G  1.9T  28% /media/Music
/dev/sdd1        15G  5.0G   10G  34% /media/26BC-A8C2

```

I realize I am sounding obtuse here but this is what I see in this output
17 GB used in / and 6.5 in /home which is under /. My understanding from what has been discussed here is that /home is a mount point and does not mean the entire contents of home are located within root. Just to reiterate this does not explain the 7GB shortfall in the ammount of space used up by root unless home is included and is not just a link. This is shown also in my GParted screenshot where root shows 17GB of space used. How can root be that large unless home is included with all it's contents . If it is then what is the point of the separate partition for home (sda4)? It would be an unnecessary duplication wouldn't it?

---

### Post by TheFu on 2014-01-20
The df output is correct.
The storage used is by partition.

If you ever had a /home under / (on the same partition)and put files there before creating the /home mount point and mounting a new partition there, then all those files are still sitting under the / partition (sda3) - effectively hidden because the other partition mounted as /home (sda4) hides it. That data is "hidden", if it exists.  I've seen this happen with backup partitions that weren't mounted for 1 backup job, so / got filled.

All of us have thought there was no way that files existed eating up storage over the yrs. Looking closer, I've always been able to find where the "lost space" was ... eventually.  Usually, I start with the **df -h** command, then use the **du -sh *** as I move down the directory tree to find the files/directories hogging storage.  Please trust us. You have files that are NOT on /home that are under sda3 on /.

I'm with steeldriver - use the CLI tools, not GUIs for this. GUIs tend to oversimplify things and might not show **the truth**. We care about truth here, not a pretty diagram.

---

### Post by Dave_L on 2014-01-20
The du command is handy for digging into this.

Example:
```
sudo du -h /var --max-depth=1
```

---

### Post by buzzingrobot on 2014-01-20
You have a single filesystem that uses multiple partitions.  You might easily have put /boot, /etc, /tmp, /var, /usr/local, and more on their own partitions, or on their own partitions on their own drives.  

The "Disk Usage Analyzer" seems to display results using the filesystem's view of things. All files and directories are part of a hierarchy beneath "/".

---

### Post by SuperFreak on 2014-01-20
This is clearer now. I opened File Sytem and found home which ontained a few files including trash and lost and found but my home directory "david" was as everyone seems to be saying a symbolic link not the actual directory.
Thank you all for providing the commands I will try them and see if there is a big resource hog in Root

---

### Post by tgalati4 on 2014-01-21
The advantage (one of several) of keeping home on a separate partition is that if your root drive/partition gets trashed, you could boot a LiveUSB and mount your home partition and have all of your work and personal files preserved.  The downside is that some tools (as you have noticed) will hide the relationship between disk space use and the directory tree.  Add a few remote file servers to your mount table and things quickly get confusing.

---

### Post by SuperFreak on 2014-01-21
> **tgalati4 said:**
> The advantage (one of several) of keeping home on a separate partition is that if your root drive/partition gets trashed, you could boot a LiveUSB and mount your home partition and have all of your work and personal files preserved.  The downside is that some tools (as you have noticed) will hide the relationship between disk space use and the directory tree.  Add a few remote file servers to your mount table and things quickly get confusing.

Presumably this is why it does in fact appear that my home folder contents are counted towards the total capacity of the Root Directory both in GParted and Disk Usage Analyzer. Presumably this is because they are on the same disk although separate partitions. The /media/Music  directory is on a separate disk and partition and is not counted towards Roots capacity
Using ```


sudo du -h /var --max-depth=1
```
command that Dave_L gave I looked at all the directories in my Root and added them up. Unless I add in the value for Home I don't get a total equal to what GParted( where as I said before root and home are separate partitions) said root is. 

Please forgive my confusion. I enjoy tinkering and using computers but I really have very little technical experience

---

### Post by TheFu on 2014-01-21
gparted/parted tells the truth at the partition level.  If /home is mounted to a different partition, then that storage is NOT included in the / mount storage reports.  

I cannot speak to how other GUI tools work. Don't use them.  
I trust **df** and **du**.

I'd have to check a little to see how LVM LVs munge this stuff. It doesn't, df still works as expected. Just checked.

BTW, /home is not some mandatory name or location. It can be named anything you like, just the passwd entry data would need to be modified to know where it is for each userid.  Different users can have their HOME on the same or different partitions as well.  At prior work places, our HOME directories were NFS mounted to every UNIX machine we had logins on. Same HOME regardless of the platform is handy, though it can mess with startup and config scripts - especially when the tools are in different locations for different machine architectures. ;)

---

### Post by SuperFreak on 2014-01-21
> gparted/parted tells the truth at the partition level. If /home is mounted to a different partition, then that storage is NOT included in the / mount storage reports.


That being the case I have to wonder about whether I have home within the root partition as well as as it's own partition, because otherwise the numbers don't seem to add up.
If I add up all the directories below (file system which I believe is Root or /)I get approximately 15 GB with Home included but media excluded(as it clearly is not counted part of root in Gparted). This is a bit shy of the 16.7 GParted says is used in Root partition but much closer than if I didn't count Home(6.5GB) in Root. Is the home directory duplicated then in Root and in it's own partition?
```
david@MainSqueeze:~$ sudo du -h /bin --max-depth=1
8.9M	/bin
david@MainSqueeze:~$ sudo du -h /boot --max-depth=1
487K	/boot/efi
2.4M	/boot/grub
4.4M	/boot/grub.bak
1.6M	/boot/extlinux
146M	/boot
david@MainSqueeze:~$ sudo du -h /dev --max-depth=1
0	/dev/snd
0	/dev/cpu
4.0K	/dev/.udev
0	/dev/usb
0	/dev/disk
0	/dev/bsg
0	/dev/dri
0	/dev/char
0	/dev/block
0	/dev/pts
0	/dev/mapper
0	/dev/input
0	/dev/bus
0	/dev/net
4.0K	/dev
david@MainSqueeze:~$ sudo du -h /etc --max-depth=1
20K	/etc/gnome
8.0K	/etc/insserv
84K	/etc/cron.daily
8.0K	/etc/gnome-app-install
8.0K	/etc/python
28K	/etc/pm
28K	/etc/dpkg
32K	/etc/NetworkManager
1.1M	/etc/bash_completion.d
96K	/etc/sgml
8.0K	/etc/sudoers.d
12K	/etc/ca-certificates
24K	/etc/avahi
8.0K	/etc/cron.hourly
204K	/etc/default
28K	/etc/skel
20K	/etc/cron.weekly
8.0K	/etc/at-spi2
12K	/etc/emacs
8.0K	/etc/postgresql-common
256K	/etc/xdg
12K	/etc/systemd
16K	/etc/apparmor
8.0K	/etc/rc3.d
24K	/etc/menu-methods
348K	/etc/fonts
44K	/etc/dhcp
20K	/etc/ConsoleKit
12K	/etc/libnl-3
560K	/etc/mono
96K	/etc/speech-dispatcher
48K	/etc/polkit-1
36K	/etc/ghostscript
12K	/etc/doc-base
8.0K	/etc/.java
16K	/etc/openal
32K	/etc/squeezeboxserver
332K	/etc/sane.d
8.0K	/etc/ldap
8.0K	/etc/profile.d
12K	/etc/cron.monthly

144K	/etc/alternatives
8.0K	/etc/qemu
60K	/etc/grub.d
4.0K	/etc/fstab.d
68K	/etc/apport
20K	/etc/gnome-system-tools
12K	/etc/kbd
156K	/etc/console-setup
12K	/etc/vim
32K	/etc/iproute2
68K	/etc/gimp
24K	/etc/udev
8.0K	/etc/bonobo-activation
16K	/etc/foomatic
32K	/etc/logcheck
540K	/etc/X11
56K	/etc/sound
8.0K	/etc/calendar
4.0K	/etc/update-notifier
12K	/etc/checkbox.d
1.9M	/etc/apparmor.d
8.0K	/etc/gufw
3.7M	/etc/brltty
16K	/etc/rsyslog.d
60K	/etc/xml
20K	/etc/libreoffice
4.0K	/etc/ODBCDataSources
300K	/etc/apt
76K	/etc/network
8.0K	/etc/menu
12K	/etc/lightdm
40K	/etc/apm
8.0K	/etc/thunderbird
8.0K	/etc/icedtea-web
4.0K	/etc/lsb-base
16K	/etc/chatscripts
228K	/etc/ImageMagick
12K	/etc/pkcs11
4.0K	/etc/sensors.d
32K	/etc/update-motd.d
4.0K	/etc/libpaper.d
44K	/etc/resolvconf
4.0K	/etc/usb_modeswitch.d
76K	/etc/samba
24K	/etc/gconf
104K	/etc/pam.d
12K	/etc/newt
64K	/etc/apcupsd
72K	/etc/initramfs-tools
224K	/etc/dbus-1
8.0K	/etc/gdb
260K	/etc/init.d
12K	/etc/groff
24K	/etc/vlc
8.0K	/etc/rc6.d
44K	/etc/wpa_supplicant
20K	/etc/smartmontools
16K	/etc/cupshelpers
8.0K	/etc/gamin
340K	/etc/init
8.0K	/etc/terminfo
8.0K	/etc/pcmcia
12K	/etc/mysql
996K	/etc/ssl
8.0K	/etc/esound
44K	/etc/kernel
28K	/etc/perl
8.0K	/etc/snmp
8.0K	/etc/UPower
32K	/etc/bluetooth
8.0K	/etc/python2.7
16K	/etc/firefox
52K	/etc/security
12K	/etc/qt3
28K	/etc/compizconfig
8.0K	/etc/depmod.d
12K	/etc/xul-ext
16K	/etc/ginn
20K	/etc/update-manager
156K	/etc/java-7-openjdk
4.0K	/etc/dictionaries-common
12K	/etc/dhcp3
32K	/etc/defoma
12K	/etc/cron.d
48K	/etc/modprobe.d
12K	/etc/obex-data-server
8.0K	/etc/ifplugd
12K	/etc/gtk-3.0
24K	/etc/pulse
44K	/etc/motion
112K	/etc/ppp
8.0K	/etc/gnome-settings-daemon
8.0K	/etc/rc2.d
8.0K	/etc/rcS.d
80K	/etc/logrotate.d
36K	/etc/sysctl.d
84K	/etc/postfix
8.0K	/etc/rc4.d
20K	/etc/ld.so.conf.d
12K	/etc/wireshark
64K	/etc/ufw
152K	/etc/java-6-openjdk
8.0K	/etc/rc1.d
8.0K	/etc/rc0.d
8.0K	/etc/hp
8.0K	/etc/rc5.d
12K	/etc/insserv.conf.d
132K	/etc/ssh
260K	/etc/acpi
16K	/etc/opt
488K	/etc/apache2
16K	/etc/gnome-vfs-2.0
92K	/etc/cups
8.0K	/etc/grub.d.bak
248K	/etc/fail2ban
17M	/etc
david@MainSqueeze:~$ sudo du -h /home --max-depth=1
du: cannot access `/home/david/.gvfs': Permission denied
6.5G	/home/david
244K	/home/.Trash-0
24K	/home/hts
16K	/home/lost+found
6.5G	/home
david@MainSqueeze:~$ sudo du -h /lib --max-depth=1
100K	/lib/cryptsetup
120K	/lib/systemd
8.0K	/lib/apparmor
16K	/lib/lsb
459M	/lib/modules
49M	/lib/firmware
1.7M	/lib/udev
52K	/lib/recovery-mode
748K	/lib/brltty
16K	/lib/hdparm
12K	/lib/linux-sound-base
8.0K	/lib/resolvconf
16K	/lib/bridge-utils
1.1M	/lib/xtables
24K	/lib/init
204K	/lib/terminfo
28K	/lib/crda
328K	/lib/plymouth
60K	/lib/security
11M	/lib/i386-linux-gnu
16M	/lib/x86_64-linux-gnu
40K	/lib/ufw
8.0K	/lib/oss-compat
540M	/lib
david@MainSqueeze:~$ sudo du -h /lib32 --max-depth=1
3.4M	/lib32
david@MainSqueeze:~$ sudo du -h /lib64 --max-depth=1
4.0K	/lib64
david@MainSqueeze:~$ sudo du -h /lost+found --max-depth=1
16K	/lost+found
david@MainSqueeze:~$ sudo du -h /media --max-depth=1
85G	/media/Documents
1.9T	/media/Videos
689G	/media/Music
5.0G	/media/26BC-A8C2
2.6T	/media
david@MainSqueeze:~$ sudo du -h /mnt --max-depth=1
16K	/mnt/boot-sav
16K	/mnt/BootInfo
36K	/mnt
david@MainSqueeze:~$ sudo du -h /opt --max-depth=1
208M	/opt/google
71M	/opt/BitDefender
200K	/opt/brother
540M	/opt/libreoffice4.0
183M	/opt/BitDefender-scanner
1000M	/opt
david@MainSqueeze:~$ sudo du -h /proc --max-depth=1
0	/proc/asound
0	/proc/dri
0	/proc/scsi
0	/proc/acpi
0	/proc/irq
0	/proc/sys
0	/proc/bus
0	/proc/tty
0	/proc/driver
0	/proc/fs
0	/proc/sysvipc
0	/proc/1
0	/proc/2
0	/proc/3
0	/proc/5
0	/proc/6
0	/proc/7
0	/proc/8
0	/proc/9
0	/proc/10
0	/proc/11
0	/proc/12
0	/proc/13
0	/proc/14
0	/proc/16
0	/proc/17
0	/proc/18
0	/proc/19
0	/proc/20
0	/proc/21
0	/proc/22
0	/proc/23
0	/proc/24
0	/proc/26
0	/proc/27
0	/proc/28
0	/proc/29
0	/proc/31
0	/proc/32
0	/proc/33
0	/proc/34
0	/proc/35
0	/proc/36
0	/proc/37
0	/proc/38
0	/proc/39
0	/proc/40
0	/proc/41
0	/proc/42
0	/proc/43
0	/proc/44
0	/proc/45
0	/proc/46
0	/proc/47
0	/proc/48
0	/proc/49
0	/proc/50
0	/proc/51
0	/proc/52
0	/proc/53
0	/proc/54
0	/proc/55
0	/proc/56
0	/proc/57
0	/proc/58
0	/proc/60
0	/proc/61
0	/proc/62
0	/proc/63
0	/proc/64
0	/proc/65
0	/proc/66
0	/proc/77
0	/proc/80
0	/proc/82
0	/proc/101
0	/proc/102
0	/proc/104
0	/proc/275
0	/proc/276
0	/proc/277
0	/proc/278
0	/proc/279
0	/proc/280
0	/proc/285
0	/proc/287
0	/proc/288
0	/proc/292
0	/proc/293
0	/proc/297
0	/proc/298
0	/proc/318
0	/proc/321
0	/proc/322
0	/proc/372
0	/proc/373
0	/proc/486
0	/proc/487
0	/proc/735
0	/proc/736
0	/proc/738
0	/proc/739
0	/proc/740
0	/proc/743
0	/proc/744
0	/proc/747
0	/proc/748
0	/proc/761
0	/proc/766
0	/proc/792
0	/proc/821
0	/proc/872
0	/proc/899
0	/proc/938
0	/proc/941
0	/proc/945
0	/proc/948
0	/proc/1036
0	/proc/1042
0	/proc/1077
0	/proc/1117
0	/proc/1191
0	/proc/1209
0	/proc/1210
0	/proc/1245
0	/proc/1254
0	/proc/1278
0	/proc/1329
0	/proc/1331
0	/proc/1334
0	/proc/1346
0	/proc/1367
0	/proc/1399
0	/proc/1406
0	/proc/1416
0	/proc/1417
0	/proc/1419
0	/proc/1432
0	/proc/1434
0	/proc/1435
0	/proc/1436
0	/proc/1442
0	/proc/1444
0	/proc/1525
0	/proc/1537
0	/proc/1551
0	/proc/1552
0	/proc/1565
0	/proc/1655
0	/proc/1689
0	/proc/1690
0	/proc/1702
0	/proc/1716
0	/proc/1782
0	/proc/1822
0	/proc/1833
0	/proc/1835
0	/proc/1842
0	/proc/1877
0	/proc/1879
0	/proc/1903
0	/proc/1906
0	/proc/1908
0	/proc/1909
0	/proc/2136
0	/proc/2225
0	/proc/2229
0	/proc/2260
0	/proc/2271
0	/proc/2272
0	/proc/2281
0	/proc/2494
0	/proc/2505
0	/proc/2551
0	/proc/2562
0	/proc/2599
0	/proc/2602
0	/proc/2603
0	/proc/2612
0	/proc/2622
0	/proc/2624
0	/proc/2631
0	/proc/2642
0	/proc/2647
0	/proc/2649
0	/proc/2656
0	/proc/2660
0	/proc/2661
0	/proc/2666
0	/proc/2669
0	/proc/2673
0	/proc/2674
0	/proc/2677
0	/proc/2679
0	/proc/2680
0	/proc/2688
0	/proc/2693
0	/proc/2697
0	/proc/2714
0	/proc/2717
0	/proc/2722
0	/proc/2801
0	/proc/2904
0	/proc/2923
0	/proc/2945
0	/proc/2985
0	/proc/3051
0	/proc/3185
0	/proc/6122
0	/proc/7468
0	/proc/8938
0	/proc/9884
0	/proc/10121
0	/proc/10181
0	/proc/10238
0	/proc/10325
0	/proc/10329
0	/proc/10426
0	/proc/10455
0	/proc/10527
0	/proc/10533
0	/proc/10534
0	/proc/10661
0	/proc/10668
0	/proc/10696
0	/proc/10697
0	/proc/10698
0	/proc/10699
0	/proc/10700
0	/proc/10701
0	/proc/10734
0	/proc/10767
0	/proc/10768
0	/proc/10769
0	/proc/10770
0	/proc/10771
0	/proc/10772
0	/proc/10773
0	/proc/10774
0	/proc/10775
0	/proc/10776
0	/proc/10777
0	/proc/10778
0	/proc/10779
0	/proc/10780
0	/proc/10783
du: cannot access `/proc/10784/task/10784/fd/3': No such file or directory
du: cannot access `/proc/10784/task/10784/fdinfo/3': No such file or directory
du: cannot access `/proc/10784/fd/3': No such file or directory
du: cannot access `/proc/10784/fdinfo/3': No such file or directory
0	/proc/10784
0	/proc
david@MainSqueeze:~$ sudo du -h /run --max-depth=1
0	/run/udisks
0	/run/pm-utils
4.0K	/run/fail2ban
0	/run/apache2
0	/run/pppconfig
4.0K	/run/xfs
4.0K	/run/console
4.0K	/run/ConsoleKit
4.0K	/run/lightdm
152K	/run/samba
12K	/run/cups
0	/run/udev-configure-printer
4.0K	/run/avahi-daemon
4.0K	/run/network
4.0K	/run/dbus
220K	/run/shm
4.0K	/run/lock
0	/run/mount
8.0K	/run/resolvconf
8.0K	/run/sendsigs.omit.d
860K	/run/udev
0	/run/initramfs
1.4M	/run
david@MainSqueeze:~$ sudo du -h /sbin --max-depth=1
9.3M	/sbin
david@MainSqueeze:~$ sudo du -h /selinux --max-depth=1
4.0K	/selinux
david@MainSqueeze:~$ sudo du -h /srv --max-depth=1
4.0K	/srv
david@MainSqueeze:~$ sudo du -h /sys --max-depth=1
0	/sys/fs
0	/sys/bus
0	/sys/dev
0	/sys/devices
0	/sys/block
0	/sys/class
0	/sys/power
0	/sys/firmware
0	/sys/kernel
0	/sys/module
0	/sys/hypervisor
0	/sys
david@MainSqueeze:~$ sudo du -h /tmp --max-depth=1
4.0K	/tmp/at-spi2
4.0K	/tmp/.winbindd
4.0K	/tmp/plugtmp
4.0K	/tmp/pulse-PKdhtXMmr18n
8.0K	/tmp/pulse-weOzMmjUZvV2
16K	/tmp/par-squeezeboxserver
4.0K	/tmp/keyring-RN56Yb
4.0K	/tmp/ssh-esmVEhfK2562
4.0K	/tmp/.X11-unix
4.0K	/tmp/.font-unix
4.0K	/tmp/.ICE-unix
4.0K	/tmp/orbit-david
4.0K	/tmp/pulse-2L9K88eMlGn7
76K	/tmp
david@MainSqueeze:~$ sudo du -h /ubiquity-apt-clone --max-depth=1
4.0M	/ubiquity-apt-clone
david@MainSqueeze:~$ sudo du -h /usr --max-depth=1
160K	/usr/lib64
1.6G	/usr/share
606M	/usr/src
8.4M	/usr/include
280M	/usr/bin
34M	/usr/sbin
6.5M	/usr/lib32
508K	/usr/games
1.9G	/usr/lib
4.8M	/usr/local
4.4G	/usr
david@MainSqueeze:~$ sudo du -h /var --max-depth=1
1.5M	/var/mail
8.0K	/var/www
91M	/var/log
4.0K	/var/crash
3.6M	/var/spool
4.0K	/var/games
1.6G	/var/lib
183M	/var/tmp
5.8M	/var/backups
185M	/var/cache
4.0K	/var/opt
4.0K	/var/local
2.1G	/var
david@MainSqueeze:~$ 

```

---

### Post by buzzingrobot on 2014-01-21
> **SuperFreak said:**
> That being the case I have to wonder about whether I have home within the root partition as well as as it's own partition, because otherwise the numbers don't seem to add up.
If I add up all the directories below (file system which I believe is Root or /)I get approximately 15 GB with Home included but media excluded(as it clearly is not counted part of root in Gparted). This is a bit shy of the 16.7 GParted says is used in Root partition but much closer than if I didn't count Home(6.5GB) in Root. Is the home directory duplicated then in Root and in it's own partition?
```
david@MainSqueeze:~$ sudo du -h /bin --max-depth=1
8.9M    /bin
david@MainSqueeze:~$ sudo du -h /boot --max-depth=1
487K    /boot/efi
2.4M    /boot/grub
4.4M    /boot/grub.bak
1.6M    /boot/extlinux
146M    /boot
david@MainSqueeze:~$ sudo du -h /dev --max-depth=1
0    /dev/snd
0    /dev/cpu
4.0K    /dev/.udev
0    /dev/usb
0    /dev/disk
0    /dev/bsg
0    /dev/dri
0    /dev/char
0    /dev/block
0    /dev/pts
0    /dev/mapper
0    /dev/input
0    /dev/bus
0    /dev/net
4.0K    /dev
david@MainSqueeze:~$ sudo du -h /etc --max-depth=1
20K    /etc/gnome
8.0K    /etc/insserv
84K    /etc/cron.daily
8.0K    /etc/gnome-app-install
8.0K    /etc/python
28K    /etc/pm
28K    /etc/dpkg
32K    /etc/NetworkManager
1.1M    /etc/bash_completion.d
96K    /etc/sgml
8.0K    /etc/sudoers.d
12K    /etc/ca-certificates
24K    /etc/avahi
8.0K    /etc/cron.hourly
204K    /etc/default
28K    /etc/skel
20K    /etc/cron.weekly
8.0K    /etc/at-spi2
12K    /etc/emacs
8.0K    /etc/postgresql-common
256K    /etc/xdg
12K    /etc/systemd
16K    /etc/apparmor
8.0K    /etc/rc3.d
24K    /etc/menu-methods
348K    /etc/fonts
44K    /etc/dhcp
20K    /etc/ConsoleKit
12K    /etc/libnl-3
560K    /etc/mono
96K    /etc/speech-dispatcher
48K    /etc/polkit-1
36K    /etc/ghostscript
12K    /etc/doc-base
8.0K    /etc/.java
16K    /etc/openal
32K    /etc/squeezeboxserver
332K    /etc/sane.d
8.0K    /etc/ldap
8.0K    /etc/profile.d
12K    /etc/cron.monthly

144K    /etc/alternatives
8.0K    /etc/qemu
60K    /etc/grub.d
4.0K    /etc/fstab.d
68K    /etc/apport
20K    /etc/gnome-system-tools
12K    /etc/kbd
156K    /etc/console-setup
12K    /etc/vim
32K    /etc/iproute2
68K    /etc/gimp
24K    /etc/udev
8.0K    /etc/bonobo-activation
16K    /etc/foomatic
32K    /etc/logcheck
540K    /etc/X11
56K    /etc/sound
8.0K    /etc/calendar
4.0K    /etc/update-notifier
12K    /etc/checkbox.d
1.9M    /etc/apparmor.d
8.0K    /etc/gufw
3.7M    /etc/brltty
16K    /etc/rsyslog.d
60K    /etc/xml
20K    /etc/libreoffice
4.0K    /etc/ODBCDataSources
300K    /etc/apt
76K    /etc/network
8.0K    /etc/menu
12K    /etc/lightdm
40K    /etc/apm
8.0K    /etc/thunderbird
8.0K    /etc/icedtea-web
4.0K    /etc/lsb-base
16K    /etc/chatscripts
228K    /etc/ImageMagick
12K    /etc/pkcs11
4.0K    /etc/sensors.d
32K    /etc/update-motd.d
4.0K    /etc/libpaper.d
44K    /etc/resolvconf
4.0K    /etc/usb_modeswitch.d
76K    /etc/samba
24K    /etc/gconf
104K    /etc/pam.d
12K    /etc/newt
64K    /etc/apcupsd
72K    /etc/initramfs-tools
224K    /etc/dbus-1
8.0K    /etc/gdb
260K    /etc/init.d
12K    /etc/groff
24K    /etc/vlc
8.0K    /etc/rc6.d
44K    /etc/wpa_supplicant
20K    /etc/smartmontools
16K    /etc/cupshelpers
8.0K    /etc/gamin
340K    /etc/init
8.0K    /etc/terminfo
8.0K    /etc/pcmcia
12K    /etc/mysql
996K    /etc/ssl
8.0K    /etc/esound
44K    /etc/kernel
28K    /etc/perl
8.0K    /etc/snmp
8.0K    /etc/UPower
32K    /etc/bluetooth
8.0K    /etc/python2.7
16K    /etc/firefox
52K    /etc/security
12K    /etc/qt3
28K    /etc/compizconfig
8.0K    /etc/depmod.d
12K    /etc/xul-ext
16K    /etc/ginn
20K    /etc/update-manager
156K    /etc/java-7-openjdk
4.0K    /etc/dictionaries-common
12K    /etc/dhcp3
32K    /etc/defoma
12K    /etc/cron.d
48K    /etc/modprobe.d
12K    /etc/obex-data-server
8.0K    /etc/ifplugd
12K    /etc/gtk-3.0
24K    /etc/pulse
44K    /etc/motion
112K    /etc/ppp
8.0K    /etc/gnome-settings-daemon
8.0K    /etc/rc2.d
8.0K    /etc/rcS.d
80K    /etc/logrotate.d
36K    /etc/sysctl.d
84K    /etc/postfix
8.0K    /etc/rc4.d
20K    /etc/ld.so.conf.d
12K    /etc/wireshark
64K    /etc/ufw
152K    /etc/java-6-openjdk
8.0K    /etc/rc1.d
8.0K    /etc/rc0.d
8.0K    /etc/hp
8.0K    /etc/rc5.d
12K    /etc/insserv.conf.d
132K    /etc/ssh
260K    /etc/acpi
16K    /etc/opt
488K    /etc/apache2
16K    /etc/gnome-vfs-2.0
92K    /etc/cups
8.0K    /etc/grub.d.bak
248K    /etc/fail2ban
17M    /etc
david@MainSqueeze:~$ sudo du -h /home --max-depth=1
du: cannot access `/home/david/.gvfs': Permission denied
6.5G    /home/david
244K    /home/.Trash-0
24K    /home/hts
16K    /home/lost+found
6.5G    /home
david@MainSqueeze:~$ sudo du -h /lib --max-depth=1
100K    /lib/cryptsetup
120K    /lib/systemd
8.0K    /lib/apparmor
16K    /lib/lsb
459M    /lib/modules
49M    /lib/firmware
1.7M    /lib/udev
52K    /lib/recovery-mode
748K    /lib/brltty
16K    /lib/hdparm
12K    /lib/linux-sound-base
8.0K    /lib/resolvconf
16K    /lib/bridge-utils
1.1M    /lib/xtables
24K    /lib/init
204K    /lib/terminfo
28K    /lib/crda
328K    /lib/plymouth
60K    /lib/security
11M    /lib/i386-linux-gnu
16M    /lib/x86_64-linux-gnu
40K    /lib/ufw
8.0K    /lib/oss-compat
540M    /lib
david@MainSqueeze:~$ sudo du -h /lib32 --max-depth=1
3.4M    /lib32
david@MainSqueeze:~$ sudo du -h /lib64 --max-depth=1
4.0K    /lib64
david@MainSqueeze:~$ sudo du -h /lost+found --max-depth=1
16K    /lost+found
david@MainSqueeze:~$ sudo du -h /media --max-depth=1
85G    /media/Documents
1.9T    /media/Videos
689G    /media/Music
5.0G    /media/26BC-A8C2
2.6T    /media
david@MainSqueeze:~$ sudo du -h /mnt --max-depth=1
16K    /mnt/boot-sav
16K    /mnt/BootInfo
36K    /mnt
david@MainSqueeze:~$ sudo du -h /opt --max-depth=1
208M    /opt/google
71M    /opt/BitDefender
200K    /opt/brother
540M    /opt/libreoffice4.0
183M    /opt/BitDefender-scanner
1000M    /opt
david@MainSqueeze:~$ sudo du -h /proc --max-depth=1
0    /proc/asound
0    /proc/dri
0    /proc/scsi
0    /proc/acpi
0    /proc/irq
0    /proc/sys
0    /proc/bus
0    /proc/tty
0    /proc/driver
0    /proc/fs
0    /proc/sysvipc
0    /proc/1
0    /proc/2
0    /proc/3
0    /proc/5
0    /proc/6
0    /proc/7
0    /proc/8
0    /proc/9
0    /proc/10
0    /proc/11
0    /proc/12
0    /proc/13
0    /proc/14
0    /proc/16
0    /proc/17
0    /proc/18
0    /proc/19
0    /proc/20
0    /proc/21
0    /proc/22
0    /proc/23
0    /proc/24
0    /proc/26
0    /proc/27
0    /proc/28
0    /proc/29
0    /proc/31
0    /proc/32
0    /proc/33
0    /proc/34
0    /proc/35
0    /proc/36
0    /proc/37
0    /proc/38
0    /proc/39
0    /proc/40
0    /proc/41
0    /proc/42
0    /proc/43
0    /proc/44
0    /proc/45
0    /proc/46
0    /proc/47
0    /proc/48
0    /proc/49
0    /proc/50
0    /proc/51
0    /proc/52
0    /proc/53
0    /proc/54
0    /proc/55
0    /proc/56
0    /proc/57
0    /proc/58
0    /proc/60
0    /proc/61
0    /proc/62
0    /proc/63
0    /proc/64
0    /proc/65
0    /proc/66
0    /proc/77
0    /proc/80
0    /proc/82
0    /proc/101
0    /proc/102
0    /proc/104
0    /proc/275
0    /proc/276
0    /proc/277
0    /proc/278
0    /proc/279
0    /proc/280
0    /proc/285
0    /proc/287
0    /proc/288
0    /proc/292
0    /proc/293
0    /proc/297
0    /proc/298
0    /proc/318
0    /proc/321
0    /proc/322
0    /proc/372
0    /proc/373
0    /proc/486
0    /proc/487
0    /proc/735
0    /proc/736
0    /proc/738
0    /proc/739
0    /proc/740
0    /proc/743
0    /proc/744
0    /proc/747
0    /proc/748
0    /proc/761
0    /proc/766
0    /proc/792
0    /proc/821
0    /proc/872
0    /proc/899
0    /proc/938
0    /proc/941
0    /proc/945
0    /proc/948
0    /proc/1036
0    /proc/1042
0    /proc/1077
0    /proc/1117
0    /proc/1191
0    /proc/1209
0    /proc/1210
0    /proc/1245
0    /proc/1254
0    /proc/1278
0    /proc/1329
0    /proc/1331
0    /proc/1334
0    /proc/1346
0    /proc/1367
0    /proc/1399
0    /proc/1406
0    /proc/1416
0    /proc/1417
0    /proc/1419
0    /proc/1432
0    /proc/1434
0    /proc/1435
0    /proc/1436
0    /proc/1442
0    /proc/1444
0    /proc/1525
0    /proc/1537
0    /proc/1551
0    /proc/1552
0    /proc/1565
0    /proc/1655
0    /proc/1689
0    /proc/1690
0    /proc/1702
0    /proc/1716
0    /proc/1782
0    /proc/1822
0    /proc/1833
0    /proc/1835
0    /proc/1842
0    /proc/1877
0    /proc/1879
0    /proc/1903
0    /proc/1906
0    /proc/1908
0    /proc/1909
0    /proc/2136
0    /proc/2225
0    /proc/2229
0    /proc/2260
0    /proc/2271
0    /proc/2272
0    /proc/2281
0    /proc/2494
0    /proc/2505
0    /proc/2551
0    /proc/2562
0    /proc/2599
0    /proc/2602
0    /proc/2603
0    /proc/2612
0    /proc/2622
0    /proc/2624
0    /proc/2631
0    /proc/2642
0    /proc/2647
0    /proc/2649
0    /proc/2656
0    /proc/2660
0    /proc/2661
0    /proc/2666
0    /proc/2669
0    /proc/2673
0    /proc/2674
0    /proc/2677
0    /proc/2679
0    /proc/2680
0    /proc/2688
0    /proc/2693
0    /proc/2697
0    /proc/2714
0    /proc/2717
0    /proc/2722
0    /proc/2801
0    /proc/2904
0    /proc/2923
0    /proc/2945
0    /proc/2985
0    /proc/3051
0    /proc/3185
0    /proc/6122
0    /proc/7468
0    /proc/8938
0    /proc/9884
0    /proc/10121
0    /proc/10181
0    /proc/10238
0    /proc/10325
0    /proc/10329
0    /proc/10426
0    /proc/10455
0    /proc/10527
0    /proc/10533
0    /proc/10534
0    /proc/10661
0    /proc/10668
0    /proc/10696
0    /proc/10697
0    /proc/10698
0    /proc/10699
0    /proc/10700
0    /proc/10701
0    /proc/10734
0    /proc/10767
0    /proc/10768
0    /proc/10769
0    /proc/10770
0    /proc/10771
0    /proc/10772
0    /proc/10773
0    /proc/10774
0    /proc/10775
0    /proc/10776
0    /proc/10777
0    /proc/10778
0    /proc/10779
0    /proc/10780
0    /proc/10783
du: cannot access `/proc/10784/task/10784/fd/3': No such file or directory
du: cannot access `/proc/10784/task/10784/fdinfo/3': No such file or directory
du: cannot access `/proc/10784/fd/3': No such file or directory
du: cannot access `/proc/10784/fdinfo/3': No such file or directory
0    /proc/10784
0    /proc
david@MainSqueeze:~$ sudo du -h /run --max-depth=1
0    /run/udisks
0    /run/pm-utils
4.0K    /run/fail2ban
0    /run/apache2
0    /run/pppconfig
4.0K    /run/xfs
4.0K    /run/console
4.0K    /run/ConsoleKit
4.0K    /run/lightdm
152K    /run/samba
12K    /run/cups
0    /run/udev-configure-printer
4.0K    /run/avahi-daemon
4.0K    /run/network
4.0K    /run/dbus
220K    /run/shm
4.0K    /run/lock
0    /run/mount
8.0K    /run/resolvconf
8.0K    /run/sendsigs.omit.d
860K    /run/udev
0    /run/initramfs
1.4M    /run
david@MainSqueeze:~$ sudo du -h /sbin --max-depth=1
9.3M    /sbin
david@MainSqueeze:~$ sudo du -h /selinux --max-depth=1
4.0K    /selinux
david@MainSqueeze:~$ sudo du -h /srv --max-depth=1
4.0K    /srv
david@MainSqueeze:~$ sudo du -h /sys --max-depth=1
0    /sys/fs
0    /sys/bus
0    /sys/dev
0    /sys/devices
0    /sys/block
0    /sys/class
0    /sys/power
0    /sys/firmware
0    /sys/kernel
0    /sys/module
0    /sys/hypervisor
0    /sys
david@MainSqueeze:~$ sudo du -h /tmp --max-depth=1
4.0K    /tmp/at-spi2
4.0K    /tmp/.winbindd
4.0K    /tmp/plugtmp
4.0K    /tmp/pulse-PKdhtXMmr18n
8.0K    /tmp/pulse-weOzMmjUZvV2
16K    /tmp/par-squeezeboxserver
4.0K    /tmp/keyring-RN56Yb
4.0K    /tmp/ssh-esmVEhfK2562
4.0K    /tmp/.X11-unix
4.0K    /tmp/.font-unix
4.0K    /tmp/.ICE-unix
4.0K    /tmp/orbit-david
4.0K    /tmp/pulse-2L9K88eMlGn7
76K    /tmp
david@MainSqueeze:~$ sudo du -h /ubiquity-apt-clone --max-depth=1
4.0M    /ubiquity-apt-clone
david@MainSqueeze:~$ sudo du -h /usr --max-depth=1
160K    /usr/lib64
1.6G    /usr/share
606M    /usr/src
8.4M    /usr/include
280M    /usr/bin
34M    /usr/sbin
6.5M    /usr/lib32
508K    /usr/games
1.9G    /usr/lib
4.8M    /usr/local
4.4G    /usr
david@MainSqueeze:~$ sudo du -h /var --max-depth=1
1.5M    /var/mail
8.0K    /var/www
91M    /var/log
4.0K    /var/crash
3.6M    /var/spool
4.0K    /var/games
1.6G    /var/lib
183M    /var/tmp
5.8M    /var/backups
185M    /var/cache
4.0K    /var/opt
4.0K    /var/local
2.1G    /var
david@MainSqueeze:~$ 

```


Can't have partitions inside of partitions. If you created /home as a separate partition, it is.

Some tools use 1024k as a kilobyte.  Others round down to 1000k.  That might account for the slight difference. (Actually, all those numbers have been rounded to a single decimal place. I.e., 1,024,001 bytes and 995,001 bytes both get rounded to 1.0M, obscuring the difference of 29000 bytes.)

---

### Post by SuperFreak on 2014-01-21
It makes sense what you are saying but if I don't include the home volume    in the total for Root then Root works out to less than 9 GB which is considerably less than the 16.7 GB GParted reports Root as. That is not really a slight difference. And yes I did create  separate partitions for / and home using Something Different option in the installation.

We seem to be rehashing the same points. My issue is I don't understand why my Root partition as reported by Gparted is so big  since home is a separate partition (see first image post 1) and I have added up the volumes using both graphical and CLI and the only explanation I can come up with is either home is duplicated in root (which you say is not possible) or Gparted is not reporting correctly or the more obvious explanation I have misunderstood the matter

---

### Post by jeanjd63 on 2014-01-22
Could you give the return of :
**sudo du -shx /* | sort -rh**

---

### Post by SuperFreak on 2014-01-22
Thanks for putting up with my line of inquiry. Here is the output:

```
david@MainSqueeze:~$ sudo du -shx /* | sort -rh
[sudo] password for david: 
du: cannot access `/home/david/.gvfs': Permission denied
du: cannot access `/proc/5318/task/5318/fd/3': No such file or directory
du: cannot access `/proc/5318/task/5318/fdinfo/3': No such file or directory
du: cannot access `/proc/5318/fd/3': No such file or directory
du: cannot access `/proc/5318/fdinfo/3': No such file or directory
8.0G	/root
6.5G	/home
4.4G	/usr
2.1G	/var
1.3G	/opt
542M	/lib
145M	/boot
17M	/etc
9.3M	/sbin
8.9M	/bin
4.0M	/ubiquity-apt-clone
3.4M	/lib32
1.1M	/run
116K	/gapcmon-0.8.2.tar.bz2
76K	/tmp
36K	/mnt
20K	/media
16K	/lost+found
12K	/gapcmon.spec
4.0K	/srv
4.0K	/selinux
4.0K	/lib64
4.0K	/dev
4.0K	/dead.letter
4.0K	/cdrom
0	/vmlinuz.old
0	/vmlinuz
0	/sys
0	/proc
0	/initrd.img.old
0	/initrd.img
david@MainSqueeze:~$ 

```

The output appears to segregate directories like /home,/usr, /var, /opt etc from /root, are some of these (or all) not infact contained within root. Perhaps I am not understanding this but I had thought that File System, Root and / were all the same thing

---

### Post by TheFu on 2014-01-22
8G under /root!!!!!!!    There is an issue.
On my machines /root has under 50MB - mostly scripts and data used only by root for backups or kernel cleanup stuff.
That /gapcmon*bz2 file in / ... scary.  

How often do you use the root account for normal desktop stuff?  It can be very dangerous to download files with root.

---

### Post by SuperFreak on 2014-01-22
I may be a little careless downloading and installing 3rd party software. gapcmon*bz2 is used to monitor my UPS, graphically showing power failures and such.
I think I followed the instructions [HERE]("http://raspisimon.no-ip.org/ups.php") to install it (not sure it was a bookmark I saved)

---

### Post by TheFu on 2014-01-22
Almost all temp files should be put into  ... er ... /tmp. It is cleaned up with every reboot.

Downloading files while root is asking for trouble ... begging for it really.

I'm still freaked out by the 8G under /root. Never heard of anyone using it that way.  root is meant to be used in an extremely limited way, not as the default userid.

"root", /root", /, and "file system" ARE NOT the same thing. There are times when they overlap and "root" is ambiguous.

/ - the root directory
/root - the HOME directory for the root userid; no other userid can view it normally.

---

### Post by jeanjd63 on 2014-01-22
/ and /root  are two things different 
Could you now do :
**sudo du -sh /root/* | sort -rh**

---

### Post by SuperFreak on 2014-01-22
> **jeanjd63 said:**
> / and /root  are two things different 
Could you now do :
**sudo du -sh /root/* | sort -rh**

result:
```
david@MainSqueeze:~$ sudo du -sh /root/* | sort -rh
[sudo] password for david: 
du: cannot access `/root/*': No such file or directory
david@MainSqueeze:~$ 

```

---

### Post by TheFu on 2014-01-22
> **SuperFreak said:**
> result:
```
david@MainSqueeze:~$ sudo du -sh /root/* | sort -rh
[sudo] password for david: 
du: cannot access `/root/*': No such file or directory
david@MainSqueeze:~$ 

```

The '*' gets expanded by the current userid - before sudo takes effect.  I'd do it this way (it looked fine to me before too).

```
sudo -s
du -sh /root/* | sort -rh

```
That works here.

---

### Post by jeanjd63 on 2014-01-22
And what return :
**sudo  ls  -l   /root/.local/share/Trash/files**

---

### Post by SuperFreak on 2014-01-22
@ The Fu
```
david@MainSqueeze:~$ sudo -s
[sudo] password for david: 
root@MainSqueeze:~# du -sh /root/* | sort -rh
28K	/root/Boot-Info_2013-04-21__19h04.txt
4.0K	/root/gparted_details.htm
4.0K	/root/Desktop
root@MainSqueeze:~# 




```

@jeandj63
```
david@MainSqueeze:~$ sudo ls -l /root/.local/share/Trash/files
[sudo] password for david: 
total 2566092
-rw-r--r-- 1 squeezeboxserver nogroup 655443968 Jul 28 23:07 artwork.2.db
-rw-r--r-- 1 squeezeboxserver nogroup 586689536 Jan 14 22:24 artwork.3.db
-rw-r--r-- 1 squeezeboxserver nogroup 599079936 Jun 25  2013 artwork.db
-rw-r--r-- 1 squeezeboxserver nogroup     32768 Jul 28 23:07 artwork.db-shm
-rw-r--r-- 1 squeezeboxserver nogroup    232688 Jul 28 20:41 artwork.db-wal
-rw-r--r-- 1 squeezeboxserver nogroup 137900032 Jan 14 22:24 cache.2.db
-rw-r--r-- 1 squeezeboxserver nogroup  14802944 Jun 25  2013 cache.db
-rw-r--r-- 1 squeezeboxserver nogroup      1715 Jan 14 22:24 cookies.2.dat
-rw-r--r-- 1 squeezeboxserver nogroup       910 Jun 25  2013 cookies.dat
drwxr-xr-x 7 root             root         4096 Nov  1  2012 cxoffice
-rw-r----- 1 squeezeboxserver nogroup     24576 Jun 25  2013 __db.001
-rw-r----- 1 squeezeboxserver nogroup    196608 Jun 25  2013 __db.002
-rw-r----- 1 squeezeboxserver nogroup    270336 Jun 25  2013 __db.003
-rw-r----- 1 squeezeboxserver nogroup     24576 Jan 14 21:57 __db.2.001
-rw-r----- 1 squeezeboxserver nogroup    196608 Jan 14 21:57 __db.2.002
-rw-r----- 1 squeezeboxserver nogroup    270336 Jan 14 21:57 __db.2.003
-rw-r--r-- 1 squeezeboxserver nogroup      8538 Sep  1 19:14 extrastrings.2.json
-rw-r--r-- 1 squeezeboxserver nogroup      8019 Apr 22  2013 extrastrings.json
-rw-r--r-- 1 squeezeboxserver nogroup      3072 Jun 25  2013 FileCache-InformationScreen-Mail-0.2.3183-Screens.db
-rw-r--r-- 1 squeezeboxserver nogroup      7168 Jun 25  2013 FileCache-InformationScreen-Mail-0.2.3183-ScreenTemplates.db
-rw-r--r-- 1 squeezeboxserver nogroup    113474 Dec  7 18:33 fontcache.2.x86_64-linux.bin
-rw-r--r-- 1 squeezeboxserver nogroup    113474 Jun 25  2013 fontcache.x86_64-linux.bin
-rw-r--r-- 1 squeezeboxserver nogroup 302809088 Jan 14 22:24 imgproxy.2.db
-rw-r--r-- 1 squeezeboxserver nogroup    125952 Jun 20  2013 imgproxy.db
-rw-r--r-- 1 squeezeboxserver nogroup     32768 Jun 25  2013 imgproxy.db-shm
-rw-r--r-- 1 squeezeboxserver nogroup         0 Jun 25  2013 imgproxy.db-wal
-rw-r--r-- 1 squeezeboxserver nogroup       731 Apr 22  2013 infobrowser.opml
-rw-r--r-- 1 squeezeboxserver nogroup       165 Apr 22  2013 infobrowser.opml.backup
-rw-r----- 1 squeezeboxserver nogroup   1335296 Jan 14 21:57 libmediascan.2.db
-rw-r----- 1 squeezeboxserver nogroup   1368064 Jun 24  2013 libmediascan.db
-rw-r--r-- 1 squeezeboxserver nogroup 133022720 Jan 14 22:24 library.2.db
-rw-r--r-- 1 squeezeboxserver nogroup 131540992 Jun 25  2013 library.db
-rwxrwxr-x 1 david            david         483 Jan 15 16:36 mmserver
-rw-r--r-- 1 squeezeboxserver nogroup  34197504 Jan 14 21:57 persist.2.db
-rw-r--r-- 1 squeezeboxserver nogroup  23901184 Jun 25  2013 persist.db
-rw-r--r-- 1 squeezeboxserver nogroup   1362944 Jan 14 16:16 PluginCache-CustomBrowse.2.db
-rw-r--r-- 1 squeezeboxserver nogroup   1360896 Jun 25  2013 PluginCache-CustomBrowse.db
-rw-r--r-- 1 squeezeboxserver nogroup     63488 Jun 25  2013 PluginCache-InformationScreen.db
-rw-r--r-- 1 squeezeboxserver nogroup     12288 Apr 22  2013 PluginCache-LicenseManagerPlugin.db
-rw-r--r-- 1 squeezeboxserver nogroup     63488 Jan 14 22:24 PluginCache-MultiLibrary.2.db
-rw-r--r-- 1 squeezeboxserver nogroup     79872 Jun 25  2013 PluginCache-MultiLibrary.db
-rw-r--r-- 1 squeezeboxserver nogroup    261120 Jan 14 16:16 PluginCache-SQLPlayList.2.db
-rw-r--r-- 1 squeezeboxserver nogroup    263168 Jun 25  2013 PluginCache-SQLPlayList.db
-rw-r--r-- 1 squeezeboxserver nogroup     33694 Dec  7 18:33 plugin-data.2.yaml
-rw-r--r-- 1 squeezeboxserver nogroup     36051 Jun 25  2013 plugin-data.yaml
-rw-r--r-- 1 root             root        11997 Dec 17 14:04 smb.conf
-rw-r--r-- 1 squeezeboxserver nogroup    100891 Jan 14 17:39 stringcache.2.x86_64-linux.bin
-rw-r--r-- 1 squeezeboxserver nogroup    211303 Jun 25  2013 stringcache.x86_64-linux.bin
drwxr-xr-x 3 root             root         4096 Oct 19 22:51 YUMI
david@MainSqueeze:~$ 

```

---

### Post by jeanjd63 on 2014-01-22
You have find where is the 8 Go size :
In the Trash of /root
The commands :
[B]sudo -s 
[/B][B][COLOR=#000000][FONT=Ubuntu Mono]du -sh /root/. | sort -rh
[/FONT][/COLOR][/B]will have give information i think.
You can now do :
**sudo  rm  /root/.local/share/Thrash/files/***

---

### Post by SuperFreak on 2014-01-22
> **jeanjd63 said:**
> You have find where is the 8 Go size :
In the Trash of /root
The commands :
[B]sudo -s 
[/B][B][COLOR=#000000][FONT=Ubuntu Mono]du -sh /root/. | sort -rh
[/FONT][/COLOR][/B]will have give information i think.
You can now do :
**sudo  rm  /root/.local/share/Thrash/files/***


I assume you meant Trash not Trash in the last command. It did not seem to work though
```
david@MainSqueeze:~$ sudo rm /root/.local/share/Trash/files/*
[sudo] password for david: 
rm: cannot remove `/root/.local/share/Trash/files/*': No such file or directory
david@MainSqueeze:~$ rm /root/.local/share/Trash/files/*
rm: cannot remove `/root/.local/share/Trash/files/*': Permission denied
david@MainSqueeze:~$ 


```

Curious what was in trash, so I ran:```
david@MainSqueeze:~$ sudo rm /root/.local/share/Trash/files/*
[sudo] password for david: 
rm: cannot remove `/root/.local/share/Trash/files/*': No such file or directory
david@MainSqueeze:~$ rm /root/.local/share/Trash/files/*
rm: cannot remove `/root/.local/share/Trash/files/*': Permission denied
david@MainSqueeze:~$ sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort
du: cannot access `/media/Documents/Documents/David/Tech/Computer/Addresses-Favorites/Thunderbird': No such file or directory
du: cannot access `Renee/Trash.sbd': No such file or directory
du: cannot access `/media/Documents/Documents/David/Tech/Computer/Addresses-Favorites/Thunderbird': No such file or directory
du: cannot access `Profile': No such file or directory
du: cannot access `TODAY/Trash.sbd': No such file or directory
du: cannot access `/media/Documents/Documents/David/Tech/Computer/Addresses-Favorites/Thunderbird': No such file or directory
du: cannot access `Archive': No such file or directory
du: cannot access `Renee/2013': No such file or directory
du: cannot access `08.sbd/Trash': No such file or directory
du: cannot access `/media/Documents/Documents/David/Tech/Computer/Addresses-Favorites/Thunderbird': No such file or directory
du: cannot access `Archive': No such file or directory
du: cannot access `Renee/2013': No such file or directory
du: cannot access `08/Trash.sbd': No such file or directory
du: cannot access `/media/Music/MP3/ROCK/Cooper,': No such file or directory
du: cannot access `Alice/23': No such file or directory
du: cannot access `-': No such file or directory
du: cannot access `Trash': No such file or directory
du: cannot access `1989': No such file or directory
103M	/root/.local/share/Trash/files/cxoffice/lib
104K	/root/.local/share/Trash/files/cxoffice/lib/perl/Parse
112K	/root/.local/share/Trash/files/cxoffice/share/icons/128x128
1.1M	/root/.local/share/Trash/files/cxoffice/lib/perl
12K	/home/david/.local/share/Trash/files/MusicIP.3/MusicIP Mixer2
12K	/root/.local/share/Trash/files/cxoffice/lib/perl/XML/Handler
12K	/root/.local/share/Trash/files/cxoffice/support/desktopdata/cxoffice-1/cxassoc/Scripts
1.2M	/root/.local/share/Trash/files/cxoffice/share/locale
133M	/root/.local/share/Trash/files/cxoffice
13M	/home/david/.local/share/Trash/files/MusicIP
13M	/home/david/.local/share/Trash/files/MusicIP.2
13M	/home/david/.local/share/Trash/files/MusicIP/MusicIP Mixer
144K	/root/.local/share/Trash/files/cxoffice/share/crossover/bottle_data
148K	/root/.local/share/Trash/files/cxoffice/share/crossover/bottle_templates
15M	/root/.local/share/Trash/files/cxoffice/lib/wine/fakedlls
15M	/root/.local/share/Trash/files/cxoffice/share/wine/gecko
164K	/home/.Trash-0/files/.2.thumbnails/normal
168K	/home/.Trash-0/files/.2.thumbnails
16K	/home/david/.local/share/Trash/files/MusicIP.3
16K	/media/Music/.Trash-1000
16K	/root/.local/share/Trash/files/cxoffice/share/locale/it/LC_MESSAGES
16K	/root/.local/share/Trash/files/YUMI/boot/grub/locale
1.6M	/root/.local/share/Trash/files/cxoffice/lib/python
172K	/home/.Trash-0/files
1.9M	/root/.local/share/Trash/files/YUMI/boot/grub
208K	/root/.local/share/Trash/info
20K	/root/.local/share/Trash/files/cxoffice/lib/perl/XML/DOM
20K	/root/.local/share/Trash/files/cxoffice/share/locale/it
20K	/root/.local/share/Trash/files/cxoffice/support/desktopdata/cxoffice-1/cxassoc
2.0M	/root/.local/share/Trash/files/cxoffice/bin
20M	/root/.local/share/Trash/files/cxoffice/share/wine
2.1M	/root/.local/share/Trash/files/cxoffice/share/images
244K	/home/.Trash-0
24K	/home/david/.local/share/Trash/files/MusicIP Mixer/examples
24K	/media/Videos/.Trash-1000
24K	/root/.local/share/Trash/files/cxoffice/lib/perl/XML/SAX/PurePerl/Reader
24K	/root/.local/share/Trash/files/cxoffice/share/icons/16x16
24K	/root/.local/share/Trash/files/cxoffice/support/desktopdata/cxoffice-0/cxassoc/Scripts
24K	/root/.local/share/Trash/files/cxoffice/support/desktopdata/cxoffice-1
252K	/home/david/.local/share/Trash/files/MusicIP Mixer/skin
256K	/root/.local/share/Trash/files/cxoffice/lib/perl/XML/SAX
25M	/home/david/.local/share/Trash/files/MusicIP Mixer
268K	/root/.local/share/Trash/files/cxoffice/share/icons/256x256
27M	/home/david/.local/share/Trash/files/.MusicMagic
28K	/root/.local/share/Trash/files/cxoffice/share/icons/32x32
29M	/root/.local/share/Trash/files/cxoffice/share
312K	/root/.local/share/Trash/files/cxoffice/lib/python/glade
32K	/root/.local/share/Trash/files/cxoffice/etc
32K	/root/.local/share/Trash/files/cxoffice/lib/perl/Parse/Win32Registry/Win95
32K	/root/.local/share/Trash/files/cxoffice/lib/perl/Parse/Win32Registry/WinNT
32K	/root/.local/share/Trash/files/cxoffice/support/desktopdata/cxoffice-0/cxassoc
36K	/media/Documents/.Trash-1000/expunged/2817812527/gnomecatalog-0.3.4.2/build/mo
36K	/root/.local/share/Trash/files/cxoffice/share/crossover/bottle_templates/win2000
36K	/root/.local/share/Trash/files/cxoffice/share/crossover/bottle_templates/win98
36K	/root/.local/share/Trash/files/cxoffice/share/crossover/bottle_templates/winvista
36K	/root/.local/share/Trash/files/cxoffice/share/crossover/bottle_templates/winxp
36K	/root/.local/share/Trash/files/cxoffice/support/desktopdata/cxoffice-0
4.0K	/home/david/.local/share/Trash/expunged
4.0K	/home/david/.local/share/Trash/files/MusicIP.2/moods
4.0K	/home/david/.local/share/Trash/files/MusicIP/MusicIP Mixer/djs
4.0K	/home/david/.local/share/Trash/files/.MusicMagic/djs
40K	/media/Documents/.Trash-1000/expunged/2817812527/gnomecatalog-0.3.4.2/build
4.0K	/media/Documents/.Trash-1000/files
4.0K	/media/Documents/.Trash-1000/info
4.0K	/media/Music/.Trash-1000/expunged
4.0K	/media/Music/.Trash-1000/files
4.0K	/media/Music/.Trash-1000/info
4.0K	/media/Videos/.Trash-1000/expunged
4.0K	/media/Videos/.Trash-1000/files
4.0K	/root/.local/share/Trash/files/cxoffice/lib/perl/XML/lib/XML
4.0K	/root/.local/share/Trash/files/cxoffice/support/desktopdata/cxoffice-0/cxassoc/tagged_icons
4.0K	/root/.local/share/Trash/files/cxoffice/support/desktopdata/cxoffice-1/cxassoc/tagged_icons
4.2M	/home/david/.local/share/Trash/files/MusicIP.2/lib
44K	/media/Documents/.Trash-1000/expunged/2817812527/gnomecatalog-0.3.4.2
452K	/root/.local/share/Trash/files/cxoffice/lib/perl/XML
4.7M	/root/.local/share/Trash/files/cxoffice/share/crossover/data
48K	/media/Documents/.Trash-1000/expunged/2817812527
48K	/root/.local/share/Trash/files/cxoffice/share/icons/64x64
48K	/root/.local/share/Trash/files/cxoffice/share/locale/sk/LC_MESSAGES
52K	/media/Documents/.Trash-1000/expunged
52K	/root/.local/share/Trash/files/cxoffice/share/locale/sk
5.2M	/root/.local/share/Trash/files/cxoffice/share/crossover
5.3G	/root/.local/share/Trash/files/YUMI
5.3G	/root/.local/share/Trash/files/YUMI/boot
5.3G	/root/.local/share/Trash/files/YUMI/boot/isos
544K	/root/.local/share/Trash/files/cxoffice/share/icons
548K	/home/david/.local/share/Trash/files/MusicIP Mixer/help/graphics
560K	/home/david/.local/share/Trash/files/MusicIP Mixer/help
56K	/home/david/.local/share/Trash/info
5.7M	/root/.local/share/Trash/files/cxoffice/share/wine/fonts
60K	/root/.local/share/Trash/files/cxoffice/share/icons/48x48
64K	/media/Documents/.Trash-1000
64K	/root/.local/share/Trash/files/cxoffice/support/desktopdata
68K	/home/.Trash-0/info
68K	/root/.local/share/Trash/files/cxoffice/share/locale/pt/LC_MESSAGES
68K	/root/.local/share/Trash/files/cxoffice/support
72K	/root/.local/share/Trash/files/cxoffice/share/crossover/cxrepackage
72K	/root/.local/share/Trash/files/cxoffice/share/locale/nl/LC_MESSAGES
72K	/root/.local/share/Trash/files/cxoffice/share/locale/pt
72K	/root/.local/share/Trash/files/cxoffice/share/locale/zh_CN/LC_MESSAGES
76K	/root/.local/share/Trash/files/cxoffice/lib/perl/Parse/Win32Registry
76K	/root/.local/share/Trash/files/cxoffice/share/crossover/cxbottle
76K	/root/.local/share/Trash/files/cxoffice/share/locale/cs/LC_MESSAGES
76K	/root/.local/share/Trash/files/cxoffice/share/locale/lt/LC_MESSAGES
76K	/root/.local/share/Trash/files/cxoffice/share/locale/nl
76K	/root/.local/share/Trash/files/cxoffice/share/locale/pt_BR/LC_MESSAGES
76K	/root/.local/share/Trash/files/cxoffice/share/locale/sv/LC_MESSAGES
76K	/root/.local/share/Trash/files/cxoffice/share/locale/zh_CN
77M	/home/david/.local/share/Trash
77M	/home/david/.local/share/Trash/files
7.9G	/root/.local/share/Trash
7.9G	/root/.local/share/Trash/files
8.0K	/home/david/.local/share/Trash/files/MusicIP.2/server
8.0K	/home/david/.local/share/Trash/files/MusicIP Mixer/server
8.0K	/media/Documents/.Trash-1000/expunged/2817812527/gnomecatalog-0.3.4.2/build/mo/de
8.0K	/media/Documents/.Trash-1000/expunged/2817812527/gnomecatalog-0.3.4.2/build/mo/en
8.0K	/media/Documents/.Trash-1000/expunged/2817812527/gnomecatalog-0.3.4.2/build/mo/es
8.0K	/media/Documents/.Trash-1000/expunged/2817812527/gnomecatalog-0.3.4.2/build/mo/pl
8.0K	/media/Videos/.Trash-1000/info
8.0K	/root/.local/share/Trash/files/cxoffice/lib/perl/XML/lib
80K	/root/.local/share/Trash/files/cxoffice/share/locale/cs
80K	/root/.local/share/Trash/files/cxoffice/share/locale/de/LC_MESSAGES
80K	/root/.local/share/Trash/files/cxoffice/share/locale/es/LC_MESSAGES
80K	/root/.local/share/Trash/files/cxoffice/share/locale/fr/LC_MESSAGES
80K	/root/.local/share/Trash/files/cxoffice/share/locale/lt
80K	/root/.local/share/Trash/files/cxoffice/share/locale/pl/LC_MESSAGES
80K	/root/.local/share/Trash/files/cxoffice/share/locale/pt_BR
80K	/root/.local/share/Trash/files/cxoffice/share/locale/sv
84K	/root/.local/share/Trash/files/cxoffice/share/locale/de
84K	/root/.local/share/Trash/files/cxoffice/share/locale/es
84K	/root/.local/share/Trash/files/cxoffice/share/locale/fr
84K	/root/.local/share/Trash/files/cxoffice/share/locale/pl
88K	/root/.local/share/Trash/files/cxoffice/share/locale/ja/LC_MESSAGES
92K	/root/.local/share/Trash/files/cxoffice/lib/perl/XML/SAX/PurePerl
92K	/root/.local/share/Trash/files/cxoffice/share/locale/ja
92K	/root/.local/share/Trash/files/cxoffice/share/locale/ru/LC_MESSAGES
96K	/root/.local/share/Trash/files/cxoffice/share/locale/ru
99M	/root/.local/share/Trash/files/cxoffice/lib/wine
david@MainSqueeze:~$ 

```

It is mostly small files except for obne several GB in size YUMI. Which was an attempt at making a multiboot USB. Obviously the wrong way

---

### Post by SuperFreak on 2014-01-22
I used ```
gksudo nautilus /root/.local/share/Trash/files
```
Then I permanently deleted all files
My Root is now as below
```
david@MainSqueeze:~$ sudo du -shx /* | sort -rh
du: cannot access `/home/david/.gvfs': Permission denied
du: cannot access `/proc/29101/task/29101/fd/3': No such file or directory
du: cannot access `/proc/29101/task/29101/fdinfo/3': No such file or directory
du: cannot access `/proc/29101/fd/3': No such file or directory
du: cannot access `/proc/29101/fdinfo/3': No such file or directory
6.5G	/home
4.4G	/usr
2.1G	/var
1.5G	/opt
542M	/lib
145M	/boot
59M	/root
17M	/etc
9.3M	/sbin
8.9M	/bin
4.0M	/ubiquity-apt-clone
3.4M	/lib32
1.3M	/run
116K	/gapcmon-0.8.2.tar.bz2
100K	/tmp
36K	/mnt
20K	/media
16K	/lost+found
12K	/gapcmon.spec
4.0K	/srv
4.0K	/selinux
4.0K	/lib64
4.0K	/dev
4.0K	/dead.letter
4.0K	/cdrom
0	/vmlinuz.old
0	/vmlinuz
0	/sys
0	/proc
0	/initrd.img.old
0	/initrd.img
david@MainSqueeze:~$ 

```

This seems to be more like what I would expect. Thanks for your help.

GParted now reports Root as 9.34 GB which seems right

---

### Post by TheFu on 2014-01-22
Using sudo with regex in locked down directories doesn't work.
Running GUI programs, like nautilus, as root can be very hazardous to your personal settings.

The reason the du cmd didn't find large directories under /root - even after you had changed to the root uid is because '*' does NOT match on .* ... that means that any files which begin with a '.' are hidden until explicitly requested.
```

sudo -s
du -sh /root/.[A-z]* /root/*
```
That should work.  Make sense?

---

### Post by SuperFreak on 2014-01-22
> **TheFu said:**
> Using sudo with regex in locked down directories doesn't work.
Running GUI programs, like nautilus, as root can be very hazardous to your personal settings.

The reason the du cmd didn't find large directories under /root - even after you had changed to the root uid is because '*' does NOT match on .* ... that means that any files which begin with a '.' are hidden until explicitly requested.
```

sudo -s
du -sh /root/.[A-z]* /root/*
```
That should work.  Make sense?

Makes sense, but surely there is no risk using nautilus if I am deleting files out of Trash? I know CLI is the way to go but i have a long way to go before I understand the cli interface

---

### Post by TheFu on 2014-01-22
> **SuperFreak said:**
> Makes sense, but surely there is no risk using nautilus if I am deleting files out of Trash? I know CLI is the way to go but i have a long way to go before I understand the cli interface

Suppose a nautilus setting is changed and you are using an effective UID of root, but your HOME is still /home/user5  - where do you think that setting will be placed?  Where does the "last used" get stored?  Do you believe the setting file(s) wouldn't be owned by root and set with a umask of 077?   

Next time you run nautilus as yourself. The setting file is there - owned by root and cannot be read. Does nautilus keep working or crash?

Imagine every GUI program with a setting file doing the same thing every time you use sudo. Not good.
At some point the settings will be screwed up enough that only a new userid will fix it.  These forums have hundreds of "program X doesn't work anymore" issues that nobody figures out. Either they make a new userid or they reinstall everything ... because is isn't happening to people like me.

Not every GUI program will do this, but there isn't an easy way to determine which will and which will not. By the time you notice the issue, you will have forgotten about running the program under sudo.

---

### Post by SuperFreak on 2014-01-22
I guess I have always taken the most obvious path with Ubuntu out of fear that I might issue a command that was wrong and did some damage to the OS. I didn't realize such a risk existed with gksudo nautilus which I have used with some frequency (to  the point of having a launcher for it). I guess I am going to have to tread much more carefully and get more accustomed to terminal commands, but I must confess it is all greek to me now. I will try and do some reading, I think I have a document I pulled off of the web of terminal commands

---

### Post by SuperFreak on 2014-02-08
> **TheFu said:**
> Using sudo with regex in locked down directories doesn't work.
Running GUI programs, like nautilus, as root can be very hazardous to your personal settings.

The reason the du cmd didn't find large directories under /root - even after you had changed to the root uid is because '*' does NOT match on .* ... that means that any files which begin with a '.' are hidden until explicitly requested.
```

sudo -s
du -sh /root/.[A-z]* /root/*
```
That should work.  Make sense?

not sure if you will see this as it is an old thread that was solved. I had a look at the command "gksudo" I used and am under the impression it is the correct command to use for graphical applications like nautilus under root. Are you sure you are correct about your comment? I have used gksudo for several years to use nautilus to go into the filesystem and remove or add files

---

### Post by TheFu on 2014-02-08
It all depends on whether gksudo changes the $HOME or not. It shouldn't, but ... 

Application settings are stored based off  the $HOME environment variable ... so if root is the effective userid, but HOME is set to /home/userid-someone ... then root will own the settings.  I've seen this mainly with GUI backup tools like Back-in-Time, but **any** GUI tool that creates a settings file will do the same thing.  If the settings files pre-exist and no preferences are modified (or automatically created) by any clicks in the software, then nothing bad should happen.  More and more, it is hard to tell when/if any GUI program will do that sort of stuff or not since more and more of them don't have OK/Apply buttons, but auto-save ... thanks to the way Canonical is trying to make things more intuitive.  A blessing AND a curse.

---

### Post by SuperFreak on 2014-02-08
This is why I have used gksudo this way although from what you are saying using it in /root is dangerous but I assume iy is OK for other system file diretories such as USR, VAR, etc([https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo"))> 
Graphical sudo

You should never use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on Kubuntu) to run such programs. gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by Root. (AFAICT, this is all that's special about the environment of the started process with gksudo vs. sudo).

Examples:

gksudo gedit /etc/fstab

or

kdesudo kate /etc/X11/xorg.conf

    To run the graphical configuration utilities, simply launch the application via the Administration menu.

    gksudo and kdesudo simply link to the commands gksu and kdesu

---

