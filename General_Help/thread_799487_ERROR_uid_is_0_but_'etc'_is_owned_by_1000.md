---
title: "ERROR: uid is 0 but '/etc' is owned by 1000"
date: 2008-05-19
forum: General Help
---

### Post by DSP8000 on 2008-05-19
This is the error that I'm keep on getting when I try to enable ufw in Ubuntu Hardy.
ivan@ivan-laptop:~$ sudo ufw enable
ERROR: uid is 0 but '/etc' is owned by 1000


Does anyone know how to fix this. My desktop is fine but on my laptop I can't enable the firewall.

Any help is appreciated.

DSP8000

---

### Post by bingoUV on 2008-05-19
Did you have any adventures with chmod on your laptop? Post the output of the following commands : 
```

ls -l /
ls -l /etc

```

---

### Post by DSP8000 on 2008-05-19
Here's the log:

ivan@ivan-laptop:~$ ls -l /
total 84
drwxr-xr-x   2 root root  4096 2008-05-10 15:04 bin
drwxr-xr-x   3 root root  4096 2008-04-27 06:03 boot
lrwxrwxrwx   1 root  999    11 2008-04-26 19:48 cdrom -> media/cdrom
drwxr-xr-x  13 root root 13780 2008-05-20 00:20 dev
drwxr-xr-x 132 ivan ivan 12288 2008-05-20 00:20 etc
drwxr-xr-x   4 root root  4096 2008-04-26 20:01 home
drwxr-xr-x   2 root root  4096 2008-04-23 03:48 initrd
lrwxrwxrwx   1 root  999    33 2008-04-27 06:03 initrd.img -> boot/initrd.img-2.6.24-16-generic
drwxr-xr-x  16 root root  4096 2008-04-27 06:04 lib
drwx------   2 root root 16384 2008-04-26 19:47 lost+found
drwxr-xr-x   4 root root  4096 2008-05-20 00:20 media
drwxr-xr-x   2 root root  4096 2008-04-15 15:53 mnt
drwxr-xr-x   4 root root  4096 2008-05-19 14:35 opt
dr-xr-xr-x 121 root root     0 2008-05-20 10:19 proc
drwxr-xr-x  18 root root  4096 2008-05-19 15:34 root
drwxr-xr-x   2 root root  4096 2008-05-15 14:21 sbin
drwxr-xr-x   2 root root  4096 2008-04-23 03:48 srv
drwxr-xr-x  12 root root     0 2008-05-20 10:19 sys
drwxrwxrwt  14 root root  4096 2008-05-20 00:20 tmp
drwxr-xr-x  12 ivan ivan  4096 2008-05-18 15:39 usr
drwxr-xr-x  15 root root  4096 2008-04-23 04:07 var
lrwxrwxrwx   1 root  999    30 2008-04-27 06:03 vmlinuz -> boot/vmlinuz-2.6.24-16-generic
ivan@ivan-laptop:~$ ls -l /etc
total 1448
drwxr-xr-x  8 root root      4096 2008-04-23 04:01 acpi
-rw-r--r--  1 root root      2975 2008-04-23 03:49 adduser.conf
-rw-r--r--  1 root root        46 2008-05-19 16:41 adjtime
-rw-r--r--  1 root root        49 2008-04-26 20:01 aliases
drwxr-xr-x  2 root root      4096 2008-05-18 16:45 alternatives
-rw-r--r--  1 root root       395 2007-03-05 17:38 anacrontab
drwxr-xr-x  7 root root      4096 2008-04-23 04:01 apm
drwxr-xr-x  2 root root      4096 2008-05-09 09:58 apparmor
drwxr-xr-x  6 root root      4096 2008-04-23 03:52 apparmor.d
drwxr-xr-x  3 root root      4096 2008-05-09 09:58 apport
drwxr-xr-x  4 root root      4096 2008-05-19 16:56 apt
-rw-r-----  1 root daemon     144 2007-02-21 00:41 at.deny
drwxr-xr-x  3 root root      4096 2008-04-23 04:06 avahi
-rw-r--r--  1 root root      1733 2008-04-15 13:36 bash.bashrc
-rw-r--r--  1 root root    216529 2008-04-15 11:45 bash_completion
drwxr-xr-x  2 root root      4096 2008-04-23 04:05 bash_completion.d
drwxr-xr-x  2 root root      4096 2008-04-23 03:49 belocs
-rw-r--r--  1 root root       332 2008-04-05 09:16 bindresvport.blacklist
-rw-r--r--  1 root root       521 2008-04-27 06:03 blkid.tab
drwxr-xr-x  2 root root      4096 2008-04-23 04:06 bluetooth
-rw-r--r--  1 root root      6813 2008-02-25 07:22 bogofilter.cf
drwxr-xr-x  2 root root      4096 2008-04-23 03:59 bonobo-activation
-rw-r--r--  1 root root        33 2008-04-23 04:05 brlapi.key
drwxr-xr-x  2 root root      4096 2008-04-23 04:05 brltty
-rw-r--r--  1 root root     15721 2008-03-28 10:25 brltty.conf
-rw-r--r--  1 root root      4867 2008-04-23 04:02 ca-certificates.conf
drwxr-xr-x  2 root root      4096 2008-04-23 04:00 calendar
drwxr-s---  2 root dip       4096 2008-04-23 04:01 chatscripts
drwxr-xr-x  2 root root      4096 2008-04-23 04:02 compizconfig
-rw-r--r--  1 root root     55367 2006-07-06 07:15 complete.tcsh
drwxr-xr-x  3 root root      4096 2008-04-23 03:51 ConsoleKit
drwxr-xr-x  2 root root      4096 2008-04-23 03:49 console-setup
drwxr-xr-x  2 root root      4096 2008-04-23 03:49 console-tools
drwxr-xr-x  2 root root      4096 2008-04-23 04:01 cron.d
drwxr-xr-x  2 root root      4096 2008-05-09 09:58 cron.daily
drwxr-xr-x  2 root root      4096 2008-04-23 04:01 cron.hourly
drwxr-xr-x  2 root root      4096 2008-04-23 04:01 cron.monthly
-rw-r--r--  1 root root       724 2008-04-09 04:02 crontab
drwxr-xr-x  2 root root      4096 2008-04-23 04:01 cron.weekly
drwxr-xr-x  3 root root      4096 2008-05-10 15:04 csh
-rw-r--r--  1 root root       428 2006-07-06 07:15 csh.cshrc
-rw-r--r--  1 root root       275 2006-07-06 07:15 csh.login
-rw-r--r--  1 root root        67 2006-07-06 07:15 csh.logout
drwxr-xr-x  4 root lp        4096 2008-05-19 09:53 cups
drwxr-xr-x  5 root root      4096 2008-04-23 04:06 dbus-1
-rw-r--r--  1 root root      2969 2008-03-12 02:51 debconf.conf
-rw-r--r--  1 root root        10 2007-10-20 21:51 debian_version
drwxr-xr-x  2 root root      4096 2008-05-19 16:57 default
drwxr-xr-x  4 root root      4096 2008-04-23 03:58 defoma
-rw-r--r--  1 root root       600 2007-10-24 01:01 deluser.conf
drwxr-xr-x  2 root root      4096 2008-04-23 03:49 depmod.d
drwxr-xr-x  4 root root      4096 2008-04-23 03:54 devfs
drwxr-xr-x  4 root root      4096 2008-04-23 03:49 dhcp3
drwxr-xr-x  2 root root      4096 2008-04-23 04:11 dictionaries-common
drwxr-xr-x  2 root root      4096 2008-04-22 01:50 dm
drwxr-xr-x  3 root root      4096 2008-04-23 03:53 doc-base
drwxr-xr-x  3 root root      4096 2008-05-09 09:38 dpkg
-rw-r--r--  1 root root        34 2008-02-19 15:33 e2fsck.conf
drwxr-xr-x  3 root root      4096 2008-04-23 03:51 emacs
-rw-r--r--  1 root root       118 2008-04-26 11:09 environment
drwxr-xr-x  2 root root      4096 2008-04-23 03:59 esound
drwxr-xr-x  2 root root      4096 2008-04-23 03:49 event.d
-rw-r--r--  1 root root       354 2007-03-05 17:54 fdmount.conf
-rw-r--r--  1 root root      8366 2008-03-24 08:29 ffserver.conf
drwxr-xr-x  4 root root      4096 2008-04-23 03:53 firefox-3.0
drwxr-xr-x  4 root root      4096 2008-04-23 03:51 fonts
drwxr-xr-x  3 root root      4096 2008-04-23 03:54 foomatic
-rw-r--r--  1 root root       623 2008-05-19 16:32 fstab
-rw-r--r--  1 root root       651 2008-05-06 23:32 fstab.pre-ntfs-config
-rw-r-----  1 root fuse       216 2008-02-27 05:25 fuse.conf
-rw-r--r--  1 root root      2689 2008-04-05 09:16 gai.conf
drwxr-xr-x  2 root root      4096 2008-04-23 04:05 gamin
drwxr-xr-x  6 root root      4096 2008-04-23 03:51 gconf
drwxr-xr-x  7 root root      4096 2008-05-17 10:29 gdm
drwxr-xr-x  3 root root      4096 2008-04-26 10:23 ggi
drwxr-xr-x  3 root root      4096 2008-04-23 03:53 gimp
drwxr-xr-x  3 root root      4096 2008-05-18 15:45 gnome
drwxr-xr-x  2 root root      4096 2008-04-23 04:01 gnome-app-install
drwxr-xr-x  3 root root      4096 2008-04-23 03:53 gnome-system-tools
drwxr-xr-x  4 root root      4096 2008-04-23 03:51 gnome-vfs-2.0
-rw-r--r--  1 root root     10852 2007-04-28 12:27 gnome-vfs-mime-magic
drwxr-xr-x  2 root root      4096 2008-05-09 09:59 gre.d
drwxr-xr-x  2 root root      4096 2008-04-23 04:00 groff
-rw-r--r--  1 root root       853 2008-04-26 20:01 group
-rw-------  1 root root       849 2008-04-26 20:01 group-
drwxr-xr-x  2 root root      4096 2008-04-23 04:01 grub.d
-rw-r-----  1 root shadow     708 2008-04-26 20:01 gshadow
-rw-------  1 root root       704 2008-04-26 20:01 gshadow-
drwxr-xr-x  2 root root      4096 2008-05-17 10:29 gtk-2.0
drwxr-xr-x  3 root root      4096 2008-04-23 03:53 hal
-rw-r--r--  1 root root      4793 2008-03-29 09:26 hdparm.conf
-rw-r--r--  1 root root       425 2008-04-23 04:03 hesiod.conf
-rw-r--r--  1 root root        92 2007-10-20 21:51 host.conf
-rw-r--r--  1 root root        12 2008-04-26 20:01 hostname
-rw-r--r--  1 root     999    247 2008-04-26 20:01 hosts
-rw-r--r--  1 root root       579 2008-04-23 03:49 hosts.allow
-rw-r--r--  1 root root       878 2008-04-23 03:49 hosts.deny
drwxr-xr-x  2 root root      4096 2008-04-23 03:59 hp
drwxr-xr-x  2 root root      4096 2008-04-23 04:03 hwtest.d
drwxr-xr-x  2 root root      4096 2008-05-19 16:57 init.d
drwxr-xr-x  5 root root      4096 2008-04-23 03:49 initramfs-tools
-rw-r--r--  1 root root      1723 2007-10-03 00:35 inputrc
drwxr-xr-x  2 root root      4096 2008-04-23 03:49 iproute2
-rw-r--r--  1 root root        19 2008-04-15 15:53 issue
-rw-r--r--  1 root root        12 2008-04-15 15:53 issue.net
drwxr-xr-x  5 root root      4096 2008-05-18 14:41 java-6-openjdk
drwxr-xr-x  4 root root      4096 2008-05-18 15:36 java-6-sun
-rw-r--r--  1 root root       294 2006-05-08 20:56 jvm
drwxr-xr-x  4 root root      4096 2008-05-09 16:10 kde3
-rw-r--r--  1 root root       167 2008-04-27 06:03 kernel-img.conf
drwxr-xr-x 10 root root      4096 2008-04-23 04:01 laptop-mode
drwxr-xr-x  2 root root      4096 2008-05-09 09:58 ldap
-rw-r--r--  1 root root     63239 2008-05-19 13:57 ld.so.cache
-rw-r--r--  1 root root        34 2008-04-23 03:49 ld.so.conf
drwxr-xr-x  2 root root      4096 2008-04-23 03:49 ld.so.conf.d
-rw-r--r--  1 root root      3578 2007-11-16 03:03 lftp.conf
-rw-r--r--  1 root root        20 2007-10-24 13:09 libao.conf
drwxr-xr-x  2 root root      4096 2007-11-14 22:01 libpaper.d
-rw-r--r--  1 root root      2586 2008-03-11 22:02 locale.alias
-rw-r--r--  1 root     999   2183 2008-04-26 20:01 localtime
drwxr-xr-x  5 root root      4096 2008-04-23 03:52 logcheck
-rw-r--r--  1 root root      9681 2008-04-03 12:08 login.defs
-rw-r--r--  1 root root       599 2006-06-20 04:21 logrotate.conf
drwxr-xr-x  2 root root      4096 2008-05-19 13:52 logrotate.d
drwxr-xr-x  2 root root      4096 2008-03-27 05:23 lsb-base
-rw-r--r--  1 root root      3820 2008-03-11 06:00 lsb-base-logging.sh
-rw-r--r--  1 root root        96 2008-04-15 15:04 lsb-release
-rw-r--r--  1 root root     13144 2007-11-16 23:04 ltrace.conf
-rw-r--r--  1 root root       111 2007-10-24 09:03 magic
-rw-r--r--  1 root root       111 2007-10-24 09:03 magic.mime
-rw-r--r--  1 root root     21738 2008-05-19 14:35 mailcap
-rw-r--r--  1 root root       449 2008-04-02 05:11 mailcap.order
-rw-r--r--  1 root root      4624 2008-03-13 00:24 manpath.config
-rw-r--r--  1 root root     11742 2007-03-05 17:54 mediaprm
drwxr-xr-x  2 root root      4096 2008-05-09 09:59 menu-methods
-rw-r--r--  1 root root        40 2008-05-15 14:38 mfpcommon.modules.conf
-rw-r--r--  1 root root     20891 2008-04-02 05:11 mime.types
-rw-r--r--  1 root root       417 2008-03-28 04:25 mke2fs.conf
-rw-r--r--  1 root root        40 2008-05-15 14:38 modprobe.conf
drwxr-xr-x  3 root root      4096 2008-04-23 04:03 modprobe.d
-rw-r--r--  1 root root       208 2008-04-27 06:02 modules
drwxr-xr-x  2 root root      4096 2008-04-23 04:03 modutils
drwxr-xr-x  4 root root      4096 2008-04-23 04:02 mono
lrwxrwxrwx  1 root root        13 2008-04-26 19:48 motd -> /var/run/motd
-rw-r--r--  1 root root       346 2008-04-23 03:49 motd.tail
drwxr-xr-x  2 root root      4096 2008-05-18 14:22 mplayer
-rw-r--r--  1 root root       293 2008-03-18 11:54 mplayerplug-in.conf
-rw-r--r--  1 root root       965 2008-03-18 11:54 mplayerplug-in.types
-rw-r--r--  1 root root       758 2008-05-20 00:20 mtab
drwxr-xr-x  3 root root      4096 2008-05-09 12:59 mysql
-rw-r--r--  1 root root      7672 2008-04-09 00:02 nanorc
-rw-r--r--  1 root root      2064 2006-11-24 06:33 netscsid.conf
drwxr-xr-x  6 root root      4096 2008-04-23 03:49 network
drwxr-xr-x  3 root root      4096 2008-04-23 03:54 NetworkManager
-rw-r--r--  1 root root        91 2007-05-16 02:07 networks
-rw-r--r--  1 root root       513 2008-04-23 04:08 nsswitch.conf
-rw-r--r--  1 root root         0 2008-04-03 23:12 odbc.ini
-rw-r--r--  1 root root         0 2008-04-03 23:12 odbcinst.ini
-rw-r--r--  1 root root        60 2007-12-04 10:31 openalrc
drwxr-xr-x  2 root root      4096 2008-04-23 04:05 openoffice
drwxr-xr-x  2 root root      4096 2008-04-23 03:48 opt
-rw-r--r--  1 root root       552 2008-04-10 06:22 pam.conf
drwxr-xr-x  2 root root      4096 2008-05-17 10:29 pam.d
drwxr-xr-x  2 root root      4096 2008-04-23 03:58 pango
-rw-r--r--  1 root     999      3 2008-04-27 06:03 papersize
-rw-r--r--  1 root root      1457 2008-04-26 20:01 passwd
-rw-------  1 root root      1441 2008-04-26 20:01 passwd-
drwxr-xr-x  2 root root      4096 2008-04-23 03:49 pcmcia
drwxr-xr-x  4 root root      4096 2008-04-23 03:50 perl
drwxr-xr-x  5 root root      4096 2008-04-23 03:53 pm
-rw-r--r--  1 root root      7649 2008-04-23 04:03 pnm2ppa.conf
drwxr-xr-x  2 root root      4096 2008-04-23 04:07 PolicyKit
-rw-r--r--  1 root     999    342 2008-04-27 06:03 popularity-contest.conf
drwxr-xr-x  4 root root      4096 2008-04-23 03:52 power
drwxr-xr-x  8 root dip       4096 2008-04-23 04:01 ppp
-rw-r--r--  1 root root      4266 2007-05-01 04:21 preload.conf
-rw-r--r--  1 root root         0 2008-05-15 13:56 printcap
-rw-r--r--  1 root root       497 2008-04-23 03:49 profile
drwxr-xr-x  2 root root      4096 2008-04-15 15:53 profile.d
-rw-r--r--  1 root root      2510 2007-12-04 09:04 protocols
drwxr-xr-x  2 root root      4096 2008-04-23 04:03 pulse
drwxr-xr-x  2 root root      4096 2008-04-23 04:03 purple
drwxr-xr-x  2 root root      4096 2008-04-23 03:49 python
drwxr-xr-x  2 root root      4096 2008-04-23 03:49 python2.5
drwxr-xr-x  2 root root      4096 2008-05-15 14:43 qt3
drwxr-xr-x  2 root root      4096 2008-05-19 16:57 rc0.d
drwxr-xr-x  2 root root      4096 2008-05-19 16:57 rc1.d
drwxr-xr-x  2 root root      4096 2008-05-19 13:52 rc2.d
drwxr-xr-x  2 root root      4096 2008-05-19 13:52 rc3.d
drwxr-xr-x  2 root root      4096 2008-05-19 13:52 rc4.d
drwxr-xr-x  2 root root      4096 2008-05-19 13:52 rc5.d
drwxr-xr-x  2 root root      4096 2008-05-19 16:57 rc6.d
-rwxr-xr-x  1 root root       306 2008-04-23 03:49 rc.local
drwxr-xr-x  2 root root      4096 2008-05-19 16:57 rcS.d
drwxr-xr-x  2 root root      4096 2008-04-23 04:03 readahead
drwxr-xr-x  3 root root      4096 2008-04-23 03:53 resolvconf
-rw-r--r--  1 root root       152 2008-05-19 17:08 resolv.conf
-rw-r-----  1 root root     19593 2008-05-12 10:07 rkhunter.conf
-rwxr-xr-x  1 root root       268 2008-04-04 22:07 rmt
-rw-r--r--  1 root root       887 2007-12-04 09:04 rpc
drwxr-xr-x  2 root root      4096 2008-04-27 04:58 samba
drwxr-xr-x  3 ivan ivan      4096 2006-09-12 19:15 sane.d
drwxr-xr-x  2 root root      4096 2008-04-23 04:05 scim
-rw-r--r--  1 root root      3663 2007-10-24 02:02 screenrc
-rw-r--r--  1 root root        23 2007-12-07 00:20 scrollkeeper.conf
-rw-r--r--  1 root root      1024 2008-04-03 12:08 securetty
drwxr-xr-x  2 root root      4096 2008-04-23 03:49 security
-rw-r--r--  1 root root     18274 2007-12-04 09:04 services
drwxr-xr-x  3 root root      4096 2008-04-23 03:59 sgml
-rw-r-----  1 root shadow     912 2008-05-19 15:41 shadow
-rw-------  1 root root       846 2008-04-26 20:01 shadow-
-rw-r--r--  1 root root       181 2008-05-10 15:04 shells
drwxr-xr-x  2 root root      4096 2008-04-23 03:53 skel
drwxr-xr-x  3 root root      4096 2008-04-23 03:51 sound
drwxr-xr-x  2 root root      4096 2008-05-15 14:21 ssh
drwxr-xr-x  4 root root      4096 2008-05-15 14:21 ssl
-r--r-----  1 root root       470 2008-04-26 20:01 sudoers
-rw-r--r--  1 root root      2405 2008-03-14 09:24 sysctl.conf
-rw-r--r--  1 root root      1614 2007-11-23 20:06 syslog.conf
drwxr-xr-x  2 root root      4096 2008-04-23 03:49 terminfo
drwxr-xr-x  4 root root      4096 2008-05-10 16:37 thunderbird
-rw-r--r--  1 root root        17 2008-04-26 20:01 timezone
-rw-r--r--  1 root root      1260 2008-02-21 18:22 ucf.conf
drwxr-xr-x  3 root root      4096 2008-04-23 03:49 udev
drwxr-xr-x  2 root root      4096 2008-05-19 16:57 ufw
-rw-r--r--  1 root root       142 2008-01-25 03:51 uniconf.conf
-rw-r--r--  1 root root       214 2008-03-09 05:22 updatedb.conf
drwxr-xr-x  2 root root      4096 2008-05-15 14:21 update-manager
drwxr-xr-x  2 root root      4096 2008-04-05 08:34 update-notifier
-rw-r--r--  1 root root       116 2008-04-27 06:03 usplash.conf
drwxr-xr-x  2 root root      4096 2008-05-18 14:22 vga
drwxr-xr-x  2 root root      4096 2008-04-23 03:49 vim
drwxr-xr-x  2 root root      4096 2008-04-23 04:01 w3m
-rw-r--r--  1 root root      4221 2007-06-18 19:45 wgetrc
drwxr-xr-x  2 root root      4096 2008-05-18 14:41 wildmidi
-rw-r--r--  1 root root      1343 2007-01-10 05:39 wodim.conf
drwxr-xr-x  2 root root      4096 2008-04-23 03:49 wpa_supplicant
-rw-r-----  1 root dialout     66 2008-04-23 04:05 wvdial.conf
drwxr-xr-x 10 root root      4096 2008-04-26 10:23 X11
drwxr-xr-x  5 root root      4096 2008-04-23 04:05 xdg
drwxr-xr-x  2 root root      4096 2008-04-23 03:54 xml
drwxr-xr-x  2 root root      4096 2008-05-09 09:59 xulrunner-1.9
-rw-r--r--  1 root root       461 2008-04-04 06:33 zsh_command_not_found
ivan@ivan-laptop:~$ 

