---
title: "GRUB2 broke Gusty"
date: 2007-10-24
forum: General Help
---

### Post by obsrv on 2007-10-24
Tonight I wanted to test GRUB2 for the first time in my life and I'm failed. Currently I'm Windows XP user, for a long time I was Gentoo user, now I'm planning to buy MacBook for work and have KUbuntu as desktop, but KUbuntu at this time didn't make my happy.

This is log of what I did NOW with KUbuntu 7.10 Gusty Gibon CD:

```

Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> setup (hd0)
setup (hd0)

Error 12: Invalid device requested
grub> root (hd1,3)
root (hd1,3)

Error 22: No such partition
grub> quit
quit
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# mount /dev/sdb
sdb   sdb1  sdb2  sdb3
root@ubuntu:/home/ubuntu# mount /dev/sdb2 /mnt/
root@ubuntu:/home/ubuntu# mount -t proc none /mnt/proc/
root@ubuntu:/home/ubuntu# mount -o bind /dev /mnt/dev/
root@ubuntu:/home/ubuntu# chroot /mnt/ /bin/bash
root@ubuntu:/# cd /
root@ubuntu:/# env-update
bash: env-update: command not found
root@ubuntu:/# export PS1="(ubuntu-&#12367;&#12381;) $PS1"
(ubuntu-&#12367;&#12381;) root@ubuntu:/# apt-get update
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1) gutsy/main
Translation-en_US
Ign cdrom://Kubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1) gutsy/restr
icted Translation-en_US
Get:1 [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy Release.gpg [191B]
Ign [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy/main Translation-en_US
Ign [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy/universe Translation-en_US
Ign [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy/restricted Translation-en_US
Ign [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy/multiverse Translation-en_US
Get:2 [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-updates Release.gpg [191B]
Ign [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-updates/universe Translation-en_US
Ign [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-updates/main Translation-en_US
Ign [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-updates/multiverse Translation-en_US
Ign [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-updates/restricted Translation-en_US
Get:3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Get:5 [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-proposed Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Ign [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-proposed/universe Translation-en_US
Ign [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-proposed/main Translation-en_US
Ign [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-proposed/multiverse Translation-en_US
Ign [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-proposed/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Get:6 [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-backports Release.gpg [191B]
Ign [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-backports/universe Translation-en_US
Ign [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-backports/main Translation-en_US
Ign [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-backports/multiverse Translation-en_US
Ign [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-backports/restricted Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy Release
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-proposed Release
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-backports Release
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy/main Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy/universe Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy/restricted Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy/multiverse Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy/main Sources
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy/universe Sources
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy/restricted Sources
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy/multiverse Sources
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-updates/main Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-updates/multiverse Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-updates/restricted Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-updates/universe Sources
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-updates/main Sources
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-updates/multiverse Sources
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-updates/restricted Sources
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-proposed/universe Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-proposed/main Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-proposed/multiverse Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-proposed/restricted Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-proposed/universe Sources
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-proposed/main Sources
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-proposed/multiverse Sources
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-proposed/restricted Sources
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-backports/main Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-backports/multiverse Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-backports/restricted Packages
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-backports/universe Sources
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-backports/main Sources
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-backports/multiverse Sources
Hit [http://ftp.linux.edu.lv](http://ftp.linux.edu.lv) gutsy-backports/restricted Sources
Fetched 6B in 0s (10B/s)
Reading package lists... Done
(ubuntu-&#12367;&#12381;) root@ubuntu:/# apt-get purge grub2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package grub2 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  python-gnome2 python-pyorbit libxml2-utils libbeagle0 docbook-xml
  python-gnomecanvas python-glade2 librarian0 yelp sgml-data
  liblaunchpad-integration0 python-gconf gnome-doc-utils
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
(ubuntu-&#12367;&#12381;) root@ubuntu:/# apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-gnome2 python-pyorbit libxml2-utils libbeagle0 docbook-xml
  python-gnomecanvas python-glade2 librarian0 yelp sgml-data
  liblaunchpad-integration0 python-gconf gnome-doc-utils
The following packages will be REMOVED:
  docbook-xml gnome-doc-utils libbeagle0 liblaunchpad-integration0 librarian0
  libxml2-utils python-gconf python-glade2 python-gnome2 python-gnomecanvas
  python-pyorbit sgml-data yelp
0 upgraded, 0 newly installed, 13 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 14.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 92677 files and directories currently installed.)
Removing yelp ...
Removing docbook-xml ...
Removing gnome-doc-utils ...
Removing libbeagle0 ...
Removing liblaunchpad-integration0 ...
Removing librarian0 ...
Removing libxml2-utils ...
Removing python-gnome2 ...
Removing python-gconf ...
Removing python-glade2 ...
Removing python-gnomecanvas ...
Removing python-pyorbit ...
Removing sgml-data ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: /lib32/libQtAssistantClient.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtScript.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtCore.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtGui.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtDesignerComponents.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtDesigner.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtNetwork.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtDBus.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtSvg.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtTest.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtXml.so.4 is not a symbolic link

/sbin/ldconfig.real: /lib32/libdbus-1.so.3 is not a symbolic link

/sbin/ldconfig.real: /lib32/libQtOpenGL.so.4 is not a symbolic link

(ubuntu-&#12367;&#12381;) root@ubuntu:/# apt-get
apt 0.7.6ubuntu14.1 for amd64 compiled on Oct 22 2007 10:47:43
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   purge - Remove and purge packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to continue if the integrity check fails
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
(ubuntu-&#12367;&#12381;) root@ubuntu:/# apt-get purge grub
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  grub*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 1843kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 91990 files and directories currently installed.)
Removing grub ...
(ubuntu-&#12367;&#12381;) root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  grub-doc mdadm
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/847kB of archives.
After unpacking 1843kB of additional disk space will be used.
Selecting previously deselected package grub.
(Reading database ... 91944 files and directories currently installed.)
Unpacking grub (from .../grub_0.97-29ubuntu4_amd64.deb) ...
Setting up grub (0.97-29ubuntu4) ...

(ubuntu-&#12367;&#12381;) root@ubuntu:/# apt-get reinstall
E: Invalid operation reinstall
(ubuntu-&#12367;&#12381;) root@ubuntu:/# apt-get
apt 0.7.6ubuntu14.1 for amd64 compiled on Oct 22 2007 10:47:43
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   purge - Remove and purge packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to continue if the integrity check fails
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
(ubuntu-&#12367;&#12381;) root@ubuntu:/# apt-get check
Reading package lists... Done
Building dependency tree
Reading state information... Done
(ubuntu-&#12367;&#12381;) root@ubuntu:/# apt-get purge linux-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-generic*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 53.2kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 91990 files and directories currently installed.)
Removing linux-generic ...
(ubuntu-&#12367;&#12381;) root@ubuntu:/# apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not up
(ubuntu-&#12367;&#12381;) root@ubuntu:/# apt-get install linux-gene
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be install
  linux-generic
0 upgraded, 1 newly installed, 0 to
Need to get 0B/25.4kB of archives.
After unpacking 53.2kB of addit
Selecting previously deselected
(Reading database ... 91988 fil
Unpacking linux-generic (from .
Setting up linux-generic (2.6.2
(ubuntu-&#12367;&#12381;) root@ubuntu:/# ad
adept_batch      adept_installe
(ubuntu-&#12367;&#12381;) root@ubuntu:/#

(ubuntu-&#12367;&#12381;) root@ubun
E: Invalid operation pu
(ubuntu-&#12367;&#12381;) root@ubun
(ubuntu-&#12367;&#12381;) root@ubuntu:/# apt-get purge linux-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-generic*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.                      Need to get 0B of archives.
After unpacking 53.2kB disk space will be freed.                                    Do you want to continue [Y/n]? y
(Reading database ... 91990 files and directories currently installed.)
Removing linux-generic ...
(ubuntu-&#12367;&#12381;) root@ubuntu:/# apt-get install linux-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  linux-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.4kB of archives.
After unpacking 53.2kB of additional disk space will be used.
Selecting previously deselected package linux-generic.
(Reading database ... 91988 files and directories currently installed.)
Unpacking linux-generic (from .../linux-generic_2.6.22.14.21_amd64.deb) ...
Setting up linux-generic (2.6.22.14.21) ...
(ubuntu-&#12367;&#12381;) root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree
Reading state information... Done
grub is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
(ubuntu-&#12367;&#12381;) root@ubuntu:/# grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> quit
quit
(ubuntu-&#12367;&#12381;) root@ubuntu:/# ls /boot/
abi-2.6.22-14-generic         initrd.img-2.6.22-14-generic.bak
config-2.6.22-14-generic      memtest86+.bin
grub                          System.map-2.6.22-14-generic
initrd.img-2.6.22-14-generic  vmlinuz-2.6.22-14-generic
(ubuntu-&#12367;&#12381;) root@ubuntu:/# ls /boot/grub/
acorn.mod       core.img      halt.mod      minix.mod       terminfo.mod
affs.mod        cpuid.mod     hello.mod     moddep.lst      test.mod
amiga.mod       device.map    help.mod      _multiboot.mod  tga.mod
apple.mod       diskboot.img  hfs.mod       multiboot.mod   ufs.mod
bitmap.mod      elf.mod       hfsplus.mod   normal.mod      vbeinfo.mod
blocklist.mod   ext2.mod      iso9660.mod   pc.mod          vbe.mod
boot.img        fat.mod       jfs.mod       play.mod        vbetest.mod
boot.mod        font.mod      kernel.img    pxeboot.img     video.mod
cat.mod         fshelp.mod    _linux.mod    raid.mod        videotest.mod
_chain.mod      fs.lst        linux.mod     reboot.mod      xfs.mod
chain.mod       gfxterm.mod   loopback.mod  search.mod
cmp.mod         gpt.mod       ls.mod        sfs.mod
command.lst     grub.cfg      lvm.mod       sun.mod
configfile.mod  gzio.mod      menu.lst      terminal.mod
(ubuntu-&#12367;&#12381;) root@ubuntu:/# cat /boot/grub/menu.lst

#
gfxmenu /boot/grub/message.snow
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
#password --md5 $1$ZJkQC$jeZqb/6U71fHuNazfdHcF/
#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b35b3d2f-a6a2-4484-8414-dd1673cf610a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=795

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Chainload into GRUB 2
root            (hd1,1)
kernel          /boot/grub/core.img
savedefault

title           Debian GNU/Linux, kernel 2.6.22-14-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b35b3d2f-a6a2-4484-8414-dd1673cf610a ro quiet splash vga=795
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Windows XP Professional
root            (hd0,0)
makeactive
chainloader     +1
(ubuntu-&#12367;&#12381;) root@ubuntu:/# grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> setup (hd0)
setup (hd0)

Error 12: Invalid device requested
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub>
```

