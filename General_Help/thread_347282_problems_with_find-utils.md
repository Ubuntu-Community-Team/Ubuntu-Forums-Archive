---
title: "problems with find-utils"
date: 2007-01-27
forum: General Help
---

### Post by dunja on 2007-01-27
I'm trying to upgrade an installation of dapper drake which hasn't been upgraded in a while.  When I try "aptitude dist-upgrade", it fails because common system commands aren't available.  Here's an example of one of the error messages:
```
[...]
/var/lib/dpkg/info/python2.4-tk.prerm: line 11: xargs: command not found
[...]
```

The common "find" utility is also missing.

When I try to check the status of the binary, I see:
```
$ ls -al /usr/bin/find
ls: /usr/bin/find: Permission denied
```

And as a super-user:
```
$ sudo ls -al /usr/bin/find
ls: /usr/bin/find: Permission denied
```

When I try to reinstall one of the packages that contains the missing files it fails:
```
$ sudo aptitude reinstall findutils
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done      
The following packages have been kept back:
[...] 
The following packages will be REINSTALLED:
  findutils 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 231 not upgraded.
Need to get 0B/298kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 129860 files and directories currently installed.)
Preparing to replace findutils 4.2.27-1ubuntu1 (using .../findutils_4.2.27-1ubuntu1_i386.deb) ...
Document `findutils' is not installed, cannot remove.
Unpacking replacement findutils ...
dpkg: error processing /var/cache/apt/archives/findutils_4.2.27-1ubuntu1_i386.deb (--unpack):
 unable to stat `./usr/bin/find' (which I was about to install): Permission deni
ed                                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/findutils_4.2.27-1ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

I also tried a plain "aptitude install":
```
$ sudo aptitude install findutils
Reading package lists... Done
Building dependency tree... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
The following packages have been kept back:
[...]
0 packages upgraded, 0 newly installed, 0 to remove and 231 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
```

How did my system get in this state and how can I fix it?

---

### Post by taurus on 2007-01-27
Did you remember to run the update first?

```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by dunja on 2007-01-27
Yep, right before trying to upgrade.

---

### Post by taurus on 2007-01-27
What happens if you run these two commands?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by dunja on 2007-01-27
```
$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:3 http://archive.ubuntu.com dapper-security Release.gpg [191B]
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper-security/restricted Packages
Hit http://archive.ubuntu.com dapper-security/universe Packages
Hit http://archive.ubuntu.com dapper-security/multiverse Packages
Fetched 3B in 2s (1B/s)
Reading package lists... Done

```