I can't remember doing something unusual or playing with chmod.
The last thing that I did was to update and install AWN trunk. That's it, nothing else. Any ideas?

---

### Post by Monicker on 2008-05-19
Your /etc folder should be owned by root, and not by ivan.  You did not change the default ownership of that direcotry???

```
chown -R root /etc
```


EDIT:  /usr also has the wrong ownership.  It should also be owned by root.

---

### Post by bingoUV on 2008-05-19
/etc/ufw seems to be fine. Just do 
```

sudo chown root /etc

```

---

### Post by bingoUV on 2008-05-19
Please don't use chown -R on /etc. No one knows what strange programs you have installed and what their requirements about ownership in files inside /etc. Ownership of /etc itself is incorrect so just fix it by chown without -R.

---

### Post by Monicker on 2008-05-19
> **bingoUV said:**
> Please don't use chown -R on /etc. No one knows what strange programs you have installed and what their requirements about ownership in files inside /etc. Ownership of /etc itself is incorrect so just fix it by chown without -R.

Root should own everything in /etc.  Group ownership may be different, but running the command as I gave it will not change that.

And ownership of /usr is still wrong in his case.

---

### Post by DSP8000 on 2008-05-19
nope, did not fix the problem. I ran the two commands and ran ls -l / after two reboots and etc has these values:

ivan@ivan-laptop:~$ ls -l /
total 84
drwxr-xr-x   2 root root  4096 2008-05-10 15:04 bin
drwxr-xr-x   3 root root  4096 2008-04-27 06:03 boot
lrwxrwxrwx   1 root  999    11 2008-04-26 19:48 cdrom -> media/cdrom
drwxr-xr-x  13 root root 13780 2008-05-20 00:52 dev
drwxr-xr-x 132 root ivan 12288 2008-05-20 00:52 etc
drwxr-xr-x   4 root root  4096 2008-04-26 20:01 home
drwxr-xr-x   2 root root  4096 2008-04-23 03:48 initrd
lrwxrwxrwx   1 root  999    33 2008-04-27 06:03 initrd.img -> boot/initrd.img-2.6.24-16-generic
drwxr-xr-x  16 root root  4096 2008-04-27 06:04 lib
drwx------   2 root root 16384 2008-04-26 19:47 lost+found
drwxr-xr-x   4 root root  4096 2008-05-20 00:52 media
drwxr-xr-x   2 root root  4096 2008-04-15 15:53 mnt
drwxr-xr-x   4 root root  4096 2008-05-19 14:35 opt
dr-xr-xr-x 122 root root     0 2008-05-20 10:51 proc
drwxr-xr-x  18 root root  4096 2008-05-19 15:34 root
drwxr-xr-x   2 root root  4096 2008-05-15 14:21 sbin
drwxr-xr-x   2 root root  4096 2008-04-23 03:48 srv
drwxr-xr-x  12 root root     0 2008-05-20 10:51 sys
drwxrwxrwt  14 root root  4096 2008-05-20 00:52 tmp
drwxr-xr-x  12 ivan ivan  4096 2008-05-18 15:39 usr
drwxr-xr-x  15 root root  4096 2008-04-23 04:07 var
lrwxrwxrwx   1 root  999    30 2008-04-27 06:03 vmlinuz -> boot/vmlinuz-2.6.24-16-generic
ivan@ivan-laptop:~$ sudo ufw status
[sudo] password for ivan: 
ERROR: uid is 0 but '/usr' is owned by 1000
ivan@ivan-laptop:~$ 