My /boot/grub/menu.lst:

```

#
gfxmenu /boot/grub/message.snow
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
#password --md5 $1$ZJkQC$jeZqb/6U71fHuNazfdHcF/
#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b35b3d2f-a6a2-4484-8414-dd1673cf610a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
(ubuntu-****) root@ubuntu:/#    # alternative=false

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=795

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Chainload into GRUB 2
root            (hd1,1)
kernel          /boot/grub/core.img
savedefault

title           Debian GNU/Linux, kernel 2.6.22-14-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b35b3d2f-a6a2-4484-8414-dd1673cf610a ro quiet splash vga=795
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Windows XP Professional
root            (hd0,0)
makeactive
chainloader     +1
(ubuntu-****) root@ubuntu:/# cat /boot/grub/menu.lst

#
gfxmenu /boot/grub/message.snow
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
#password --md5 $1$ZJkQC$jeZqb/6U71fHuNazfdHcF/
#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b35b3d2f-a6a2-4484-8414-dd1673cf610a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=795

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Chainload into GRUB 2
root            (hd1,1)
kernel          /boot/grub/core.img
savedefault

title           Debian GNU/Linux, kernel 2.6.22-14-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b35b3d2f-a6a2-4484-8414-dd1673cf610a ro quiet splash vga=795
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Windows XP Professional
root            (hd0,0)
makeactive
chainloader     +1
```

