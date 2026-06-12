---
title: "Problem with privileges"
date: 2013-02-21
forum: General Help
---

### Post by mr.suchy on 2013-02-21
Hi,

I dont know what but I enter this comand into the comand line

```

sudo chown -R my_login:my_login /  

```or something like that. Now everything is fine but when I want enter 

```

sudo <comand>

```or something like that I have warning
```
/etc/sudoers.d jest uid 1000, powinien by&#263; 0
```When I enter 
```
ls -l /etc
``````
drwxr-xr-x  3 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 acpi
-rw-r--r--  1 mrsuchy mrsuchy  2981 pa&#378; 17 19:05 adduser.conf
-rw-r--r--  1 mrsuchy mrsuchy    10 lis 18 18:13 adjtime
drwxr-xr-x  2 mrsuchy mrsuchy  4096 sty 27 19:17 adobe
drwxr-xr-x  2 mrsuchy mrsuchy 12288 lut 20 19:27 alternatives
-rw-r--r--  1 mrsuchy mrsuchy   401 maj 25  2012 anacrontab
drwxr-xr-x  7 mrsuchy mrsuchy  4096 lut 20 19:47 apache2
drwxr-xr-x  6 mrsuchy mrsuchy  4096 lut 19 18:40 apm
drwxr-xr-x  3 mrsuchy mrsuchy  4096 lis 19 18:00 apparmor
drwxr-xr-x  8 mrsuchy mrsuchy  4096 lut 20 19:22 apparmor.d
drwxr-xr-x  4 mrsuchy mrsuchy  4096 lis 19 18:01 apport
drwxr-xr-x  6 mrsuchy mrsuchy  4096 sty 26 15:20 apt
-rw-r-----  1 mrsuchy mrsuchy   144 cze 11  2012 at.deny
drwxr-xr-x  2 mrsuchy mrsuchy  4096 gru  1 11:24 at-spi2
drwxr-xr-x  3 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 avahi
-rw-r--r--  1 mrsuchy mrsuchy  2177 wrz 19 15:42 bash.bashrc
-rw-r--r--  1 mrsuchy mrsuchy    45 cze 17  2012 bash_completion
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 20 19:25 bash_completion.d
-rw-r--r--  1 mrsuchy mrsuchy   356 pa&#378;  4 03:14 bindresvport.blacklist
-rw-r--r--  1 mrsuchy mrsuchy   321 wrz  6 23:28 blkid.conf
lrwxrwxrwx  1 root    root       15 lis 18 18:08 blkid.tab -> /dev/.blkid.tab
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 bluetooth
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lis 23 23:52 bonobo-activation
-rw-r--r--  1 mrsuchy mrsuchy    33 pa&#378; 17 19:08 brlapi.key
drwxr-xr-x  2 mrsuchy mrsuchy 12288 pa&#378; 17 19:08 brltty
-rw-r--r--  1 mrsuchy mrsuchy 21169 wrz 19 17:57 brltty.conf
drwxr-xr-x  3 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 ca-certificates
-rw-r--r--  1 mrsuchy mrsuchy  6854 pa&#378; 17 19:08 ca-certificates.conf
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 calendar
drwxr-s---  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 chatscripts
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lis 23 22:32 chromium-browser
-rw-r--r--  1 mrsuchy mrsuchy   871 pa&#378; 10 12:30 colord.conf
drwxr-xr-x  5 mrsuchy mrsuchy  4096 pa&#378; 17 19:06 ConsoleKit
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:05 console-setup
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 20 19:27 cron.d
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 20 19:25 cron.daily
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:05 cron.hourly
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 cron.monthly
-rw-r--r--  1 mrsuchy mrsuchy   722 cze 14  2012 crontab
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 cron.weekly
drwxr-xr-x  4 root    lp       4096 pa&#378; 17 19:07 cups
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 cupshelpers
drwxr-xr-x  4 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 dbus-1
-rw-r--r--  1 mrsuchy mrsuchy  2969 sie 16  2012 debconf.conf
-rw-r--r--  1 mrsuchy mrsuchy    11 lip  3  2012 debian_version
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 20 19:25 default
-rw-r--r--  1 mrsuchy mrsuchy   604 maj  1  2012 deluser.conf
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:05 depmod.d
drwxr-xr-x  4 mrsuchy mrsuchy  4096 lis 19 18:01 dhcp
drwxr-xr-x  3 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 dhcp3
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lis 19 18:47 dictionaries-common
drwxr-xr-x  3 mrsuchy mrsuchy  4096 lis 24 10:04 dkms
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 dnsmasq.d
drwxr-xr-x  3 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 doc-base
drwxr-xr-x  4 mrsuchy mrsuchy  4096 lis 24 10:04 dpkg
-rw-r--r--  1 mrsuchy mrsuchy   347 sie  8  2012 eclipse.ini
drwxr-xr-x  3 mrsuchy mrsuchy  4096 pa&#378; 17 19:06 emacs
-rw-r--r--  1 mrsuchy mrsuchy    96 pa&#378; 17 19:05 environment
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lis 24 09:35 firefox
drwxr-xr-x  4 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 fonts
drwxr-xr-x  3 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 foomatic
-rw-r--r--  1 mrsuchy mrsuchy   867 lis 18 18:07 fstab
drwxr-xr-x  2 mrsuchy mrsuchy  4096 wrz  6 23:28 fstab.d
-rw-r-----  1 mrsuchy mrsuchy   216 pa&#378; 18  2011 fuse.conf
-rw-r--r--  1 mrsuchy mrsuchy  3343 pa&#378;  4 03:14 gai.conf
drwxr-xr-x  5 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 gconf
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 gdb
drwxr-xr-x  4 mrsuchy mrsuchy  4096 pa&#378; 17 19:06 ghostscript
drwxr-xr-x  3 mrsuchy mrsuchy  4096 lis 23 19:33 gimp
-rw-r--r--  1 mrsuchy mrsuchy   580 lip 16  2012 gnashpluginrc
-rw-r--r--  1 mrsuchy mrsuchy  5597 lip 16  2012 gnashrc
-rw-r--r--  1 mrsuchy mrsuchy   690 lip 16  2012 gnashthumbnailrc
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 gnome
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 gnome-app-install
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 gnome-system-tools
drwxr-xr-x  3 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 gnome-vfs-2.0
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 groff
-rw-r--r--  1 mrsuchy mrsuchy   885 lut 21 20:07 group
-rw-------  1 mrsuchy mrsuchy   878 lut 20 19:22 group-
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 grub.d
-rw-r-----  1 mrsuchy mrsuchy   737 lut 21 20:07 gshadow
-rw-------  1 mrsuchy mrsuchy   730 lut 20 19:22 gshadow-
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 gtk-2.0
drwxr-xr-x  2 mrsuchy mrsuchy  4096 gru  1 11:24 gtk-3.0
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 gtkmathview
-rw-r--r--  1 mrsuchy mrsuchy  4728 maj  1  2012 hdparm.conf
-rw-r--r--  1 mrsuchy mrsuchy    92 lip  3  2012 host.conf
-rw-r--r--  1 mrsuchy mrsuchy    16 lis 18 18:12 hostname
-rw-r--r--  1 mrsuchy mrsuchy   296 lut 21 20:16 hosts
-rw-r--r--  1 mrsuchy mrsuchy   580 pa&#378; 17 19:08 hosts.allow
-rw-r--r--  1 mrsuchy mrsuchy   880 pa&#378; 17 19:08 hosts.deny
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 hp
drwxr-xr-x  3 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 ifplugd
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lis 27 17:45 ImageMagick
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 20 19:22 init
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 21 21:54 init.d
drwxr-xr-x  5 mrsuchy mrsuchy  4096 pa&#378; 17 19:05 initramfs-tools
-rw-r--r--  1 mrsuchy mrsuchy  1721 wrz 18 14:21 inputrc
drwxr-xr-x  3 mrsuchy mrsuchy  4096 sie 10  2012 insserv
-rw-r--r--  1 mrsuchy mrsuchy   839 sie 10  2012 insserv.conf
drwxr-xr-x  2 mrsuchy mrsuchy  4096 sie 10  2012 insserv.conf.d
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:05 iproute2
-rw-r--r--  1 mrsuchy mrsuchy    20 pa&#378;  9 16:59 issue
-rw-r--r--  1 mrsuchy mrsuchy    13 pa&#378;  9 16:59 issue.net
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lis 23 23:53 java-6-openjdk
drwxr-xr-x  5 mrsuchy mrsuchy  4096 lis 23 23:52 java-7-openjdk
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:05 kbd
drwxr-xr-x  6 mrsuchy mrsuchy  4096 lis 24 10:04 kernel
-rw-r--r--  1 mrsuchy mrsuchy   110 lis 18 18:15 kernel-img.conf
-rw-r--r--  1 mrsuchy mrsuchy  1311 lip 20  2012 kerneloops.conf
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 ldap
-rw-r--r--  1 mrsuchy mrsuchy 77545 lut 20 19:25 ld.so.cache
-rw-r--r--  1 mrsuchy mrsuchy    34 pa&#378; 17 19:05 ld.so.conf
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 ld.so.conf.d
-rw-r--r--  1 mrsuchy mrsuchy   267 lip  3  2012 legal
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 libnl-3
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 19 19:12 libpaper.d
drwxr-xr-x  2 mrsuchy mrsuchy  4096 sty  1 12:39 libreoffice
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 lightdm
-rw-r--r--  1 mrsuchy mrsuchy  1291 wrz 28 18:38 lintianrc
-rw-r--r--  1 mrsuchy mrsuchy  2570 sie  5  2010 locale.alias
-rw-r--r--  1 mrsuchy mrsuchy  2679 lis 18 18:13 localtime
drwxr-xr-x  5 mrsuchy mrsuchy  4096 lut 20 19:22 logcheck
-rw-r--r--  1 mrsuchy mrsuchy 10551 wrz  6 21:14 login.defs
-rw-r--r--  1 mrsuchy mrsuchy   599 pa&#378;  4  2011 logrotate.conf
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 20 19:25 logrotate.d
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 10 20:31 lsb-base
-rw-r--r--  1 mrsuchy mrsuchy  3279 sie 15  2012 lsb-base-logging.sh
-rw-r--r--  1 mrsuchy mrsuchy   100 pa&#378;  9 14:14 lsb-release
-rw-r--r--  1 mrsuchy mrsuchy 15752 lip 25  2009 ltrace.conf
-rw-r--r--  1 mrsuchy mrsuchy   111 lip  1  2012 magic
-rw-r--r--  1 mrsuchy mrsuchy   111 lip  1  2012 magic.mime
-rw-r--r--  1 mrsuchy mrsuchy  9946 lut 19 19:11 mailcap
-rw-r--r--  1 mrsuchy mrsuchy   449 lip 16  2012 mailcap.order
-rw-r--r--  1 mrsuchy mrsuchy  5173 wrz 19 00:44 manpath.config
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lis 23 22:53 mc
drwxr-xr-x  2 mrsuchy mrsuchy  4096 gru  1 13:50 menu
drwxr-xr-x  2 mrsuchy mrsuchy  4096 gru  1 13:50 menu-methods
-rw-r--r--  1 mrsuchy mrsuchy 24166 gru 16 01:30 mime.types
-rw-r--r--  1 mrsuchy mrsuchy   956 sie 23  2012 mke2fs.conf
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 19 18:40 modprobe.d
-rw-r--r--  1 mrsuchy mrsuchy   215 gru  9 21:34 modules
drwxr-xr-x  4 mrsuchy mrsuchy  4096 lut  7 17:11 mono
lrwxrwxrwx  1 root    root       13 lis 18 18:08 motd -> /var/run/motd
-rw-r--r--  1 mrsuchy mrsuchy   793 lut 21 22:21 mtab
-rw-------  1 mrsuchy mrsuchy     0 lis 18 19:01 mtab.fuselock
-rw-r--r--  1 mrsuchy mrsuchy   624 sie  8  2007 mtools.conf
drwxr-xr-x  3 mrsuchy mrsuchy  4096 lut 20 19:22 mysql
-rw-r--r--  1 mrsuchy mrsuchy  8453 pa&#378;  1 16:11 nanorc
drwxr-xr-x  3 mrsuchy mrsuchy  4096 lis 19 16:54 ndiswrapper
drwxr-xr-x  6 mrsuchy mrsuchy  4096 pa&#378; 17 19:05 network
drwxr-xr-x  6 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 NetworkManager
-rw-r--r--  1 mrsuchy mrsuchy    91 lip  3  2012 networks
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:05 newt
-rw-r--r--  1 mrsuchy mrsuchy   513 pa&#378; 17 19:08 nsswitch.conf
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 obex-data-server
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lis 23 19:15 openal
drwxr-xr-x  3 mrsuchy mrsuchy  4096 lis 24 10:54 OpenCL
drwxr-xr-x  3 mrsuchy mrsuchy  4096 lis 19 18:14 opt
-rw-r--r--  1 mrsuchy mrsuchy   128 pa&#378; 23 23:53 os-release
-rw-r--r--  1 mrsuchy mrsuchy   552 lip  3  2012 pam.conf
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 21 21:54 pam.d
-rw-r--r--  1 mrsuchy mrsuchy     3 lis 18 18:14 papersize
-rw-r--r--  1 mrsuchy mrsuchy  1668 lut 20 19:22 passwd
-rw-------  1 mrsuchy mrsuchy  1653 lut 20 19:22 passwd-
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 pcmcia
drwxr-xr-x  4 mrsuchy mrsuchy  4096 pa&#378; 17 19:06 perl
drwxr-xr-x  6 mrsuchy mrsuchy  4096 lut 20 19:27 php5
drwxr-xr-x  3 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 pkcs11
drwxr-xr-x  5 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 pm
-rw-r--r--  1 mrsuchy mrsuchy  7649 pa&#378; 17 19:08 pnm2ppa.conf
drwxr-xr-x  5 mrsuchy mrsuchy  4096 pa&#378; 17 19:06 polkit-1
-rw-r--r--  1 mrsuchy mrsuchy   350 lis 18 18:14 popularity-contest.conf
drwxr-xr-x  8 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 ppp
-rw-r--r--  1 mrsuchy mrsuchy   665 lis 19 17:59 profile
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 profile.d
-rw-r--r--  1 mrsuchy mrsuchy  2933 lip  3  2012 protocols
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 19 18:39 pulse
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 purple
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 python
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 python2.7
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:05 python3
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lis 19 18:01 python3.2
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 20 19:25 rc0.d
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 20 19:25 rc1.d
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 21 21:54 rc2.d
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 21 21:54 rc3.d
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 21 21:54 rc4.d
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 21 21:54 rc5.d
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 20 19:25 rc6.d
-rwxr-xr-x  1 mrsuchy mrsuchy   306 pa&#378; 17 19:05 rc.local
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 rcS.d
drwxr-xr-x  5 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 resolvconf
lrwxrwxrwx  1 root    root       29 lis 18 18:12 resolv.conf -> ../run/resolvconf/resolv.conf
-rwxr-xr-x  1 mrsuchy mrsuchy   268 mar 31  2012 rmt
-rw-r--r--  1 mrsuchy mrsuchy   887 lip  3  2012 rpc
-rw-r--r--  1 mrsuchy mrsuchy  1263 mar 30  2012 rsyslog.conf
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 rsyslog.d
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 samba
drwxr-xr-x  3 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 sane.d
-rw-r--r--  1 mrsuchy mrsuchy  3902 wrz  6 21:14 securetty
drwxr-xr-x  4 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 security
-rw-r--r--  1 mrsuchy mrsuchy 10333 pa&#378;  5 13:36 sensors3.conf
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 sensors.d
-rw-r--r--  1 mrsuchy mrsuchy 19398 lip  3  2012 services
drwxr-xr-x  3 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 sgml
-rw-r-----  1 mrsuchy mrsuchy  1141 lut 20 19:22 shadow
-rw-------  1 mrsuchy mrsuchy  1141 lut 20 19:22 shadow-
-rw-r--r--  1 mrsuchy mrsuchy    73 pa&#378; 17 19:05 shells
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 skel
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 snmp
drwxr-xr-x  3 mrsuchy mrsuchy  4096 lis 23 23:51 sound
drwxr-xr-x  4 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 speech-dispatcher
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 ssh
drwxr-xr-x  4 mrsuchy mrsuchy  4096 pa&#378; 17 19:07 ssl
-r--r-----  1 root    root      745 lip 16  2012 sudoers
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lut 21 21:54 sudoers.d
-rw-r--r--  1 mrsuchy mrsuchy    19 maj  1  2011 su-to-rootrc
-rw-r--r--  1 mrsuchy mrsuchy  2263 sty 27 19:22 sysctl.conf
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:05 sysctl.d
drwxr-xr-x  3 mrsuchy mrsuchy  4096 pa&#378; 17 19:05 systemd
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:05 terminfo
drwxr-xr-x 12 mrsuchy mrsuchy  4096 lut 19 19:11 texmf
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lis 24 09:36 thunderbird
-rw-r--r--  1 mrsuchy mrsuchy    14 lis 18 18:13 timezone
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lis 23 19:16 timidity
-rw-r--r--  1 mrsuchy mrsuchy   645 maj  1  2012 ts.conf
-rw-r--r--  1 mrsuchy mrsuchy  1260 maj 30  2008 ucf.conf
drwxr-xr-x  3 mrsuchy mrsuchy  4096 pa&#378; 17 19:05 udev
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378;  9 21:45 udisks2
drwxr-xr-x  3 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 ufw
-rw-r--r--  1 mrsuchy mrsuchy   326 sie 15  2012 updatedb.conf
drwxr-xr-x  3 mrsuchy mrsuchy  4096 lis 19 18:01 update-manager
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lis 19 18:01 update-motd.d
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 10 00:41 update-notifier
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 UPower
-rw-r--r--  1 mrsuchy mrsuchy   572 pa&#378;  9 04:08 usb_modeswitch.conf
drwxr-xr-x  2 mrsuchy mrsuchy  4096 wrz 19 15:13 usb_modeswitch.d
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lis 19 18:01 vim
drwx------  2 mrsuchy mrsuchy  4096 lut  3 21:54 vpnc
lrwxrwxrwx  1 root    root       23 lis 18 18:08 vtrgb -> /etc/alternatives/vtrgb
-rw-r--r--  1 mrsuchy mrsuchy  4496 cze 15  2012 wgetrc
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lis 23 19:15 wildmidi
drwxr-xr-x  2 mrsuchy mrsuchy  4096 pa&#378; 17 19:08 wpa_supplicant
drwxr-xr-x 10 mrsuchy mrsuchy  4096 lis 24 10:59 X11
drwxr-xr-x  7 mrsuchy mrsuchy  4096 sty 31 18:54 xdg
-rw-r--r--  1 mrsuchy mrsuchy   289 sie 17  2012 xinetd.conf
drwxr-xr-x  2 mrsuchy mrsuchy  4096 sty 22 19:42 xinetd.d
drwxr-xr-x  3 mrsuchy mrsuchy  4096 lut 19 19:11 xml
drwxr-xr-x  2 mrsuchy mrsuchy  4096 lis 24 09:36 xul-ext
-rw-r--r--  1 mrsuchy mrsuchy   349 sty 13  2012 zsh_command_not_found
```I see my_login:my_login. How can I fix this problem ? :p

---edit
I run ubuntu from live CD and login as root. Then I enter this comand
```
sudo chown -R root:root /etc 
```And everything looks fine. But when I login into my Xubuntu, my_login was owner and group of /etc :-/

--edit

I think I have solution:
```

Let's do this from the terminal
   1) sudo -i
   2) sudo chown root.root /etc/*
   3) sudo chmod 755 /etc/*
   4) exit

```
If I must change another folder ?

---

### Post by Impavidus on 2013-02-21
You set yourself as the owner of your entire file system. Not on the live system, but on your installed system. By giving yourself as ordinary user writing rights to directories like /bin you basically disabled security. You are not root but you don't need to be root anymore to destroy the system.

But sudo depends on some files being owned by root, so that didn't work. Then you changed the owner of /etc/* to root and set permissions to 755. This is slightly better, but still many files don't have the correct owner or permission. A 100,000 of them may be trivial (root:root, 644), but some 1000s are not. Ideally you'd have to find the correct permissions and owner for all of them and change them one by one.

Or back up your home directory and maybe some other files and reinstall.

Just don't mess with permissions and owners of system files.

---

