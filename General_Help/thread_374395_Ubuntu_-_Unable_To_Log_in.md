---
title: "Ubuntu - Unable To Log in"
date: 2007-03-02
forum: General Help
---

### Post by Virgo53 on 2007-03-02
At log in I get the following message:

GDM could not write to your authorization file. This could mean that you are out of disk
space or that your home directory could not be opened for writing. In any case, it is
not possible to log in. Please contact your system administrator.

Ubuntu resides on a 10 GB partition created using gparted (8.75 GB and 1.25 GB swap)
The boot menu looks like this:

GNU GRUB version 0.97
(639 K /owner/523008 K upper memory)

Ubuntu, kernel 2.6.15-28-386
Ubuntu, kernel 2.6.15-28-386 (recovery mode)
Ubuntu, kernel 2.6.15-27-386
Ubuntu, kernel 2.6.15-27-386 (recovery mode)
Ubuntu, kernel 2.6.15-23-386
Ubuntu, kernel 2.6.15-23-386 (recovery mode)
Ubuntu, memtest86+

Other Operating Systems:

Windows NT/2000/XP
Microsoft Windows XP Professional Edition

What steps should be followed  to fix my login problem?  What can be safely deleted to free up disk space? Is there a program for searching for and eliminating duplicate files? I had no idea that once all the disk space is used that I would not be able to login again. Thanks for any help on this!

---

### Post by taurus on 2007-03-02
Boot into recovery mode, Ubuntu, kernel 2.6.15-28-386 (recovery mode), and at the prompt, post the output of this command?

```
df   -h
```

---

### Post by Paerez on 2007-03-02
run:
```
sudo aptitude clean
```
That will delete the archives for installed packages. Ubuntu automatically saves them, even though you don't usually need them.

---

### Post by Virgo53 on 2007-03-02
Here's the results of running the command df -h:

Filesystem       Size       Used      Avail       Use%       Mounted on

/dev/hda3       8.7G       8.3G        0          100%            /
varrun            252M       12K       252M         1%           /var/run
varlock           252M       4.0K      252M         1%           /var/lock
udev               252M      184K      252M         1%          /dev
devshm           252M        0         252M         0%          /dev/shm
lrm                 252M        19M      234M         8%         /lib/modules/2.6.15-28-386/volatile
/dev/hda1        6.3G       5.5G      830M        88%        /media/hda1
/dev/hda2       133G       94G         40G        71%        /media/hda2

Can the earlier versions of Ubuntu  be deleted without compromising the latest version?

---

### Post by taurus on 2007-03-02
I guess you know that you are running out of space on /.

```
/dev/hda3 8.7G 8.3G 0 100% /
```
Therefore, you need to boot into recovery mode again and clean out the cache.

```
aptitude clean
df -h
```
And yes, you can remove the old kernel(s) if you wish to free up more space.

---

### Post by Virgo53 on 2007-03-03
Yes, I'm well aware that / is maxed out. I ran sudo aptitude clean as suggested by Paerez,
and the results read:

Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done

What's the best and/or proper way of removing the old kernel versions (2.6.15-23-386 and 
2.6.15-27-386) so that nothing gets fouled up with 2.6.15-28-386?
 I guess what I'm trying to say here is are the three kernel versions I'm running totally and separately independent of each other and the older kernel versions are just taking up hard drive space?

---

### Post by Paerez on 2007-03-03
the old ones are taking up space. Only the one you choose to boot is being used.

---

### Post by Virgo53 on 2007-03-04
After running aptitude clean I was able to log in normally, but only have about 10MB
of hard drive space available. I searched through lots of documentation looking for 
the command(s) to free up some hard drive space without finding anything on the subject.

I'm not sure about how to delete the old kernel versions or how to update Grub after they're gone.?????

---

### Post by taurus on 2007-03-04
What's the output of this command from a terminal?

```
sudo du -h /var
```

---