My /boot/grub/grub.cfg for GRUB2 (generated automatically):

```
#
# DO NOT EDIT THIS FILE
#
# It is automaticaly generated by /usr/sbin/update-grub using templates from /etc/grub.d
# and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd1,2)

font (hd1,2)/usr/share/grub/unifont.pff
set gfxmode=640x480
insmod gfxterm
insmod vbe
terminal gfxterm
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Debian GNU/Linux, linux 2.6.22-14-generic" {
	linux	(hd1,2)/boot/vmlinuz-2.6.22-14-generic root=/dev/sdb2 ro 
	initrd	(hd1,2)/boot/initrd.img-2.6.22-14-generic
}
menuentry "Debian GNU/Linux, linux 2.6.22-14-generic (single-user mode)" {
	linux	(hd1,2)/boot/vmlinuz-2.6.22-14-generic root=/dev/sdb2 ro single 
	initrd	(hd1,2)/boot/initrd.img-2.6.22-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux	(hd1,2)/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

```

The problem is NOW when MBR gets read I am booted to GRUB2 Rescue console. How do I overwrite MBR to use GRUB Legacy??? :confused:

---

### Post by obsrv on 2007-10-24
Please help, NOW I'M SITTING WITH LIVECD... O_o

_EDIT by obsrv:_

I took a **nap** for 2h and I found the problem :lolflag: I needed just to write grub-install /dev/sda using GRUB Legacy, what I was doing I tried that using GRUB2 which is strange for me now... Long story short, I will stick now to GRUB Legacy :)

---