however exactly the same command on my desktop shows root root.

Any other fix?

---

### Post by Monicker on 2008-05-19
> **DSP8000 said:**
> nope, did not fix the problem. I ran the two commands and ran ls -l / after two reboots and etc has these values:

drwxr-xr-x 132 root ivan 12288 2008-05-20 00:52 etc

however exatcly the same command on my desktop shows root root.

Any other fix?

Is the error messages still the same?

Since the /etc directory should have owner and group of root, you can do

```
sudo chown root.root /etc
```


EDIT: Saw your amended post.  Its now complaining about /usr, which I mentioned earlier.  :)

---

### Post by bingoUV on 2008-05-19
> **Monicker said:**
> Root should own everything in /etc.  Group ownership may be different, but running the command as I gave it will not change that.

And ownership of /usr is still wrong in his case.

Files in the directory /etc/<application name>/ are a property of the developers of the application. They might require some particular ownership and we have no business changing that. Their installer will establish correct ownership but messing with them may not guarantee smooth operation.

Just for example, amanda prefers its /etc/ directories to be owned by a special user (by default called amanda).

---

### Post by DSP8000 on 2008-05-19
Hey, hey, hey :) finally

Here's the log:

```
ivan@ivan-laptop:~$ ls -l /
total 84
drwxr-xr-x   2 root root  4096 2008-05-10 15:04 bin
drwxr-xr-x   3 root root  4096 2008-04-27 06:03 boot
lrwxrwxrwx   1 root  999    11 2008-04-26 19:48 cdrom -> media/cdrom
drwxr-xr-x  13 root root 13780 2008-05-20 00:52 dev
drwxr-xr-x 132 root ivan 12288 2008-05-20 00:52 etc
drwxr-xr-x   4 root root  4096 2008-04-26 20:01 home
drwxr-xr-x   2 root root  4096 2008-04-23 03:48 initrd
lrwxrwxrwx   1 root  999    33 2008-04-27 06:03 initrd.img -> boot/initrd.img-2.6.24-16-generic
drwxr-xr-x  16 root root  4096 2008-04-27 06:04 lib
drwx------   2 root root 16384 2008-04-26 19:47 lost+found
drwxr-xr-x   4 root root  4096 2008-05-20 00:52 media
drwxr-xr-x   2 root root  4096 2008-04-15 15:53 mnt
drwxr-xr-x   4 root root  4096 2008-05-19 14:35 opt
dr-xr-xr-x 122 root root     0 2008-05-20 10:51 proc
drwxr-xr-x  18 root root  4096 2008-05-19 15:34 root
drwxr-xr-x   2 root root  4096 2008-05-15 14:21 sbin
drwxr-xr-x   2 root root  4096 2008-04-23 03:48 srv
drwxr-xr-x  12 root root     0 2008-05-20 10:51 sys
drwxrwxrwt  14 root root  4096 2008-05-20 00:52 tmp
drwxr-xr-x  12 ivan ivan  4096 2008-05-18 15:39 usr
drwxr-xr-x  15 root root  4096 2008-04-23 04:07 var
lrwxrwxrwx   1 root  999    30 2008-04-27 06:03 vmlinuz -> boot/vmlinuz-2.6.24-16-generic
ivan@ivan-laptop:~$ sudo ufw status
[sudo] password for ivan: 
ERROR: uid is 0 but '/usr' is owned by 1000
ivan@ivan-laptop:~$ sudo chown root.root /etc
ivan@ivan-laptop:~$ ls -l /
total 84
drwxr-xr-x   2 root root  4096 2008-05-10 15:04 bin
drwxr-xr-x   3 root root  4096 2008-04-27 06:03 boot
lrwxrwxrwx   1 root  999    11 2008-04-26 19:48 cdrom -> media/cdrom
drwxr-xr-x  13 root root 13780 2008-05-20 00:58 dev
drwxr-xr-x 132 root root 12288 2008-05-20 00:58 etc
drwxr-xr-x   4 root root  4096 2008-04-26 20:01 home
drwxr-xr-x   2 root root  4096 2008-04-23 03:48 initrd
lrwxrwxrwx   1 root  999    33 2008-04-27 06:03 initrd.img -> boot/initrd.img-2.6.24-16-generic
drwxr-xr-x  16 root root  4096 2008-04-27 06:04 lib
drwx------   2 root root 16384 2008-04-26 19:47 lost+found
drwxr-xr-x   4 root root  4096 2008-05-20 00:58 media
drwxr-xr-x   2 root root  4096 2008-04-15 15:53 mnt
drwxr-xr-x   4 root root  4096 2008-05-19 14:35 opt
dr-xr-xr-x 121 root root     0 2008-05-20 10:51 proc
drwxr-xr-x  18 root root  4096 2008-05-19 15:34 root
drwxr-xr-x   2 root root  4096 2008-05-15 14:21 sbin
drwxr-xr-x   2 root root  4096 2008-04-23 03:48 srv
drwxr-xr-x  12 root root     0 2008-05-20 10:51 sys
drwxrwxrwt  14 root root  4096 2008-05-20 00:58 tmp
drwxr-xr-x  12 ivan ivan  4096 2008-05-18 15:39 usr
drwxr-xr-x  15 root root  4096 2008-04-23 04:07 var
lrwxrwxrwx   1 root  999    30 2008-04-27 06:03 vmlinuz -> boot/vmlinuz-2.6.24-16-generic
ivan@ivan-laptop:~$ sudo ufw status
ERROR: uid is 0 but '/usr' is owned by 1000
ivan@ivan-laptop:~$ sudo chown root.root /usr
ivan@ivan-laptop:~$ ls -l /
total 84
drwxr-xr-x   2 root root  4096 2008-05-10 15:04 bin
drwxr-xr-x   3 root root  4096 2008-04-27 06:03 boot
lrwxrwxrwx   1 root  999    11 2008-04-26 19:48 cdrom -> media/cdrom
drwxr-xr-x  13 root root 13780 2008-05-20 00:58 dev
drwxr-xr-x 132 root root 12288 2008-05-20 00:58 etc
drwxr-xr-x   4 root root  4096 2008-04-26 20:01 home
drwxr-xr-x   2 root root  4096 2008-04-23 03:48 initrd
lrwxrwxrwx   1 root  999    33 2008-04-27 06:03 initrd.img -> boot/initrd.img-2.6.24-16-generic
drwxr-xr-x  16 root root  4096 2008-04-27 06:04 lib
drwx------   2 root root 16384 2008-04-26 19:47 lost+found
drwxr-xr-x   4 root root  4096 2008-05-20 00:58 media
drwxr-xr-x   2 root root  4096 2008-04-15 15:53 mnt
drwxr-xr-x   4 root root  4096 2008-05-19 14:35 opt
dr-xr-xr-x 121 root root     0 2008-05-20 10:51 proc
drwxr-xr-x  18 root root  4096 2008-05-19 15:34 root
drwxr-xr-x   2 root root  4096 2008-05-15 14:21 sbin
drwxr-xr-x   2 root root  4096 2008-04-23 03:48 srv
drwxr-xr-x  12 root root     0 2008-05-20 10:51 sys
drwxrwxrwt  14 root root  4096 2008-05-20 00:58 tmp
drwxr-xr-x  12 root root  4096 2008-05-18 15:39 usr
drwxr-xr-x  15 root root  4096 2008-04-23 04:07 var
lrwxrwxrwx   1 root  999    30 2008-04-27 06:03 vmlinuz -> boot/vmlinuz-2.6.24-16-generic
ivan@ivan-laptop:~$ sudo ufw

Usage: ufw COMMAND

Commands:
  enable			Enables the firewall
  disable			Disables the firewall
  default ARG			set default policy to ALLOW or DENY
  logging ARG			set logging to ON or OFF
  allow|deny RULE		allow or deny RULE
  delete allow|deny RULE	delete the allow/deny RULE
  status			show firewall status
  version			display version information

ivan@ivan-laptop:~$ sudo ufw enable
Firewall started and enabled on system startup
ivan@ivan-laptop:~$ 


```