### Post by Virgo53 on 2007-03-04
ricvic@ricvic-desktop:~$ sudo du -h /var
Password:
0       /var/lock/lvm
4.0K    /var/lock
0       /var/run/sudo/ricvic
0       /var/run/sudo
0       /var/run/console
4.0K    /var/run/clamav
4.0K    /var/run/cups/certs
8.0K    /var/run/cups
16K     /var/run/hplip
4.0K    /var/run/avahi-daemon
4.0K    /var/run/hal
4.0K    /var/run/dbus
8.0K    /var/run/klogd
0       /var/run/screen
4.0K    /var/run/network
88K     /var/run
3.3M    /var/backups
4.0K    /var/cache/apt/archives/partial
24K     /var/cache/apt/archives
15M     /var/cache/apt
4.0K    /var/cache/cups/ppd
3.3M    /var/cache/cups
3.4M    /var/cache/debconf
28K     /var/cache/dictionaries-common
4.0K    /var/cache/gnome-system-tools/backup
8.0K    /var/cache/gnome-system-tools
4.0K    /var/cache/locate
4.0K    /var/cache/man/X11R6
4.0K    /var/cache/man/cat1
4.0K    /var/cache/man/cat2
4.0K    /var/cache/man/cat3
4.0K    /var/cache/man/cat4
4.0K    /var/cache/man/cat5
4.0K    /var/cache/man/cat6
4.0K    /var/cache/man/cat7
4.0K    /var/cache/man/cat8
4.0K    /var/cache/man/cat9
4.0K    /var/cache/man/fsstnd
4.0K    /var/cache/man/local
4.0K    /var/cache/man/oldlocal
4.0K    /var/cache/man/opt
568K    /var/cache/man
4.0K    /var/cache/pppconfig
40K     /var/cache/setup-tool-backends/debug/time/1
40K     /var/cache/setup-tool-backends/debug/time/2
40K     /var/cache/setup-tool-backends/debug/time/3
124K    /var/cache/setup-tool-backends/debug/time
8.0K    /var/cache/setup-tool-backends/debug/disks/1
8.0K    /var/cache/setup-tool-backends/debug/disks/2
28K     /var/cache/setup-tool-backends/debug/disks/3
48K     /var/cache/setup-tool-backends/debug/disks
176K    /var/cache/setup-tool-backends/debug
8.0K    /var/cache/setup-tool-backends/backup/time/First/etc
12K     /var/cache/setup-tool-backends/backup/time/First
12K     /var/cache/setup-tool-backends/backup/time/1/etc
16K     /var/cache/setup-tool-backends/backup/time/1
8.0K    /var/cache/setup-tool-backends/backup/time/2/etc
12K     /var/cache/setup-tool-backends/backup/time/2
44K     /var/cache/setup-tool-backends/backup/time
48K     /var/cache/setup-tool-backends/backup
228K    /var/cache/setup-tool-backends
4.0K    /var/cache/beagle/indexes/applications/Locks
1.5M    /var/cache/beagle/indexes/applications/PrimaryIndex
8.0K    /var/cache/beagle/indexes/applications/SecondaryIndex
1.6M    /var/cache/beagle/indexes/applications
4.0K    /var/cache/beagle/indexes/documentation/Locks
3.7M    /var/cache/beagle/indexes/documentation/PrimaryIndex
8.0K    /var/cache/beagle/indexes/documentation/SecondaryIndex
4.5M    /var/cache/beagle/indexes/documentation
6.0M    /var/cache/beagle/indexes
6.0M    /var/cache/beagle
29M     /var/cache
4.0K    /var/games
20K     /var/lib/acpi-support
76K     /var/lib/alsa
4.0K    /var/lib/apt/lists/partial
28M     /var/lib/apt/lists
4.0K    /var/lib/apt/periodic
28M     /var/lib/apt
4.0K    /var/lib/aptitude
3.5M    /var/lib/aspell
52K     /var/lib/belocs
4.0K    /var/lib/bittorrent
20K     /var/lib/defoma/fontconfig.d/A
20K     /var/lib/defoma/fontconfig.d/B
44K     /var/lib/defoma/fontconfig.d/C
108K    /var/lib/defoma/fontconfig.d/D
8.0K    /var/lib/defoma/fontconfig.d/E
24K     /var/lib/defoma/fontconfig.d/F
28K     /var/lib/defoma/fontconfig.d/G
16K     /var/lib/defoma/fontconfig.d/H
8.0K    /var/lib/defoma/fontconfig.d/J
16K     /var/lib/defoma/fontconfig.d/K
20K     /var/lib/defoma/fontconfig.d/L
68K     /var/lib/defoma/fontconfig.d/M
24K     /var/lib/defoma/fontconfig.d/N
8.0K    /var/lib/defoma/fontconfig.d/O
16K     /var/lib/defoma/fontconfig.d/P
8.0K    /var/lib/defoma/fontconfig.d/R
12K     /var/lib/defoma/fontconfig.d/S
40K     /var/lib/defoma/fontconfig.d/T
16K     /var/lib/defoma/fontconfig.d/U
12K     /var/lib/defoma/fontconfig.d/V
12K     /var/lib/defoma/fontconfig.d/a
12K     /var/lib/defoma/fontconfig.d/j
12K     /var/lib/defoma/fontconfig.d/m
8.0K    /var/lib/defoma/fontconfig.d/u
8.0K    /var/lib/defoma/fontconfig.d/W
8.0K    /var/lib/defoma/fontconfig.d/I
8.0K    /var/lib/defoma/fontconfig.d/f
8.0K    /var/lib/defoma/fontconfig.d/p
788K    /var/lib/defoma/fontconfig.d
4.0K    /var/lib/defoma/gs.d/dirs/CMap
256K    /var/lib/defoma/gs.d/dirs/fonts
264K    /var/lib/defoma/gs.d/dirs
436K    /var/lib/defoma/gs.d
228K    /var/lib/defoma/libwmf0.2-7.d
292K    /var/lib/defoma/pango.d
68K     /var/lib/defoma/scripts
4.0K    /var/lib/defoma/x-ttcidfont-conf.d/dirs/CID
436K    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
444K    /var/lib/defoma/x-ttcidfont-conf.d/dirs
1.2M    /var/lib/defoma/x-ttcidfont-conf.d
3.8M    /var/lib/defoma
12K     /var/lib/dhcp3
8.0K    /var/lib/dictionaries-common/aspell
12K     /var/lib/dictionaries-common/wordlist
24K     /var/lib/dictionaries-common
4.0K    /var/lib/discover
376K    /var/lib/doc-base/info
380K    /var/lib/doc-base
308K    /var/lib/dpkg/alternatives
31M     /var/lib/dpkg/info
4.0K    /var/lib/dpkg/methods/disk
4.0K    /var/lib/dpkg/methods/floppy
4.0K    /var/lib/dpkg/methods/mnt
16K     /var/lib/dpkg/methods
4.0K    /var/lib/dpkg/parts
4.0K    /var/lib/dpkg/updates
36M     /var/lib/dpkg
4.0K    /var/lib/fontconfig
1.4M    /var/lib/gcj-4.1
8.0K    /var/lib/gconf/debian.defaults
43M     /var/lib/gconf/defaults
43M     /var/lib/gconf
16K     /var/lib/gdm
4.0K    /var/lib/gstreamer/0.10
8.0K    /var/lib/gstreamer
16K     /var/lib/initramfs-tools
12K     /var/lib/locales/supported.d
16K     /var/lib/locales
8.0K    /var/lib/logrotate
524K    /var/lib/misc
8.0K    /var/lib/mozilla-firefox/extensions.d
12K     /var/lib/mozilla-firefox
8.0K    /var/lib/mozilla-thunderbird/extensions.d
12K     /var/lib/mozilla-thunderbird
188K    /var/lib/scrollkeeper/C
60K     /var/lib/scrollkeeper/af
68K     /var/lib/scrollkeeper/am
60K     /var/lib/scrollkeeper/an
60K     /var/lib/scrollkeeper/ar
60K     /var/lib/scrollkeeper/as
60K     /var/lib/scrollkeeper/az
72K     /var/lib/scrollkeeper/be
84K     /var/lib/scrollkeeper/bg
80K     /var/lib/scrollkeeper/bn
60K     /var/lib/scrollkeeper/br
60K     /var/lib/scrollkeeper/bs
68K     /var/lib/scrollkeeper/ca
60K     /var/lib/scrollkeeper/co
80K     /var/lib/scrollkeeper/cs
60K     /var/lib/scrollkeeper/cy
68K     /var/lib/scrollkeeper/da
104K    /var/lib/scrollkeeper/de
72K     /var/lib/scrollkeeper/el
60K     /var/lib/scrollkeeper/en
60K     /var/lib/scrollkeeper/en_GB
60K     /var/lib/scrollkeeper/eo
128K    /var/lib/scrollkeeper/es
76K     /var/lib/scrollkeeper/et
64K     /var/lib/scrollkeeper/eu
60K     /var/lib/scrollkeeper/fa
68K     /var/lib/scrollkeeper/fi
60K     /var/lib/scrollkeeper/fo
116K    /var/lib/scrollkeeper/fr
60K     /var/lib/scrollkeeper/ga
60K     /var/lib/scrollkeeper/gl
60K     /var/lib/scrollkeeper/gu
76K     /var/lib/scrollkeeper/he
68K     /var/lib/scrollkeeper/hr
80K     /var/lib/scrollkeeper/hu
60K     /var/lib/scrollkeeper/hy
60K     /var/lib/scrollkeeper/ia
80K     /var/lib/scrollkeeper/id
60K     /var/lib/scrollkeeper/is
108K    /var/lib/scrollkeeper/it
92K     /var/lib/scrollkeeper/ja
68K     /var/lib/scrollkeeper/ka
60K     /var/lib/scrollkeeper/kk
64K     /var/lib/scrollkeeper/kn
104K    /var/lib/scrollkeeper/ko
60K     /var/lib/scrollkeeper/ku
60K     /var/lib/scrollkeeper/ky
60K     /var/lib/scrollkeeper/lb
60K     /var/lib/scrollkeeper/lg
60K     /var/lib/scrollkeeper/li
60K     /var/lib/scrollkeeper/lo
72K     /var/lib/scrollkeeper/lt
60K     /var/lib/scrollkeeper/lv
60K     /var/lib/scrollkeeper/mg
60K     /var/lib/scrollkeeper/mi
60K     /var/lib/scrollkeeper/ml
60K     /var/lib/scrollkeeper/mn
60K     /var/lib/scrollkeeper/mr
60K     /var/lib/scrollkeeper/ms
60K     /var/lib/scrollkeeper/my
76K     /var/lib/scrollkeeper/nb
60K     /var/lib/scrollkeeper/ne
84K     /var/lib/scrollkeeper/nl
60K     /var/lib/scrollkeeper/nn
60K     /var/lib/scrollkeeper/no
68K     /var/lib/scrollkeeper/oc
60K     /var/lib/scrollkeeper/or
60K     /var/lib/scrollkeeper/pa
80K     /var/lib/scrollkeeper/pl
80K     /var/lib/scrollkeeper/pt
80K     /var/lib/scrollkeeper/pt_BR
60K     /var/lib/scrollkeeper/rm
88K     /var/lib/scrollkeeper/ro
100K    /var/lib/scrollkeeper/ru
60K     /var/lib/scrollkeeper/rw
60K     /var/lib/scrollkeeper/se
60K     /var/lib/scrollkeeper/si
80K     /var/lib/scrollkeeper/sk
68K     /var/lib/scrollkeeper/sl
60K     /var/lib/scrollkeeper/sq
72K     /var/lib/scrollkeeper/sr
60K     /var/lib/scrollkeeper/sr@Latn
104K    /var/lib/scrollkeeper/sv
60K     /var/lib/scrollkeeper/sw
60K     /var/lib/scrollkeeper/ta
60K     /var/lib/scrollkeeper/te
60K     /var/lib/scrollkeeper/tg
88K     /var/lib/scrollkeeper/th
60K     /var/lib/scrollkeeper/tk
68K     /var/lib/scrollkeeper/tl
80K     /var/lib/scrollkeeper/tr
60K     /var/lib/scrollkeeper/ug
100K    /var/lib/scrollkeeper/uk
80K     /var/lib/scrollkeeper/ur
60K     /var/lib/scrollkeeper/uz
60K     /var/lib/scrollkeeper/vi
60K     /var/lib/scrollkeeper/wa
60K     /var/lib/scrollkeeper/wo
60K     /var/lib/scrollkeeper/xh
60K     /var/lib/scrollkeeper/yi
60K     /var/lib/scrollkeeper/yo
100K    /var/lib/scrollkeeper/zh_CN
96K     /var/lib/scrollkeeper/zh_TW
60K     /var/lib/scrollkeeper/zu
1.6M    /var/lib/scrollkeeper/TOC
1.2M    /var/lib/scrollkeeper/index
10M     /var/lib/scrollkeeper
8.0K    /var/lib/pango
28K     /var/lib/gnome/Debian/Apps/Databases
20K     /var/lib/gnome/Debian/Apps/Editors
28K     /var/lib/gnome/Debian/Apps/Graphics
28K     /var/lib/gnome/Debian/Apps/Math
16K     /var/lib/gnome/Debian/Apps/Net/Mozilla Components
84K     /var/lib/gnome/Debian/Apps/Net
36K     /var/lib/gnome/Debian/Apps/Programming
20K     /var/lib/gnome/Debian/Apps/Shells
40K     /var/lib/gnome/Debian/Apps/Sound
16K     /var/lib/gnome/Debian/Apps/System/Admin
12K     /var/lib/gnome/Debian/Apps/System/Gnome
156K    /var/lib/gnome/Debian/Apps/System
20K     /var/lib/gnome/Debian/Apps/Text
32K     /var/lib/gnome/Debian/Apps/Tools
36K     /var/lib/gnome/Debian/Apps/Viewers
536K    /var/lib/gnome/Debian/Apps
12K     /var/lib/gnome/Debian/Games/Arcade
32K     /var/lib/gnome/Debian/Games/Board
20K     /var/lib/gnome/Debian/Games/Card
32K     /var/lib/gnome/Debian/Games/Puzzles
12K     /var/lib/gnome/Debian/Games/Tetris-like
116K    /var/lib/gnome/Debian/Games
16K     /var/lib/gnome/Debian/Help
20K     /var/lib/gnome/Debian/XShells
692K    /var/lib/gnome/Debian
696K    /var/lib/gnome
8.0K    /var/lib/mozilla/chrome/overlayinfo/communicator/content
12K     /var/lib/mozilla/chrome/overlayinfo/communicator
8.0K    /var/lib/mozilla/chrome/overlayinfo/navigator/content
12K     /var/lib/mozilla/chrome/overlayinfo/navigator
8.0K    /var/lib/mozilla/chrome/overlayinfo/messenger/content
12K     /var/lib/mozilla/chrome/overlayinfo/messenger
40K     /var/lib/mozilla/chrome/overlayinfo
84K     /var/lib/mozilla/chrome
20K     /var/lib/mozilla/chrome.d
228K    /var/lib/mozilla/components
336K    /var/lib/mozilla
4.0K    /var/lib/sgml-base
1.4M    /var/lib/slocate
4.0K    /var/lib/snmp
4.0K    /var/lib/synaptic
20K     /var/lib/ucf/cache
48K     /var/lib/ucf
8.0K    /var/lib/update-manager
4.0K    /var/lib/update-notifier/user.d
8.0K    /var/lib/update-notifier
8.0K    /var/lib/urandom
28K     /var/lib/x11
4.0K    /var/lib/xkb
36K     /var/lib/xml-core
24K     /var/lib/pdmenu
504K    /var/lib/menu-xdg/applications/menu-xdg
508K    /var/lib/menu-xdg/applications
8.0K    /var/lib/menu-xdg/menus
100K    /var/lib/menu-xdg/desktop-directories/menu-xdg
104K    /var/lib/menu-xdg/desktop-directories
624K    /var/lib/menu-xdg
12K     /var/lib/binfmts
8.0K    /var/lib/msttcorefonts
4.0K    /var/lib/ntp
8.8M    /var/lib/clamav
139M    /var/lib
4.0K    /var/local
176K    /var/log/cups
24K     /var/log/gdm
4.0K    /var/log/news
4.0K    /var/log/unattended-upgrades
148K    /var/log/installer
4.0K    /var/log/ntpstats
164K    /var/log/clamav
2.7M    /var/log
4.0K    /var/mail
4.0K    /var/opt
16K     /var/spool/anacron
8.0K    /var/spool/cron/atjobs
4.0K    /var/spool/cron/atspool
4.0K    /var/spool/cron/crontabs
20K     /var/spool/cron
4.0K    /var/spool/cups/tmp
44K     /var/spool/cups
4.0K    /var/spool/openoffice/uno_packages/cache
8.0K    /var/spool/openoffice/uno_packages
12K     /var/spool/openoffice
96K     /var/spool
4.0K    /var/tmp
1.5G    /var/backup/2006-11-21_15.36.54.131479.ricvic-desktop.ful
31M     /var/backup/2006-11-22_00.00.02.733286.ricvic-desktop.inc
30M     /var/backup/2006-11-23_00.00.03.007139.ricvic-desktop.inc
20M     /var/backup/2006-11-24_00.00.02.741876.ricvic-desktop.inc
15M     /var/backup/2006-11-25_00.00.02.474418.ricvic-desktop.inc
17M     /var/backup/2006-11-26_00.00.02.523967.ricvic-desktop.inc
32M     /var/backup/2006-11-27_00.00.02.433806.ricvic-desktop.inc
41M     /var/backup/2006-11-28_00.00.03.012901.ricvic-desktop.inc
96M     /var/backup/2006-11-29_00.00.02.562910.ricvic-desktop.ful
3.3M    /var/backup/2006-11-30_00.00.03.099837.ricvic-desktop.inc
3.7M    /var/backup/2006-12-01_00.00.03.703768.ricvic-desktop.inc
3.8M    /var/backup/2006-12-02_00.00.03.149711.ricvic-desktop.inc
6.4M    /var/backup/2006-12-03_00.00.02.809557.ricvic-desktop.inc
28M     /var/backup/2006-12-04_00.00.03.078876.ricvic-desktop.inc
29M     /var/backup/2006-12-05_00.00.02.848582.ricvic-desktop.inc
26M     /var/backup/2006-12-06_00.00.03.310162.ricvic-desktop.inc
102M    /var/backup/2006-12-10_00.00.02.527607.ricvic-desktop.ful
13M     /var/backup/2006-12-11_00.00.03.348129.ricvic-desktop.inc
67M     /var/backup/2006-12-12_00.00.02.230518.ricvic-desktop.inc
40M     /var/backup/2006-12-13_00.00.02.355505.ricvic-desktop.inc
21M     /var/backup/2006-12-14_00.00.02.207059.ricvic-desktop.inc
22M     /var/backup/2006-12-15_00.00.01.907244.ricvic-desktop.inc
18M     /var/backup/2006-12-16_00.00.02.575482.ricvic-desktop.inc
45M     /var/backup/2006-12-17_00.00.03.295181.ricvic-desktop.inc
127M    /var/backup/2006-12-18_00.00.03.797026.ricvic-desktop.ful
19M     /var/backup/2006-12-20_00.00.01.576253.ricvic-desktop.inc
116M    /var/backup/2006-12-29_00.00.02.310494.ricvic-desktop.ful
12M     /var/backup/2006-12-30_00.00.02.330126.ricvic-desktop.inc
21M     /var/backup/2006-12-31_00.00.01.931093.ricvic-desktop.inc
9.1M    /var/backup/2007-01-01_00.00.02.348196.ricvic-desktop.inc
18M     /var/backup/2007-01-02_00.00.02.491790.ricvic-desktop.inc
15M     /var/backup/2007-01-03_00.00.02.187710.ricvic-desktop.inc
15M     /var/backup/2007-01-04_00.00.01.829320.ricvic-desktop.inc
112M    /var/backup/2007-01-13_00.00.01.999640.ricvic-desktop.ful
12M     /var/backup/2007-01-14_00.00.02.428141.ricvic-desktop.inc
25M     /var/backup/2007-01-15_00.00.02.454684.ricvic-desktop.inc
17M     /var/backup/2007-01-16_00.00.03.206278.ricvic-desktop.inc
16M     /var/backup/2007-01-17_00.00.03.776402.ricvic-desktop.inc
7.4M    /var/backup/2007-01-18_00.00.01.623294.ricvic-desktop.inc
27M     /var/backup/2007-01-19_00.00.01.927377.ricvic-desktop.inc
13M     /var/backup/2007-01-20_00.00.02.107618.ricvic-desktop.inc
131M    /var/backup/2007-01-21_00.00.02.706856.ricvic-desktop.ful
11M     /var/backup/2007-01-22_00.00.02.660438.ricvic-desktop.inc
50M     /var/backup/2007-01-23_00.00.02.223640.ricvic-desktop.inc
16M     /var/backup/2007-01-24_00.00.02.860932.ricvic-desktop.inc
22M     /var/backup/2007-01-25_00.00.03.274076.ricvic-desktop.inc
41M     /var/backup/2007-01-26_00.00.03.418717.ricvic-desktop.inc
40M     /var/backup/2007-01-27_00.00.03.842341.ricvic-desktop.inc
11M     /var/backup/2007-01-28_00.00.03.870534.ricvic-desktop.inc
154M    /var/backup/2007-01-29_00.00.03.624851.ricvic-desktop.ful
21M     /var/backup/2007-01-30_00.00.03.737965.ricvic-desktop.inc
12M     /var/backup/2007-01-31_00.00.04.093196.ricvic-desktop.inc
22M     /var/backup/2007-02-01_00.00.04.083690.ricvic-desktop.inc
34M     /var/backup/2007-02-02_00.00.03.748714.ricvic-desktop.inc
8.6M    /var/backup/2007-02-03_00.00.03.433758.ricvic-desktop.inc
11M     /var/backup/2007-02-04_00.00.03.433565.ricvic-desktop.inc
14M     /var/backup/2007-02-05_00.00.03.445517.ricvic-desktop.inc
169M    /var/backup/2007-02-06_00.00.04.368927.ricvic-desktop.ful
11M     /var/backup/2007-02-07_00.00.03.672655.ricvic-desktop.inc
11M     /var/backup/2007-02-08_00.00.02.986758.ricvic-desktop.inc
20M     /var/backup/2007-02-09_00.00.09.447831.ricvic-desktop.inc
8.4M    /var/backup/2007-02-10_00.00.03.260815.ricvic-desktop.inc
21M     /var/backup/2007-02-11_00.00.04.985951.ricvic-desktop.inc
9.7M    /var/backup/2007-02-12_00.00.04.668229.ricvic-desktop.inc
13M     /var/backup/2007-02-13_00.00.03.651423.ricvic-desktop.inc
165M    /var/backup/2007-02-14_00.00.03.138010.ricvic-desktop.ful
6.0M    /var/backup/2007-02-20_00.00.02.098024.ricvic-desktop.inc
8.4M    /var/backup/2007-02-21_00.00.02.733529.ricvic-desktop.inc
147M    /var/backup/2007-02-22_00.00.02.230252.ricvic-desktop.ful
5.2M    /var/backup/2007-02-23_00.00.01.947283.ricvic-desktop.inc
4.0G    /var/backup
4.1G    /var
ricvic@ricvic-desktop:~$

