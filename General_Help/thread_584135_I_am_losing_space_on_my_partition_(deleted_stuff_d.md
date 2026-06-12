---
title: "I am losing space on my partition (deleted stuff dont free space)"
date: 2007-10-20
forum: General Help
---

### Post by Elv13 on 2007-10-20
I am having a really serious problem. Since i am using gutsy (tribe 5 + update) my pace is filling non-stop. 

-My partition is 60gb (ext3)
-I have 13gb data (including trash, /, hidden file and /home)
-I have 157mb of free space

I tried to delete stuff using rm -fr, delete key, in nautilus, in konqueror, emptying trash everywhere, doing all update, fsck (from live-cd of feisty), nothing fix that.

Gparted show that i have 2.48gb of free space and i am 100% sure that i have only 13gb of data including everythig. If i reach 0b of free space, i will have to format and i dont want to do that, please, help me to fix this.

---

### Post by ddrichardson on 2007-10-20
Use Applications/Accessories/Disk Usage Analyser to see what folders are using the most space.

---

### Post by Elv13 on 2007-10-20
I did, it confirm that i have only 13gb of data, the rest is just gone nowhere

---

### Post by ddrichardson on 2007-10-21
What is the output of:```
fdisk -l
```

---

### Post by Elv13 on 2007-10-21
Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1       13105   105265881    c  W95 FAT32 (LBA)
/dev/sda3           13106       15017    15358140    7  HPFS/NTFS

Disque /dev/sdb: 300.0 Go, 300069052416 octets
255 heads, 63 sectors/track, 36481 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000edc59

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1               1        6374    51199123+  83  Linux
/dev/sdb2            6375        6635     2096482+  82  Linux swap / Solaris
/dev/sdb3            6636       36481   239737995    b  W95 FAT32


Linux is sdb1

---

### Post by ddrichardson on 2007-10-21
Try cleaning out the apt-get cache:```
sudo apt-get clean
```

---

### Post by Elv13 on 2007-10-22
i did that, i have 13gb of data on my drive and the partition is 50gb, the rest is suppose to be only free space, but this free space dont exist. Their is no data on the rest of the drive, their is only 13gb of data. It is useless to find stuff to delete, it dont give the space back event if i delete those data from console.

---

### Post by ddrichardson on 2007-10-22
I'll be honest this is beyond me - I can only suggest filing a bug  report.

---

### Post by forestpixie on 2007-10-22
did you check root trash ? are you sure that you haven't got a problem with the drive?

---

### Post by Elv13 on 2007-10-22
about the root trash, yes, of course i did. Abou the drive, it is a brand new one, so it is possible, but i dont think, it seem to work fine. I have no problem with the files, i have problem with files tat i dont have anymore. Normally, they are indexed by the FS, no the drive itself.

---

### Post by Elv13 on 2007-10-24
up

---

### Post by studo77 on 2007-10-25
I am having the same problem. Feisty, and i deleted some Gb of data, but the disk did not get any free space. Any solutions?

Solution is here:
[http://ubuntuforums.org/showthread.php?t=588583](http://ubuntuforums.org/showthread.php?t=588583)

---

### Post by Elv13 on 2007-10-26
up... someone know a good fs utils to find out what is happening?

---

### Post by cwaldbieser on 2007-10-26
> **Elv13 said:**
> up... someone know a good fs utils to find out what is happening?

Have you run a filesystem check?
```

$ sudo touch /forcefsck

```
Then reboot.

---

### Post by Elv13 on 2007-10-26
i did before making the topic...

---

### Post by BroadArrow on 2007-10-27
I think I've got the same problem (see thread [http://ubuntuforums.org/showthread.php?t=592160](http://ubuntuforums.org/showthread.php?t=592160)) as my root partition ran out of space during the upgrade. I haven't been able to log in to X and can only boot in recovery mode or from CD. I've tried deleting several GB of files from the root partition but the disk is still described as 100% used by "du".

---

### Post by BroadArrow on 2007-10-27
> **ddrichardson said:**
> Try cleaning out the apt-get cache:```
sudo apt-get clean
```
This created just enough space for me to log in to X, which is great. However, I'm now having to deal with many other issues caused by the interrupted upgrade to Gutsy... :-( Anyway, thanks for the tip.

---

### Post by Elv13 on 2007-10-27
25mb left, if no one find why, gentoo will be back in few day...

---

### Post by #Reistlehr- on 2007-10-27
You need to empty trash if you use the GUI to delete. Otherwise if you use rm command, it will immediatly delete it

---

### Post by Elv13 on 2007-10-27
I know all that, all .trash are deleted and all apps say almost the same thing, their is 17.8gb used on my partition of 50gb and 38 mo of free space. Please stop trying to find where are hidden file, there is none, it is not the problem.

---

### Post by ddrichardson on 2007-10-27
Check to see how much space is in /var/backups```
sudo du -h /var
```

---

### Post by Gas_Man on 2007-10-27
> **Elv13 said:**
> I am having a really serious problem. Since i am using gutsy (tribe 5 + update) my pace is filling non-stop. 

-My partition is 60gb (ext3)
-I have 13gb data (including trash, /, hidden file and /home)
-I have 157mb of free space

I tried to delete stuff using rm -fr, delete key, in nautilus, in konqueror, emptying trash everywhere, doing all update, fsck (from live-cd of feisty), nothing fix that.

Gparted show that i have 2.48gb of free space and i am 100% sure that i have only 13gb of data including everythig. If i reach 0b of free space, i will have to format and i dont want to do that, please, help me to fix this.
your post says you used the live-cd in your attempts. 

Did you navigate to /media/disk/home/*username here*/.Trash/

on my box that folder is locked if i use a live cd, so you might want to try the recovery (cli) to get there. good luck

---

### Post by Elv13 on 2007-10-27
```
4,0K    /var/cache/gnome-system-tools/backup
8,0K    /var/cache/gnome-system-tools
496K    /var/cache/hald
4,0K    /var/cache/cups/ppd
4,0K    /var/cache/cups/rss
500K    /var/cache/cups
5,5M    /var/cache/debconf
4,0K    /var/cache/pppconfig
4,0K    /var/cache/samba
4,0K    /var/cache/apt/archives/partial
152K    /var/cache/apt/archives
22M     /var/cache/apt
2,5M    /var/cache/flashplugin-nonfree
32K     /var/cache/dictionaries-common
4,0K    /var/cache/man/cat6
4,0K    /var/cache/man/local/cat1
24K     /var/cache/man/local
4,0K    /var/cache/man/X11R6
4,0K    /var/cache/man/oldlocal/cat1
24K     /var/cache/man/oldlocal
4,0K    /var/cache/man/opt
4,0K    /var/cache/man/cat3
4,0K    /var/cache/man/cat5
4,0K    /var/cache/man/fsstnd
4,0K    /var/cache/man/cat4
4,0K    /var/cache/man/cat8
4,0K    /var/cache/man/cat2
4,0K    /var/cache/man/cat7
4,0K    /var/cache/man/cat1
1,2M    /var/cache/man
4,0K    /var/cache/locate
756K    /var/cache/fontconfig
8,0K    /var/cache/system-tools-backends/backup/2/var/cache/system-tools-backends
12K     /var/cache/system-tools-backends/backup/2/var/cache
16K     /var/cache/system-tools-backends/backup/2/var
20K     /var/cache/system-tools-backends/backup/2
8,0K    /var/cache/system-tools-backends/backup/1/var/cache/system-tools-backends
12K     /var/cache/system-tools-backends/backup/1/var/cache
16K     /var/cache/system-tools-backends/backup/1/var
20K     /var/cache/system-tools-backends/backup/1
8,0K    /var/cache/system-tools-backends/backup/8/etc
12K     /var/cache/system-tools-backends/backup/8
28K     /var/cache/system-tools-backends/backup/9/etc
32K     /var/cache/system-tools-backends/backup/9
8,0K    /var/cache/system-tools-backends/backup/5/var/cache/system-tools-backends
12K     /var/cache/system-tools-backends/backup/5/var/cache
16K     /var/cache/system-tools-backends/backup/5/var
20K     /var/cache/system-tools-backends/backup/5
8,0K    /var/cache/system-tools-backends/backup/6/var/cache/system-tools-backends
12K     /var/cache/system-tools-backends/backup/6/var/cache
16K     /var/cache/system-tools-backends/backup/6/var
20K     /var/cache/system-tools-backends/backup/6
8,0K    /var/cache/system-tools-backends/backup/4/var/cache/system-tools-backends
12K     /var/cache/system-tools-backends/backup/4/var/cache
16K     /var/cache/system-tools-backends/backup/4/var
20K     /var/cache/system-tools-backends/backup/4
8,0K    /var/cache/system-tools-backends/backup/3/var/cache/system-tools-backends
12K     /var/cache/system-tools-backends/backup/3/var/cache
16K     /var/cache/system-tools-backends/backup/3/var
20K     /var/cache/system-tools-backends/backup/3
8,0K    /var/cache/system-tools-backends/backup/7/var/cache/system-tools-backends
12K     /var/cache/system-tools-backends/backup/7/var/cache
16K     /var/cache/system-tools-backends/backup/7/var
20K     /var/cache/system-tools-backends/backup/7
8,0K    /var/cache/system-tools-backends/backup/First/var/cache/system-tools-backends
12K     /var/cache/system-tools-backends/backup/First/var/cache
16K     /var/cache/system-tools-backends/backup/First/var
20K     /var/cache/system-tools-backends/backup/First
208K    /var/cache/system-tools-backends/backup
216K    /var/cache/system-tools-backends
80K     /var/cache/restricted-manager
7,1M    /var/cache/app-install
40M     /var/cache
29M     /var/lib/slocate
8,0K    /var/lib/dhcp3
8,0K    /var/lib/security
4,0K    /var/lib/gstreamer/0.10
8,0K    /var/lib/gstreamer
60K     /var/lib/scrollkeeper/te
60K     /var/lib/scrollkeeper/wa
148K    /var/lib/scrollkeeper/ko
60K     /var/lib/scrollkeeper/ia
60K     /var/lib/scrollkeeper/sl
60K     /var/lib/scrollkeeper/si
60K     /var/lib/scrollkeeper/or
60K     /var/lib/scrollkeeper/li
68K     /var/lib/scrollkeeper/en
60K     /var/lib/scrollkeeper/eo
124K    /var/lib/scrollkeeper/pa
276K    /var/lib/scrollkeeper/C
60K     /var/lib/scrollkeeper/fo
124K    /var/lib/scrollkeeper/bg
60K     /var/lib/scrollkeeper/fa
60K     /var/lib/scrollkeeper/lg
64K     /var/lib/scrollkeeper/ms
60K     /var/lib/scrollkeeper/wo
4,5M    /var/lib/scrollkeeper/index
60K     /var/lib/scrollkeeper/af
60K     /var/lib/scrollkeeper/bs
108K    /var/lib/scrollkeeper/hu
60K     /var/lib/scrollkeeper/ga
84K     /var/lib/scrollkeeper/nl
60K     /var/lib/scrollkeeper/mg
68K     /var/lib/scrollkeeper/tr
60K     /var/lib/scrollkeeper/ml
60K     /var/lib/scrollkeeper/bn
60K     /var/lib/scrollkeeper/sw
60K     /var/lib/scrollkeeper/co
60K     /var/lib/scrollkeeper/an
80K     /var/lib/scrollkeeper/ar
148K    /var/lib/scrollkeeper/uk
60K     /var/lib/scrollkeeper/cy
60K     /var/lib/scrollkeeper/tg
60K     /var/lib/scrollkeeper/th
80K     /var/lib/scrollkeeper/zh_TW
60K     /var/lib/scrollkeeper/az
60K     /var/lib/scrollkeeper/ur
60K     /var/lib/scrollkeeper/rm
60K     /var/lib/scrollkeeper/sq
60K     /var/lib/scrollkeeper/gu
120K    /var/lib/scrollkeeper/de
148K    /var/lib/scrollkeeper/en_GB
60K     /var/lib/scrollkeeper/zu
64K     /var/lib/scrollkeeper/lv
260K    /var/lib/scrollkeeper/fr
60K     /var/lib/scrollkeeper/se
72K     /var/lib/scrollkeeper/ro
60K     /var/lib/scrollkeeper/am
60K     /var/lib/scrollkeeper/hr
72K     /var/lib/scrollkeeper/vi
60K     /var/lib/scrollkeeper/tk
68K     /var/lib/scrollkeeper/he
72K     /var/lib/scrollkeeper/pl
60K     /var/lib/scrollkeeper/lt
132K    /var/lib/scrollkeeper/zh_CN
60K     /var/lib/scrollkeeper/ug
60K     /var/lib/scrollkeeper/ka
60K     /var/lib/scrollkeeper/no
72K     /var/lib/scrollkeeper/sr
60K     /var/lib/scrollkeeper/br
60K     /var/lib/scrollkeeper/et
60K     /var/lib/scrollkeeper/mi
104K    /var/lib/scrollkeeper/ca
80K     /var/lib/scrollkeeper/id
60K     /var/lib/scrollkeeper/yo
60K     /var/lib/scrollkeeper/lb
60K     /var/lib/scrollkeeper/mn
60K     /var/lib/scrollkeeper/xh
68K     /var/lib/scrollkeeper/be
60K     /var/lib/scrollkeeper/nn
172K    /var/lib/scrollkeeper/it
120K    /var/lib/scrollkeeper/pt
60K     /var/lib/scrollkeeper/lo
60K     /var/lib/scrollkeeper/tl
136K    /var/lib/scrollkeeper/pt_BR
268K    /var/lib/scrollkeeper/es
80K     /var/lib/scrollkeeper/sk
60K     /var/lib/scrollkeeper/hy
60K     /var/lib/scrollkeeper/uz
256K    /var/lib/scrollkeeper/sv
60K     /var/lib/scrollkeeper/ku
64K     /var/lib/scrollkeeper/nb
60K     /var/lib/scrollkeeper/ky
60K     /var/lib/scrollkeeper/as
80K     /var/lib/scrollkeeper/cs
60K     /var/lib/scrollkeeper/ne
60K     /var/lib/scrollkeeper/yi
64K     /var/lib/scrollkeeper/da
68K     /var/lib/scrollkeeper/gl
60K     /var/lib/scrollkeeper/mr
104K    /var/lib/scrollkeeper/ja
112K    /var/lib/scrollkeeper/el
112K    /var/lib/scrollkeeper/fi
60K     /var/lib/scrollkeeper/is
60K     /var/lib/scrollkeeper/rw
60K     /var/lib/scrollkeeper/kk
5,0M    /var/lib/scrollkeeper/TOC
168K    /var/lib/scrollkeeper/oc
92K     /var/lib/scrollkeeper/eu
188K    /var/lib/scrollkeeper/ru
68K     /var/lib/scrollkeeper/kn
60K     /var/lib/scrollkeeper/ta
60K     /var/lib/scrollkeeper/my
60K     /var/lib/scrollkeeper/sr@Latn
18M     /var/lib/scrollkeeper
4,0K    /var/lib/defoma/gs.d/dirs/CMap
296K    /var/lib/defoma/gs.d/dirs/fonts
304K    /var/lib/defoma/gs.d/dirs
444K    /var/lib/defoma/gs.d
316K    /var/lib/defoma/vflib3.d
4,0K    /var/lib/defoma/fontconfig.d/F
12K     /var/lib/defoma/fontconfig.d/P
24K     /var/lib/defoma/fontconfig.d/C
4,0K    /var/lib/defoma/fontconfig.d/E
36K     /var/lib/defoma/fontconfig.d/T
8,0K    /var/lib/defoma/fontconfig.d/j
8,0K    /var/lib/defoma/fontconfig.d/m
8,0K    /var/lib/defoma/fontconfig.d/V
56K     /var/lib/defoma/fontconfig.d/M
8,0K    /var/lib/defoma/fontconfig.d/R
8,0K    /var/lib/defoma/fontconfig.d/a
4,0K    /var/lib/defoma/fontconfig.d/I
4,0K    /var/lib/defoma/fontconfig.d/u
4,0K    /var/lib/defoma/fontconfig.d/B
4,0K    /var/lib/defoma/fontconfig.d/J
8,0K    /var/lib/defoma/fontconfig.d/L
4,0K    /var/lib/defoma/fontconfig.d/W
76K     /var/lib/defoma/fontconfig.d/D
4,0K    /var/lib/defoma/fontconfig.d/H
4,0K    /var/lib/defoma/fontconfig.d/O
4,0K    /var/lib/defoma/fontconfig.d/K
12K     /var/lib/defoma/fontconfig.d/G
4,0K    /var/lib/defoma/fontconfig.d/S
4,0K    /var/lib/defoma/fontconfig.d/N
20K     /var/lib/defoma/fontconfig.d/A
4,0K    /var/lib/defoma/fontconfig.d/U
508K    /var/lib/defoma/fontconfig.d
4,0K    /var/lib/defoma/x-ttcidfont-conf.d/dirs/CID
456K    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
464K    /var/lib/defoma/x-ttcidfont-conf.d/dirs
1,3M    /var/lib/defoma/x-ttcidfont-conf.d
208K    /var/lib/defoma/libwmf0.2-7.d
76K     /var/lib/defoma/scripts
260K    /var/lib/defoma/pango.d
3,8M    /var/lib/defoma
4,0K    /var/lib/guidance-backends
3,5M    /var/lib/aptitude
12K     /var/lib/dpkg/triggers
544K    /var/lib/dpkg/alternatives
57M     /var/lib/dpkg/info
4,0K    /var/lib/dpkg/methods/mnt
4,0K    /var/lib/dpkg/methods/disk
4,0K    /var/lib/dpkg/methods/floppy
16K     /var/lib/dpkg/methods
4,0K    /var/lib/dpkg/updates
4,0K    /var/lib/dpkg/parts
65M     /var/lib/dpkg
4,0K    /var/lib/initscripts
4,0K    /var/lib/alien
68K     /var/lib/misc
4,0K    /var/lib/update-manager
4,0K    /var/lib/discover
4,0K    /var/lib/NetworkManager
4,0K    /var/lib/synaptic
8,0K    /var/lib/thunderbird/extensions.d
12K     /var/lib/thunderbird
4,0K    /var/lib/sgml-base
16K     /var/lib/update-notifier/user.d
20K     /var/lib/update-notifier
76K     /var/lib/gconf/debian.defaults
50M     /var/lib/gconf/defaults
50M     /var/lib/gconf
8,0K    /var/lib/dbus
8,0K    /var/lib/ucf/cache
40K     /var/lib/ucf
56K     /var/lib/python-support/python2.5/apport/crashdb_impl
276K    /var/lib/python-support/python2.5/apport
16K     /var/lib/python-support/python2.5/gtk-2.0/totem
16K     /var/lib/python-support/python2.5/gtk-2.0/gnomedesktop
88K     /var/lib/python-support/python2.5/gtk-2.0/gtk
16K     /var/lib/python-support/python2.5/gtk-2.0/gksu2
20K     /var/lib/python-support/python2.5/gtk-2.0/gksu
60K     /var/lib/python-support/python2.5/gtk-2.0/gobject
44K     /var/lib/python-support/python2.5/gtk-2.0/gnome
20K     /var/lib/python-support/python2.5/gtk-2.0/gnomevfs
20K     /var/lib/python-support/python2.5/gtk-2.0/gnomeprint
16K     /var/lib/python-support/python2.5/gtk-2.0/pynotify
20K     /var/lib/python-support/python2.5/gtk-2.0/egg
24K     /var/lib/python-support/python2.5/gtk-2.0/bonobo
480K    /var/lib/python-support/python2.5/gtk-2.0
16K     /var/lib/python-support/python2.5/dbus/mainloop
172K    /var/lib/python-support/python2.5/dbus
156K    /var/lib/python-support/python2.5/xdg
88K     /var/lib/python-support/python2.5/invest
2,0M    /var/lib/python-support/python2.5
16K     /var/lib/python-support/python2.4/gtk-2.0/totem
16K     /var/lib/python-support/python2.4/gtk-2.0/gnomedesktop
92K     /var/lib/python-support/python2.4/gtk-2.0/gtk
16K     /var/lib/python-support/python2.4/gtk-2.0/gksu2
20K     /var/lib/python-support/python2.4/gtk-2.0/gksu
56K     /var/lib/python-support/python2.4/gtk-2.0/gobject
44K     /var/lib/python-support/python2.4/gtk-2.0/gnome
20K     /var/lib/python-support/python2.4/gtk-2.0/gnomevfs
20K     /var/lib/python-support/python2.4/gtk-2.0/gnomeprint
20K     /var/lib/python-support/python2.4/gtk-2.0/egg
24K     /var/lib/python-support/python2.4/gtk-2.0/bonobo
460K    /var/lib/python-support/python2.4/gtk-2.0
16K     /var/lib/python-support/python2.4/dbus/mainloop
172K    /var/lib/python-support/python2.4/dbus
148K    /var/lib/python-support/python2.4/xdg
84K     /var/lib/python-support/python2.4/invest
1,4M    /var/lib/python-support/python2.4
3,3M    /var/lib/python-support
4,0K    /var/lib/apt/mirrors/partial
8,0K    /var/lib/apt/mirrors
4,0K    /var/lib/apt/lists/partial
36M     /var/lib/apt/lists
4,0K    /var/lib/apt/periodic
36M     /var/lib/apt
4,0K    /var/lib/displayconfig-gtk/locations
8,0K    /var/lib/displayconfig-gtk
8,0K    /var/lib/kdm
4,0K    /var/lib/hal
8,0K    /var/lib/doc-base/omf/libsdl1.2-dev
8,0K    /var/lib/doc-base/omf/ImageMagick
8,0K    /var/lib/doc-base/omf/opencdk
8,0K    /var/lib/doc-base/omf/debian-java-faq
8,0K    /var/lib/doc-base/omf/quilt
8,0K    /var/lib/doc-base/omf/dc
8,0K    /var/lib/doc-base/omf/python-policy
8,0K    /var/lib/doc-base/omf/libpng12
8,0K    /var/lib/doc-base/omf/fdutils-faq
8,0K    /var/lib/doc-base/omf/java-policy
8,0K    /var/lib/doc-base/omf/libxslt1-dev
8,0K    /var/lib/doc-base/omf/libusb-dev
8,0K    /var/lib/doc-base/omf/cdbs
8,0K    /var/lib/doc-base/omf/time
8,0K    /var/lib/doc-base/omf/doc-base
8,0K    /var/lib/doc-base/omf/libtasn1
8,0K    /var/lib/doc-base/omf/imlib2
8,0K    /var/lib/doc-base/omf/nat
8,0K    /var/lib/doc-base/omf/packet-filter
8,0K    /var/lib/doc-base/omf/cupsys
8,0K    /var/lib/doc-base/omf/fdutils
8,0K    /var/lib/doc-base/omf/diveintopython
8,0K    /var/lib/doc-base/omf/gnupginterface
8,0K    /var/lib/doc-base/omf/install-docs-man
8,0K    /var/lib/doc-base/omf/cvs-doc
8,0K    /var/lib/doc-base/omf/libtiff4
8,0K    /var/lib/doc-base/omf/man-db
8,0K    /var/lib/doc-base/omf/cvs-doc-client
8,0K    /var/lib/doc-base/omf/com_err
236K    /var/lib/doc-base/omf
180K    /var/lib/doc-base/info
420K    /var/lib/doc-base
52K     /var/lib/belocs
32K     /var/lib/xml-core
4,0K    /var/lib/flashplugin-nonfree
4,0K    /var/lib/snmp
28K     /var/lib/gdm/.fontconfig
48K     /var/lib/gdm
8,0K    /var/lib/logrotate
12K     /var/lib/dictionaries-common/wordlist
8,0K    /var/lib/dictionaries-common/aspell
24K     /var/lib/dictionaries-common
24K     /var/lib/binfmts
3,5M    /var/lib/aspell
8,0K    /var/lib/mozilla-firefox/extensions.d
12K     /var/lib/mozilla-firefox
8,0K    /var/lib/urandom
12K     /var/lib/alsa
28K     /var/lib/x11
32K     /var/lib/initramfs-tools
4,0K    /var/lib/vim/addons
8,0K    /var/lib/vim
68K     /var/lib/gcj-4.2
4,0K    /var/lib/bittorrent
8,0K    /var/lib/msttcorefonts
24K     /var/lib/acpi-support
8,0K    /var/lib/avahi-autoipd
4,0K    /var/lib/cvs/CVSROOT/Emptydir
192K    /var/lib/cvs/CVSROOT
196K    /var/lib/cvs
4,0K    /var/lib/xkb
16K     /var/lib/locales/supported.d
20K     /var/lib/locales
68K     /var/lib/gcj-4.1
211M    /var/lib
3,3M    /var/crash
4,0K    /var/local
12K     /var/log/fsck
1,1M    /var/log/cups
4,0K    /var/log/news
4,0K    /var/log/unattended-upgrades
4,0K    /var/log/samba
376K    /var/log/apt
752K    /var/log/installer
140K    /var/log/dist-upgrade
60K     /var/log/gdm
4,0K    /var/log/bittorrent
7,1M    /var/log
6,9M    /var/backups
4,0K    /var/lock
4,0K    /var/opt
0       /var/run/sudo/lepagee
0       /var/run/sudo
0       /var/run/console
8,0K    /var/run/avahi-daemon
0       /var/run/VirtualBox
0       /var/run/cups/certs
4,0K    /var/run/cups
0       /var/run/sshd
4,0K    /var/run/hal
8,0K    /var/run/NetworkManager
4,0K    /var/run/dbus
8,0K    /var/run/klogd
0       /var/run/screen
0       /var/run/pppconfig
4,0K    /var/run/network
100K    /var/run
16K     /var/games
4,0K    /var/tmp/kdecache-kde-devel
48K     /var/tmp/kdecache-lepagee/background
3,5M    /var/tmp/kdecache-lepagee/digiKam
64K     /var/tmp/kdecache-lepagee/help
4,0K    /var/tmp/kdecache-lepagee/favicons
4,0K    /var/tmp/kdecache-lepagee/http/e
8,0K    /var/tmp/kdecache-lepagee/http/d
4,0K    /var/tmp/kdecache-lepagee/http/s
4,0K    /var/tmp/kdecache-lepagee/http/h
8,0K    /var/tmp/kdecache-lepagee/http/n
4,0K    /var/tmp/kdecache-lepagee/http/a
4,0K    /var/tmp/kdecache-lepagee/http/r
4,0K    /var/tmp/kdecache-lepagee/http/b
4,0K    /var/tmp/kdecache-lepagee/http/g
48K     /var/tmp/kdecache-lepagee/http
4,0K    /var/tmp/kdecache-lepagee/krun
4,7M    /var/tmp/kdecache-lepagee
80K     /var/tmp/kde-devel-kde4/kdecache-kde-develBW1eEd/http/e
16K     /var/tmp/kde-devel-kde4/kdecache-kde-develBW1eEd/http/d
100K    /var/tmp/kde-devel-kde4/kdecache-kde-develBW1eEd/http
164K    /var/tmp/kde-devel-kde4/kdecache-kde-develBW1eEd/kpc
2,1M    /var/tmp/kde-devel-kde4/kdecache-kde-develBW1eEd
304K    /var/tmp/kde-devel-kde4/kdecache-kde-develhIYC4y/kpc
1,3M    /var/tmp/kde-devel-kde4/kdecache-kde-develhIYC4y
4,0K    /var/tmp/kde-devel-kde4/kdecache-kde-develPgQ0kd/http/m
12K     /var/tmp/kde-devel-kde4/kdecache-kde-develPgQ0kd/http/h
4,0K    /var/tmp/kde-devel-kde4/kdecache-kde-develPgQ0kd/http/c
24K     /var/tmp/kde-devel-kde4/kdecache-kde-develPgQ0kd/http
12K     /var/tmp/kde-devel-kde4/kdecache-kde-develPgQ0kd/kpc
1,1M    /var/tmp/kde-devel-kde4/kdecache-kde-develPgQ0kd/fontpreview
2,1M    /var/tmp/kde-devel-kde4/kdecache-kde-develPgQ0kd
48K     /var/tmp/kde-devel-kde4/kdecache-kde-develXcOoRH/background
24K     /var/tmp/kde-devel-kde4/kdecache-kde-develXcOoRH/kpc
7,1M    /var/tmp/kde-devel-kde4/kdecache-kde-develXcOoRH
4,0K    /var/tmp/kde-devel-kde4/kdecache-kde-devel
304K    /var/tmp/kde-devel-kde4/kdecache-kde-develbPj8fR/kpc
1,3M    /var/tmp/kde-devel-kde4/kdecache-kde-develbPj8fR
972K    /var/tmp/kde-devel-kde4/kdecache-kde-develdqi2Yw
8,0K    /var/tmp/kde-devel-kde4/kdecache-kde-develMeFo9K/favicons
96K     /var/tmp/kde-devel-kde4/kdecache-kde-develMeFo9K/http/k
100K    /var/tmp/kde-devel-kde4/kdecache-kde-develMeFo9K/http
116K    /var/tmp/kde-devel-kde4/kdecache-kde-develMeFo9K/kpc
1,2M    /var/tmp/kde-devel-kde4/kdecache-kde-develMeFo9K
16K     /var/tmp/kde-devel-kde4/kdecache-kde-develdiYaau/kpc
6,1M    /var/tmp/kde-devel-kde4/kdecache-kde-develdiYaau
4,0K    /var/tmp/kde-devel-kde4/kdecache-kde-develnMpVWQ/background
24K     /var/tmp/kde-devel-kde4/kdecache-kde-develnMpVWQ/favicons
408K    /var/tmp/kde-devel-kde4/kdecache-kde-develnMpVWQ/http/k
76K     /var/tmp/kde-devel-kde4/kdecache-kde-develnMpVWQ/http/e
16K     /var/tmp/kde-devel-kde4/kdecache-kde-develnMpVWQ/http/d
1,8M    /var/tmp/kde-devel-kde4/kdecache-kde-develnMpVWQ/http/n
384K    /var/tmp/kde-devel-kde4/kdecache-kde-develnMpVWQ/http/a
20K     /var/tmp/kde-devel-kde4/kdecache-kde-develnMpVWQ/http/u
48K     /var/tmp/kde-devel-kde4/kdecache-kde-develnMpVWQ/http/b
240K    /var/tmp/kde-devel-kde4/kdecache-kde-develnMpVWQ/http/p
2,9M    /var/tmp/kde-devel-kde4/kdecache-kde-develnMpVWQ/http
132K    /var/tmp/kde-devel-kde4/kdecache-kde-develnMpVWQ/kpc
5,1M    /var/tmp/kde-devel-kde4/kdecache-kde-develnMpVWQ
176K    /var/tmp/kde-devel-kde4/kdecache-kde-develWObOg2/kpc
6,3M    /var/tmp/kde-devel-kde4/kdecache-kde-develWObOg2
34M     /var/tmp/kde-devel-kde4
4,0K    /var/tmp/kdecache-root
38M     /var/tmp
16K     /var/spool/anacron
4,0K    /var/spool/cups/tmp
12K     /var/spool/cups
4,0K    /var/spool/cron/crontabs
8,0K    /var/spool/cron/atjobs
4,0K    /var/spool/cron/atspool
20K     /var/spool/cron
4,0K    /var/spool/openoffice/uno_packages/cache
8,0K    /var/spool/openoffice/uno_packages
12K     /var/spool/openoffice
64K     /var/spool
4,0K    /var/mail
305M    /var

```

About the trash:
lepagee@lepagee-desktop:~/Desktop$ ls ~/.Trash/
lepagee@lepagee-desktop:~/Desktop$ 
nothing, same for all user

---

### Post by Gas_Man on 2007-10-28
lol
.Trash is a hidden holder, as are it's contents. try:

```
ls -Al .Trash/
```

hidden files do not show up with **ls** unless you use the **-A** switch

then try:

```
rm -fi .Trash/*
```
this one gets rid of everything that is not hidden

and finally, try

```
rm -fi .Trash/.*
```
this one gets rid of everything that is  /hidden

and if you don't want to answer "**y**" to each delete request, don't include the "**i**" in the rm  code block.


good luck

ps.
if i knew how to do the code thingy, i would!

pps
i learned code tags today

ppps
also, if you go to "**System**" ->"**Preferences**" ->"**File Management**" and then select the "**Behavior**" tab, you will find the **Trash** options near the bottom

---

### Post by forestpixie on 2007-10-30
don't know if this'll help - saw [this]("http://ubuntuforums.org/showthread.php?t=594091") thread today - worth a post I guess:)

---

### Post by Elv13 on 2007-10-30
no, actually, those file are not hidden, they are just having a "." before them, witch hide them in browser.

lepagee@lepagee-desktop:~$ ls ~/.Trash/
nautilus-debug-log.txt
lepagee@lepagee-desktop:~$ 

try!

But anyway, i will format, i am running out of space and i cant do nothing about it aparently. Probably a bad bug of gutsy alpha. Tip for who read this topic:

empty for trash, clean your apt cache, and free /tmp and /var/tmp. Also, to empty an admin trash, log on as admin or it will use your own trash (sudo su). This will do for 99% of peoples, but not me...

---

### Post by skyler91 on 2007-11-04
Try clearing out the folder:
~/.local/share/Trash

For some reason when I've been removing files using the GUI they've ended up there rather than showing in the trash bin on the desktop.


Addition:
Also, ~/.kde/share/apps/amarok contained 3gb+ of old collection information that I didn't need.

---