```
$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
The following packages will be upgraded:
  acpi-support app-install-data app-install-data-commercial bind9-host
  binutils binutils-static capplets-data cpio cupsys cupsys-bsd
  cupsys-client dbus dbus-1-utils deskbar-applet desktop-file-utils
  dnsutils dpkg-dev dselect eog evince fetchmail ffmpeg file-roller firefox
  firefox-gnome-support gdb gdm gedit gedit-common gimp gimp-data
  gimp-python gnome-about gnome-accessibility-themes gnome-app-install
  gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data
  gnome-doc-utils gnome-games gnome-games-data gnome-media gnome-menus
  gnome-panel gnome-panel-data gnome-screensaver gnome-session
  gnome-terminal gnome-terminal-data gnome-themes gnupg gstreamer0.10-alsa
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-x gtk2-engines-clearlooks
  gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice
  gtkhtml3.8 hal hal-device-manager imagemagick info kdelibs-data
  language-selector language-selector-common libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-glib1 libavahi-qt3-1
  libbind9-0 libcupsimage2 libcupsys2 libcupsys2-gnutls10 libdbus-1-2
  libdbus-glib-1-2 libdns21 libeel2-2 libeel2-data libfreetype6
  libfreetype6-dev libgd2-noxpm libgeoip1 libgimp2.0 libgnome-desktop-2
  libgnome-menu2 libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin
  libgnomevfs2-common libgnomevfs2-extra libgnutls11 libgnutls12
  libgsf-1-113 libgsf-1-common libgsf-gnome-1-113
  libgstreamer-plugins-base0.10-0 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgtk2.0-dev libgtkhtml3.8-15 libgtksourceview-common
  libgtksourceview1.0-0 libgtop2-7 libhal-storage1 libhal1 libimlib2
  libisc11 libisccc0 libisccfg1 libkrb53 liblwres9 libmagick9 libmetacity0
  libmono0 libmusicbrainz4c2a libmysqlclient15off libnautilus-burn3
  libnautilus-extension1 libnspr4 libnss3 libpanel-applet2-0 libpango1.0-0
  libpango1.0-common libpango1.0-dev libpng12-0 libpng12-dev libpoppler1
  libpoppler1-glib libpq4 libqt3-mt librpm4 libsmbclient libsoup2.2-8
  libssl0.9.7 libtiff4 libtotem-plparser1 libvte-common libvte4 libwmf0.2-7
  libwnck-common libwnck18 libxfont1 libxine-dev libxine-main1 linux-386
  linux-restricted-modules-common metacity mono-classlib-1.0 mono-common
  mono-jit mozilla-firefox mozilla-thunderbird mutt mysql-common nautilus
  nautilus-cd-burner nautilus-data openoffice.org openoffice.org-base
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-evolution openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  openoffice.org2-calc openoffice.org2-impress openoffice.org2-writer
  openssh-client openssh-server openssl pcmcia-cs pmount postfix ppp
  python-gmenu python-pyorbit python-uno python-vte python2.4
  python2.4-dbus python2.4-examples python2.4-minimal python2.4-pyorbit
  python2.4-samba python2.4-tk rpm samba samba-common smbclient
  sound-juicer ssh-askpass-gnome totem totem-xine ttf-opensymbol
  ubuntu-docs w3m xinit xorg-driver-fglrx xpdf xpdf-common xpdf-reader
  xpdf-utils xserver-xorg-core xserver-xorg-input-mouse yelp zenity
229 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 8888kB/241MB of archives. After unpacking 5026kB will be used.
Do you want to continue? [Y/n/?] y
Get:1 http://archive.ubuntu.com dapper-security/main mozilla-firefox 1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1 [50.7kB]
Get:2 http://archive.ubuntu.com dapper-security/main firefox-gnome-support 1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1 [75.4kB]
Get:3 http://archive.ubuntu.com dapper-security/main libnspr4 2:1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1 [147kB]
Get:4 http://archive.ubuntu.com dapper-security/main libnss3 2:1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1 [670kB]
Get:5 http://archive.ubuntu.com dapper-security/main firefox 1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1 [7944kB]
Fetched 8888kB in 4m9s (35.6kB/s)
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 129860 files and directories currently installed.)
Preparing to replace python2.4-tk 2.4.3-0ubuntu4 (using .../python2.4-tk_2.4.3-0ubuntu6_i386.deb) ...
/var/lib/dpkg/info/python2.4-tk.prerm: line 11: xargs: command not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: line 11: xargs: command not found
Package `prerm' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
dpkg: error processing /var/cache/apt/archives/python2.4-tk_2.4.3-0ubuntu6_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Preparing to replace python2.4 2.4.3-0ubuntu4 (using .../python2.4_2.4.3-0ubuntu6_i386.deb) ...
/var/lib/dpkg/info/python2.4.prerm: line 11: xargs: command not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: line 11: xargs: command not found
Package `prerm' is not installed.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
dpkg: error processing /var/cache/apt/archives/python2.4_2.4.3-0ubuntu6_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Compiling python modules in /usr/lib/python2.4 ...
Compiling optimized python modules in /usr/lib/python2.4 ...
Preparing to replace python2.4-minimal 2.4.3-0ubuntu4 (using .../python2.4-minimal_2.4.3-0ubuntu6_i386.deb) ...
/var/lib/dpkg/info/python2.4-minimal.prerm: line 7: xargs: command not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: line 7: xargs: command not found
dpkg: error processing /var/cache/apt/archives/python2.4-minimal_2.4.3-0ubuntu6_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/python2.4-tk_2.4.3-0ubuntu6_i386.deb
 /var/cache/apt/archives/python2.4_2.4.3-0ubuntu6_i386.deb
 /var/cache/apt/archives/python2.4-minimal_2.4.3-0ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

Thanks for the help.

---

### Post by dunja on 2007-01-27
(Renamed subject.)

Can anybody help?

---

### Post by fragos on 2007-01-27
Have you tried the method recommended by Ubuntu?

If you want to upgrade from 6.06 LTS to 6.10, run the following command (either via ALT-F2 or a terminal):

gksu "update-manager -c -d"

---

### Post by dunja on 2007-01-27
But I don't want to upgrade from 6.06 LTS to 6.10.  I just want to upgrade 6.06.

---

### Post by fragos on 2007-01-27
Are you trying to upgrade from an older version, which one, of Ubuntu or update 6.06 to the latest?

---

### Post by dunja on 2007-01-27
I'm trying to upgrade 6.06 to the latest 6.06.

---

### Post by dunja on 2007-01-28
Does anybody have any ideas what I can try next?

Should I ask in another Ubuntu forum/newgroup?

---

### Post by fragos on 2007-01-28
System-> Administration-> "Update Manager".  If your system is always connected to the Internet it should be up todate any way as you will be notified when updates are available in the notification area of upper applet panel.

---

### Post by dunja on 2007-01-28
I get the same errors as I do when I try using aptitude from the command line.

---

### Post by stylishpants on 2007-01-28
It looks like the permissions are screwed up on some important system directories.

Check the permissions with these commands.  

```