---

### Post by Virgo53 on 2007-03-10
Okay, now what needs to be done to resolve my "bloated" partition? Thanks for all replies!

---

### Post by taurus on 2007-03-10
There seems to be a program doing a backup of your system everyday.  You need to look in /etc/cron.daily and perhaps move it to /etc/cron.weekly or delete it completely if you don't need it.  That's why it's taking up all the space on your harddrive, backing up.

```
sudo rm /var/backup/*
df -h
```

---

### Post by Virgo53 on 2007-03-10
I ran sudo rm /var/backup/* from recovery mode and got a bunch of cannot delete messages.
Before when I ran aptitude clean I was able to login normally with only 10MB
of free space available, but not now. I get to the Gnome login page which has 
my name listed. When I type in my user name and password, nothing happens.
What should I try next?

---

### Post by Virgo53 on 2007-03-15
My log in problem is now resolved! / was 100% maxed out  and now / is at 57%.
This was done by removing all of the older back ups (both full and incremental).
I ran sudo rm -ri /var/backup/*
I changed the back up program to do monthly full backups and weekly incremental
backups since the problem arose from it doing daily incremental and weekly full backups.
I saved the two latest full backups and the incremental backups between the two full backups.
Also am running system monitor to keep an eye on everything! :guitar: 
I hope this helps anyone with a similar problem. 
Thanks to all.

---

### Post by zumbi77 on 2007-03-26
Hi

I have the same problem. Followed the advice given in the thread, and found out that the hard disk is full. But the solution does seem to work.

When I try to run 

sudo rm /var/backup/* or sudo rm -ri /var/backup/*

the message I get is "no such file or directory"

What can I do?

---