That did the job so thank you guys :popcorn:=D>\\:D/

---

### Post by Monicker on 2008-05-19
> **DSP8000 said:**
> Hey, hey, hey :) finally


<snip>

That did the job so thank you guys :popcorn:=D>\\:D/


Cool.  :)

---

### Post by d4v1dv00 on 2008-08-02
how could I give a Thank to DSP8000?

---

### Post by Onewheeler on 2008-10-03
I've got the same problem, and found /etc was owned by me (martin martin). I've run chown and now have the correct ownership root root for /etc and for /etc/ufw (the latter was already owned by root root)

sudo ufw gives a correct response, but sudo ufw <anything else> is still giving the "ERROR: uid is 0 but '/etc' is owned by 1000" message.

(Yes, I have rebooted!)

Any ideas anyone?

martin@Vicky:~$ ls -l /
total 92
drwxr-xr-x   2 root   root    4096 2008-09-02 22:31 bin
drwxr-xr-x   3 root   root    4096 2008-09-02 22:45 boot
lrwxrwxrwx   1 root   root      11 2008-09-02 22:32 cdrom -> media/cdrom
drwxr-xr-x  13 root   root   14260 2008-10-03 17:18 dev
drwxr-xr-x 132 root   root   12288 2008-10-03 17:19 etc
drwxr-xr-x   3 root   root    4096 2008-09-02 22:42 home
drwxr-xr-x   2 root   root    4096 2008-04-22 18:48 initrd
lrwxrwxrwx   1 root   root      33 2008-09-02 22:39 initrd.img -> boot/initrd.img-2.6.24-19-generic
lrwxrwxrwx   1 root   root      33 2008-09-02 22:46 initrd.img.old -> boot/initrd.img-2.6.24-16-generic
drwxr-xr-x  16 root   root   12288 2008-09-27 22:11 lib
drwx------   2 root   root   16384 2008-09-02 22:32 lost+found
drwxr-xr-x   5 root   root    4096 2008-10-03 17:18 media
drwxr-xr-x   2 root   root    4096 2008-04-15 06:53 mnt
drwxr-xr-x   3 root   root    4096 2008-09-03 21:51 opt
dr-xr-xr-x 139 root   root       0 2008-10-03 17:18 proc
drwxr-xr-x  16 root   root    4096 2008-10-03 17:06 root
drwxr-xr-x   2 root   root    4096 2008-09-27 22:11 sbin
drwxr-xr-x   2 root   root    4096 2008-04-22 18:48 srv
drwxr-xr-x  12 root   root       0 2008-10-03 17:18 sys
drwxrwxrwt  12 root   root    4096 2008-10-03 17:37 tmp
drwxr-xr-x  11 martin martin  4096 2007-02-07 13:04 usr
drwxr-xr-x  16 root   root    4096 2008-09-18 21:37 var
lrwxrwxrwx   1 root   root      30 2008-09-02 22:39 vmlinuz -> boot/vmlinuz-2.6.24-19-generic
lrwxrwxrwx   1 root   root      30 2008-09-02 22:46 vmlinuz.old -> boot/vmlinuz-2.6.24-16-generic

Martin/

---

### Post by Onewheeler on 2008-10-03
Replying to my own problem, I've just spotted that both / and /usr are owned by martin.martin No idea how this has come about, but they're reset to root.root and all now seems OK.

Martin/

---