fraser@ged:~$ ls -ld /usr/
drwxr-xr-x 13 root root 4096 2006-10-31 22:20 /usr/

fraser@ged:~$ ls -ld /usr/bin
drwxr-xr-x 2 root root 28672 2007-01-27 18:47 /usr/bin


```

If your system was fine, then the output should match the output from my system, above.

However, I think it won't match.  The permissions have probably changed on these directories, and possibly the ownership as well.  You will also have to check that other files in /usr and /usr/bin have their correct permissions.

 Please post the output from these commands.

---

### Post by dunja on 2007-01-28
Looks like permissions of the directories are fine:
```
$ ls -ld /usr
drwxr-xr-x 13 root root 312 2007-01-26 08:44 /usr
```
```
$ ls -ld /usr/bin
drwxr-xr-x 2 root root 55608 2007-01-26 10:04 /usr/bin
```

But when I listed permissions for all files in /usr/bin, I found 15 files which even a superuser doesn't have permissions for:
```

$ sudo ls -la /usr/bin/
[...]
-rwxr-xr-x  1 root   root      13900 2006-05-05 10:50 users
-rwxr-xr-x  1 root   root     122988 2006-05-29 05:05 users-admin
?---------  ? ?      ?             ?                ? /usr/bin/col
?---------  ? ?      ?             ?                ? /usr/bin/efstool
?---------  ? ?      ?             ?                ? /usr/bin/find
?---------  ? ?      ?             ?                ? /usr/bin/locate.notslocate
?---------  ? ?      ?             ?                ? /usr/bin/neotoppm
?---------  ? ?      ?             ?                ? /usr/bin/pi1toppm
?---------  ? ?      ?             ?                ? /usr/bin/pilprint.py
?---------  ? ?      ?             ?                ? /usr/bin/pjtoppm
?---------  ? ?      ?             ?                ? /usr/bin/ppm3d
?---------  ? ?      ?             ?                ? /usr/bin/ppmbrighten
?---------  ? ?      ?             ?                ? /usr/bin/ppmchange
?---------  ? ?      ?             ?                ? /usr/bin/ppmcolormask
?---------  ? ?      ?             ?                ? /usr/bin/ppmcolors
?---------  ? ?      ?             ?                ? /usr/bin/updatedb.notslocate
?---------  ? ?      ?             ?                ? /usr/bin/xargs
-rwxr-xr-x  1 root   root       3832 2006-05-12 05:46 uuidgen
-rwxr-xr-x  1 root   root       2147 2006-05-17 23:45 uxterm
[...]
```

Which means I couldn't change the permissions on those files in the normal way:
```
$ sudo chown root:root /usr/bin/find
chown: cannot access `/usr/bin/find': Permission denied
```

So I booted to a live Ubuntu CD, ran a fsck on the filesystem /usr/bin is on, and it came back with three corruptions..

```
$ sudo fsck.reiserfs /dev/hda3
reiserfsck 3.6.19 (2003 www.namesys.com)

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to reiserfs-list@namesys.com, **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  www.namesys.com/support.html. **
*************************************************************

Will read-only check consistency of the filesystem on /dev/hda3
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes
###########
reiserfsck --check started at Sun Jan 28 22:16:53 2007
###########
Replaying journal..
Reiserfs journal '/dev/hda3' in blocks [18..8211]: 0 transactions replayed
Checking internal tree../  1 (of   2)/  1 (of  95)/109 (of 132)block 32945: The number of items (17) is incorrect, should be (1)
 the problem in the internal node occured (32945), whole subtree is skipped
/ 18 (of  95)/ 70 (of 134)bad_path: The left delimiting key [242 34005 0x671 DRCT (2)] of the node (2162699) must be equal to the first element's key [242 34005 0x673 DRCT (2)] within the node.
/ 33 (of  95)/ 29 (of 124)block 4259943: The number of items (29) is incorrect, should be (1)
 the problem in the internal node occured (4259943), whole subtree is skipped
/  2 (of   2)/ 97 (of 128)/ 11 (of 107)bad_indirect_item: block 2588779: The item (114473 114475 0x1 IND (1), len 284, location 1824 entry count 0, fsck need 0, format new) has the bad pointer (66) to the block (1674707), which is in tree already
bad_indirect_item: block 2588779: The item (114473 114475 0x1 IND (1), len 284, location 1824 entry count 0, fsck need 0, format new) has the bad pointer (68) to the block (1674708), which is in tree already
finished                  
Comparing bitmaps..vpf-10640: The on-disk and the correct bitmaps differs.
Bad nodes were found, Semantic pass skipped
3 found corruptions can be fixed only when running with --rebuild-tree
###########
reiserfsck finished at Sun Jan 28 22:18:01 2007
###########
```

Then I reran it with --rebuild-tree to fix the corruptions:

```
$ sudo fsck.reiserfs --rebuild-tree /dev/hda3
reiserfsck 3.6.19 (2003 www.namesys.com)

*************************************************************
** Do not  run  the  program  with  --rebuild-tree  unless **
** something is broken and MAKE A BACKUP  before using it. **
** If you have bad sectors on a drive  it is usually a bad **
** idea to continue using it. Then you probably should get **
** a working hard drive, copy the file system from the bad **
** drive  to the good one -- dd_rescue is  a good tool for **
** that -- and only then run this program.                 **
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to reiserfs-list@namesys.com, **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  www.namesys.com/support.html. **
*************************************************************

Will rebuild the filesystem (/dev/hda3) tree
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes
Replaying journal..
Reiserfs journal '/dev/hda3' in blocks [18..8211]: 0 transactions replayed
###########
reiserfsck --rebuild-tree started at Sun Jan 28 22:18:26 2007
###########

Pass 0:
####### Pass 0 #######
Loading on-disk bitmap .. ok, 901512 blocks marked used
Skipping 8360 blocks (super block, journal, bitmaps) 893152 blocks will be read
0%block 32945: The number of items (17) is incorrect, should be (1) - corrected
block 32945: The free space (916) is incorrect, should be (4004) - corrected
....20%...pass0: vpf-10210: block 2162699, item 0: The item with wrong offset or length found [242 34005 0x673 DRCT (2)], len 1184 - deleted
.40%....60%....80%block 4259943: The number of items (29) is incorrect, should be (1) - corrected
block 4259943: The free space (46) is incorrect, should be (4004) - corrected
pass0: vpf-10100: block 4259943, item (0): Unknown item type of StatData size, type set to StatData [268 14418 0x0 SD (0)]
....100%                        left 0, 6334 /sec
156812 directory entries were hashed with "r5" hash.
        "r5" hash is selected
Flushing..finished
        Read blocks (but not data blocks) 893152
                Leaves among those 32423
                        - corrected leaves 1
                Objectids found 156371

Pass 1 (will try to insert 32423 leaves):
####### Pass 1 #######
Looking for allocable blocks .. finished
0%....20%....40%....60%....80%....100%                        left 0, 1350 /sec
Flushing..finished
        32423 leaves read
                32162 inserted
                261 not inserted
        non-unique pointers in indirect items (zeroed) 2
####### Pass 2 #######

Pass 2:
0%....20%....40%....60%....80%....100%                         left 0, 522 /sec
Flushing..finished
        Leaves inserted item by item 261
Pass 3 (semantic):
####### Pass 3 #########
/etc/dbus-1/system.drebuild_semantic_pass: The entry [2 39143] ("bluez.conf") in directory [2 32985] points to nowhere - is removed
vpf-10650: The directory [2 32985] has the wrong size in the StatData (216) - corrected to (184)
/bluetooth/pinvpf-10680: The file [2 38571] has the wrong block count in the StatData (8) - corrected to (0)
/lib/discoverrebuild_semantic_pass: The entry [2 38592] ("usb-26.lst") in directory [2 13879] points to nowhere - is removed
rebuild_semantic_pass: The entry [2 38591] ("sbus.lst") in directory [2 13879] points to nowhere - is removed
rebuild_semantic_pass: The entry [2 38586] ("pci-sparc.lst") in directory [2 13879] points to nowhere - is removed
rebuild_semantic_pass: The entry [2 38590] ("sbus-26.lst") in directory [2 13879] points to nowhere - is removed
rebuild_semantic_pass: The entry [2 38593] ("usb.lst") in directory [2 13879] points to nowhere - is removed
rebuild_semantic_pass: The entry [2 38588] ("pcmcia-26.lst") in directory [2 13879] points to nowhere - is removed
rebuild_semantic_pass: The entry [2 38587] ("pci.lst") in directory [2 13879] points to nowhere - is removed
rebuild_semantic_pass: The entry [2 38589] ("pcmcia.lst") in directory [2 13879] points to nowhere - is removed
vpf-10650: The directory [2 13879] has the wrong size in the StatData (376) - corrected to (144)
/usr/binrebuild_semantic_pass: The entry [268 14513] ("col") in directory [241 268] points to nowhere - is removed
rebuild_semantic_pass: The entry [268 14533] ("locate.notslocate") in directory [241 268] points to nowhere - is removed
rebuild_semantic_pass: The entry [268 14509] ("find") in directory [241 268] points to nowhere - is removed
rebuild_semantic_pass: The entry [268 14540] ("ppmcolormask") in directory [241 268] points to nowhere - is removed
rebuild_semantic_pass: The entry [268 14492] ("ppm3d") in directory [241 268] points to nowhere - is removed
rebuild_semantic_pass: The entry [268 14532] ("xargs") in directory [241 268] points to nowhere - is removed
rebuild_semantic_pass: The entry [268 14539] ("ppmchange") in directory [241 268] points to nowhere - is removed
rebuild_semantic_pass: The entry [268 14454] ("efstool") in directory [241 268] points to nowhere - is removed
rebuild_semantic_pass: The entry [268 14541] ("ppmcolors") in directory [241 268] points to nowhere - is removed
rebuild_semantic_pass: The entry [268 14534] ("updatedb.notslocate") in directory [241 268] points to nowhere - is removed
rebuild_semantic_pass: The entry [268 14491] ("neotoppm") in directory [241 268] points to nowhere - is removed
/pi1toppmvpf-10680: The file [268 14418] has the wrong block count in the StatData (16) - corrected to (0)
rebuild_semantic_pass: The entry [268 14497] ("ppmbrighten") in directory [241 268] points to nowhere - is removed
rebuild_semantic_pass: The entry [268 14465] ("pjtoppm") in directory [241 268] points to nowhere - is removed
rebuild_semantic_pass: The entry [268 14463] ("pilprint.py") in directory [241 268] points to nowhere - is removed
vpf-10680: The directory [241 268] has the wrong block count in the StatData (109) - corrected to (108)
vpf-10650: The directory [241 268] has the wrong size in the StatData (55608) - corrected to (55200)
... no/gac/Microsoft.JScript/7.0.5000.0__b03f5f7f11d50a3a/Microsoft.JScript.dllvpf-10680: The file [114473 114475] has the wrong block count in the StatData (568) - corrected to (552)
Flushing..finished                                                             
        Files found: 126295
        Directories found: 11732
        Symlinks found: 12832
        Others: 5489
        Names pointing to nowhere (removed): 23
Pass 3a (looking for lost dir/files):
####### Pass 3a (lost+found pass) #########
Looking for lost directories:
Flushing..finished5, 289 /sec
Pass 4 - finished done 10900, 175 /sec
        Deleted unreachable items 3
Flushing..finished
Syncing..finished
###########
reiserfsck finished at Sun Jan 28 22:22:20 2007
###########

```

Then I mounted the partition, chrooted to it, reinstalled the critical system utilities, and dist-upgraded.

```
$ sudo mount /dev/hda3 /mnt/hda3
$ sudo mount -t proc procfs /mnt/hda3/proc/
$ sudo chroot /mnt/hda3/
# aptitude reinstall findutils
# aptitude dist-upgrade
```

I think it should be okay now.  Thanks for the help!

---

### Post by stylishpants on 2007-01-28
Great job in getting things back up and running.

Keep in mind that this is quite an unusual thing to happen.  Filesystem corruption may be a sign of failing hardware.  

You should frequently check /var/log/messages and output from 'dmesg' for the next while, and look for warnings about failed writes or reads, or anything else that looks unusual.

Good luck.

---

### Post by dunja on 2007-01-28
A memory module went bad not too long ago.  I think that's probably what caused the filesystem corruption.

---

