---
title: "/etc permissions stuffed"
date: 2008-06-30
forum: General Help
---

### Post by 4t0m1c_w07f on 2008-06-30
Hi
I stuffed up all the permissions int the /etc folder and now I cant boot on my hard drive so I am currently on a live cd and individually changing the permissions. Please can anyone suggest an easier way other than re-installing. I have noticed that almost all the files are read-write--read-only--read-only and there are of coarse the executables.

---

### Post by mempman on 2008-06-30
> **4t0m1c_w07f said:**
> Hi
I stuffed up all the permissions int the /etc folder and now I cant boot on my hard drive so I am currently on a live cd and individually changing the permissions. Please can anyone suggest an easier way other than re-installing. I have noticed that almost all the files are read-write--read-only--read-only and there are of coarse the executables.
If you don't know exactly what you have done, I would seriously recommend reinstalling ubuntu....maybe next time, keep a seperate /home folder so that after reinstalls you aren't spending countless hours reconfiguring your desired software exactly so.

Another reason I would recommend reinstalling ubuntu from scratch is that maybe later on something that you have messedup now /etc, will come to be a pain.  And that time you will be spending numerous hours trying to solve problems, and it will be a real pain.  Trust me.

---

### Post by eryksun on 2008-06-30
> **4t0m1c_w07f said:**
> Hi
I stuffed up all the permissions int the /etc folder and now I cant boot on my hard drive so I am currently on a live cd and individually changing the permissions. Please can anyone suggest an easier way other than re-installing. I have noticed that almost all the files are read-write--read-only--read-only and there are of coarse the executables.

Wow, that's a nightmare. :( Personally I would just save my data and reinstall. That being said, the 'find' command might help you. Run these commands on the /etc of your live CD. Then edit the resulting files for sanity and [sudo] execute the scripts on your 'stuffed' /etc.

For the permissions:

```
find /etc -fprintf ~/perms.sh 'chmod %m %h/%f\n'
```

Owner/group (not all the files in /etc are root:root):

```
find /etc -fprintf ~/owner.sh 'chown %u:%g %h/%f\n'
```

You can also use 'diff' to compare a listing of your original /etc vs the one on the live CD and find the files in your setup that aren't on the live CD. Then, if the list isn't too long, you can ask someone on here what the permissions should be.

---

### Post by smo0th on 2008-06-30
how did you screwed up?

what did you typed to stuff up your permissions? what the permissions look like now?

hold on a sec before reinstalling, type the ```
ls -l /etc
``` output and let's see what you did.

---

### Post by 4t0m1c_w07f on 2008-06-30
Thanks... I have spent hours configuring this system to be perfect... Is there anyway to only re-install the system files and keep all my home data?

---

### Post by 4t0m1c_w07f on 2008-06-30
Well I kinda changed the permissions of the whole /etc folder... I have slowly reduced the boot errors to only problems with the xsession script, getwuid_r, /etc/pango/pangorc and font config

---

### Post by 4t0m1c_w07f on 2008-06-30
```
ubuntu@ubuntu:~$ sudo ls -l /media/disk/etc
total 1336
drwxr-xr-x  8 root root      4096 2008-04-22 18:01 acpi
-rw-r--r--  1 root root      2975 2008-04-22 17:49 adduser.conf
-rw-r--r--  1 root root        44 2008-06-30 07:47 adjtime
-rw-r--r--  1 root root        49 2008-06-24 07:44 aliases
drwxr-xr-x  2 root root     20480 2008-06-28 10:15 alternatives
-rw-r--r--  1 root root       395 2007-03-05 06:38 anacrontab
drwxr-xr-x  7 root root      4096 2008-06-28 10:14 apache2
drwxr-xr-x  7 root root      4096 2008-04-22 18:01 apm
drwxr-xr-x  2 root root      4096 2008-06-24 08:51 apparmor
drwxr-xr-x  6 root root      4096 2008-04-22 17:52 apparmor.d
drwxr-xr-x  3 root root      4096 2008-06-24 08:52 apport
drwxr-xr-x  4 root root      4096 2008-06-27 06:51 apt
-rw-r--r--  1 root daemon     144 2007-02-20 13:41 at.deny
drwxr-xr-x  3 root root      4096 2008-04-22 18:06 avahi
-rw-r--r--  1 root root      1733 2008-04-15 03:36 bash.bashrc
-rw-r--r--  1 root root    216529 2008-04-15 01:45 bash_completion
drwxr-xr-x  2 root root      4096 2008-06-28 10:14 bash_completion.d
drwxr-xr-x  2 root root      4096 2008-04-22 17:49 belocs
-rw-r--r--  1 root root       332 2008-04-04 22:16 bindresvport.blacklist
-rw-r--r--  1 root root       309 2008-06-24 08:51 blkid.tab
-rw-r--r--  1 root root       309 2008-06-24 07:45 blkid.tab.old
drwxr-xr-x  2 root root      4096 2008-04-22 18:06 bluetooth
-rw-r--r--  1 root root      6813 2008-02-24 20:22 bogofilter.cf
drwxr-xr-x  2 root root      4096 2008-04-22 17:59 bonobo-activation
-rw-r--r--  1 root root        33 2008-04-22 18:05 brlapi.key
drwxr-xr-x  2 root root      4096 2008-04-22 18:05 brltty
-rw-r--r--  1 root root     15721 2008-03-27 23:25 brltty.conf
-rw-r--r--  1 root root      4867 2008-04-22 18:02 ca-certificates.conf
drwxr-xr-x  2 root root      4096 2008-04-22 18:00 calendar
-rw-r--r--  1 root root         0 2008-06-12 14:21 cedega.conf
drwxr-s---  2 root dip       4096 2008-04-22 18:01 chatscripts
-rw-r--r--  1 root root      3694 2007-11-18 14:29 checkinstallrc
drwxr-xr-x  2 root root      4096 2008-04-22 18:02 compizconfig
drwxr-xr-x  3 root root      4096 2008-04-22 17:51 ConsoleKit
drwxr-xr-x  2 root root      4096 2008-04-22 17:49 console-setup
drwxr-xr-x  2 root root      4096 2008-04-22 17:49 console-tools
drwxr-xr-x  2 root root      4096 2008-06-28 10:14 cron.d
drwxr-xr-x  2 root root      4096 2008-06-28 10:14 cron.daily
drwxr-xr-x  2 root root      4096 2008-04-22 18:01 cron.hourly
drwxr-xr-x  2 root root      4096 2008-04-22 18:01 cron.monthly
-rw-r--r--  1 root root       724 2008-04-08 18:02 crontab
drwxr-xr-x  2 root root      4096 2008-04-22 18:01 cron.weekly
drwxr-xr-x  4 root lp        4096 2008-04-22 17:54 cups
drwxr-xr-x  5 root root      4096 2008-06-24 08:52 dbus-1
-rw-r--r--  1 root root      2969 2008-03-11 15:51 debconf.conf
-rw-r--r--  1 root root        10 2007-10-20 11:51 debian_version
drwxr-xr-x  2 root root      4096 2008-06-28 10:14 default
drwxr-xr-x  4 root root      4096 2008-04-22 17:58 defoma
-rw-r--r--  1 root root       600 2007-10-23 15:01 deluser.conf
drwxr-xr-x  2 root root      4096 2008-04-22 17:49 depmod.d
drwxr-xr-x  4 root root      4096 2008-04-22 17:54 devfs
drwxr-xr-x  4 root root      4096 2008-04-22 17:49 dhcp3
drwxr-xr-x  2 root root      4096 2008-04-22 18:11 dictionaries-common
drwxr-xr-x  2 root root      4096 2008-04-21 15:50 dm
drwxr-xr-x  3 root root      4096 2008-04-22 17:53 doc-base
drwxr-xr-x  3 root root      4096 2008-06-24 13:13 dpkg
-rw-r--r--  1 root root        34 2008-02-19 04:33 e2fsck.conf
drwxr-xr-x  3 root root      4096 2008-04-22 17:51 emacs
-rw-r--r--  1 root root        79 2008-04-22 17:49 environment
drwxr-xr-x  2 root root      4096 2008-04-22 17:59 esound
drwxr-xr-x  2 root root      4096 2008-04-22 17:49 event.d
-rw-r--r--  1 root root       354 2007-03-05 06:54 fdmount.conf
drwxr-xr-x  4 root root      4096 2008-04-22 17:53 firefox-3.0
drwxr-xr-x  4 root root      4096 2008-04-22 17:51 fonts
drwxr-xr-x  3 root root      4096 2008-04-22 17:54 foomatic
-rw-r--r--  1 root root       480 2008-04-22 17:48 fstab
-rw-r--r--  1 root fuse       216 2008-02-26 18:25 fuse.conf
-rw-r--r--  1 root root      2689 2008-04-04 22:16 gai.conf
drwxr-xr-x  2 root root      4096 2008-04-22 18:05 gamin
drwxr-xr-x  6 root root      4096 2008-04-22 17:51 gconf
drwxr-xr-x  7 root root      4096 2008-06-27 07:20 gdm
drwxr-xr-x  3 root root      4096 2008-04-22 17:53 gimp
drwxr-xr-x  3 root root      4096 2008-06-24 08:51 gnome
drwxr-xr-x  2 root root      4096 2008-06-24 08:52 gnome-app-install
drwxr-xr-x  3 root root      4096 2008-04-22 17:53 gnome-system-tools
drwxr-xr-x  4 root root      4096 2008-04-22 17:51 gnome-vfs-2.0
-rw-r--r--  1 root root     10852 2007-04-28 02:27 gnome-vfs-mime-magic
drwxr-xr-x  2 root root      4096 2008-06-24 08:53 gre.d
drwxr-xr-x  2 root root      4096 2008-04-22 18:00 groff
-rw-r--r--  1 root root       920 2008-06-26 08:18 group
-rw-r--r--  1 root root       912 2008-06-26 08:18 group-
drwxr-xr-x  2 root root      4096 2008-04-22 18:01 grub.d
-rw-r--r--  1 root shadow     766 2008-06-26 08:18 gshadow
-rw-r--r--  1 root root       758 2008-06-26 08:18 gshadow-
drwxr-xr-x  2 root root      4096 2008-06-25 10:33 gtk
drwxr-xr-x  2 root root      4096 2008-06-24 08:50 gtk-2.0
drwxr-xr-x  3 root root      4096 2008-04-22 17:53 hal
-rw-r--r--  1 root root      4793 2008-03-28 22:26 hdparm.conf
-rw-r--r--  1 root root       425 2008-04-22 18:03 hesiod.conf
-rw-r--r--  1 root root        92 2007-10-20 11:51 host.conf
-rw-r--r--  1 root root         7 2008-06-24 07:44 hostname
-rw-r--r--  1 root root       242 2008-06-24 07:44 hosts
-rw-r--r--  1 root root       579 2008-04-22 17:49 hosts.allow
-rw-r--r--  1 root root       878 2008-04-22 17:49 hosts.deny
drwxr-xr-x  2 root root      4096 2008-04-22 17:59 hp
drwxr-xr-x  2 root root      4096 2008-04-22 18:03 hwtest.d
-rw-r--r--  1 root root         0 2008-06-27 06:54 inetd.conf
drwxr-xr-x  2 root root      4096 2008-06-28 10:14 init.d
drwxr-xr-x  5 root root      4096 2008-06-24 08:51 initramfs-tools
-rw-r--r--  1 root root      1723 2007-10-02 14:35 inputrc
drwxr-xr-x  2 root root      4096 2008-04-22 17:49 iproute2
-rw-r--r--  1 root root        19 2008-04-15 05:53 issue
-rw-r--r--  1 root root        12 2008-04-15 05:53 issue.net
drwxr-xr-x  3 root root      4096 2008-06-27 13:30 java
drwxr-xr-x  3 root root      4096 2008-06-28 10:15 java-1.5.0-sun
drwxr-xr-x  5 root root      4096 2008-06-28 10:15 java-6-openjdk
drwxr-xr-x  4 root root      4096 2008-06-28 10:14 java-6-sun
-rw-r--r--  1 root root       294 2006-05-08 10:56 jvm
drwxr-xr-x  2 root root      4096 2008-04-01 14:45 jvm.d
-rw-r--r--  1 root root       167 2008-06-24 07:45 kernel-img.conf
drwxr-xr-x 10 root root      4096 2008-04-22 18:01 laptop-mode
drwxr-xr-x  2 root root      4096 2008-06-24 08:51 ldap
-rw-r--r--  1 root root     52885 2008-06-28 10:15 ld.so.cache
-rw-r--r--  1 root root        57 2008-06-26 14:31 ld.so.conf
-rw-r--r--  1 root root        57 2008-06-26 13:30 ld.so.conf~
drwxr-xr-x  2 root root      4096 2008-04-22 17:49 ld.so.conf.d
-rw-r--r--  1 root root      3578 2007-11-15 16:03 lftp.conf
-rw-r--r--  1 root root        20 2007-10-24 03:09 libao.conf
drwxr-xr-x  2 root root      4096 2007-11-14 11:01 libpaper.d
-rw-r--r--  1 root root      2586 2008-03-11 11:02 locale.alias
-rw-r--r--  1 root root       245 2008-06-24 08:45 localtime
drwxr-xr-x  5 root root      4096 2008-04-22 17:52 logcheck
-rw-r--r--  1 root root      9676 2008-06-24 11:13 login.defs
-rw-r--r--  1 root root       599 2006-06-19 18:21 logrotate.conf
drwxr-xr-x  2 root root      4096 2008-06-28 10:14 logrotate.d
drwxr-xr-x  2 root root      4096 2008-03-26 18:23 lsb-base
-rw-r--r--  1 root root      3820 2008-03-10 19:00 lsb-base-logging.sh
-rw-r--r--  1 root root        96 2008-04-15 05:04 lsb-release
-rw-r--r--  1 root root     13144 2007-11-16 12:04 ltrace.conf
-rw-r--r--  1 root root       111 2007-10-23 23:03 magic
-rw-r--r--  1 root root       111 2007-10-23 23:03 magic.mime
-rw-r--r--  1 root root     17843 2008-06-28 10:15 mailcap
-rw-r--r--  1 root root       449 2008-04-01 18:11 mailcap.order
-rw-r--r--  1 root root      4624 2008-03-12 13:24 manpath.config
-rw-r--r--  1 root root     11742 2007-03-05 06:54 mediaprm
drwxr-xr-x  2 root root      4096 2008-06-24 08:51 menu-methods
-rw-r--r--  1 root root     20891 2008-04-01 18:11 mime.types
-rw-r--r--  1 root root       417 2008-03-27 17:25 mke2fs.conf
drwxr-xr-x  3 root root      4096 2008-06-24 08:54 modprobe.d
-rw-r--r--  1 root root       203 2008-06-24 07:45 modules
drwxr-xr-x  2 root root      4096 2008-04-22 18:03 modutils
drwxr-xr-x  4 root root      4096 2008-04-22 18:02 mono
lrwxrwxrwx  1 root root        13 2008-06-24 07:37 motd -> /var/run/motd
-rw-r--r--  1 root root       346 2008-04-22 17:49 motd.tail
-rw-r--r--  1 root root       490 2008-06-30 07:47 mtab
-rw-r--r--  1 root root      7672 2008-04-08 14:02 nanorc
-rw-r--r--  1 root root      2064 2006-11-23 19:33 netscsid.conf
drwxr-xr-x  6 root root      4096 2008-04-22 17:49 network
drwxr-xr-x  3 root root      4096 2008-04-22 17:54 NetworkManager
-rw-r--r--  1 root root        91 2007-05-15 16:07 networks
-rw-r--r--  1 root root       513 2008-04-22 18:08 nsswitch.conf
drwxr-xr-x  2 root root      4096 2008-04-03 12:12 ODBCDataSources
-rw-r--r--  1 root root         0 2008-04-03 12:12 odbc.ini
-rw-r--r--  1 root root         0 2008-04-03 12:12 odbcinst.ini
-rw-r--r--  1 root root        60 2007-12-03 23:31 openalrc
drwxr-xr-x  2 root root      4096 2008-06-24 08:54 openoffice
drwxr-xr-x  2 root root      4096 2008-04-22 17:48 opt
-rw-r--r--  1 root root        64 2008-06-26 09:14 outkafe.cfg
-rw-r--r--  1 root root       552 2008-04-09 20:22 pam.conf
drwxr-xr-x  2 root root      4096 2008-06-27 06:54 pam.d
drwxr-xr-x  2 root root      4096 2008-04-22 17:58 pango
-rw-r--r--  1 root root         3 2008-06-24 07:45 papersize
-rw-r--r--  1 root root      1525 2008-06-26 08:18 passwd
-rw-r--r--  1 root root      1498 2008-06-26 08:18 passwd-
drwxr-xr-x  2 root root      4096 2008-04-22 17:49 pcmcia
drwxr-xr-x  4 root root      4096 2008-04-22 17:50 perl
drwxr-xr-x  4 root root      4096 2008-06-28 10:14 php5
drwxr-xr-x  5 root root      4096 2008-04-22 17:53 pm
-rw-r--r--  1 root root      7649 2008-04-22 18:03 pnm2ppa.conf
drwxr-xr-x  2 root root      4096 2008-04-22 18:07 PolicyKit
-rw-r--r--  1 root root       342 2008-06-24 07:45 popularity-contest.conf
drwxr-xr-x  3 root root      4096 2008-06-26 08:18 postgresql
drwxr-xr-x  3 root root      4096 2008-06-26 08:18 postgresql-common
drwxr-xr-x  4 root root      4096 2008-04-22 17:52 power
drwxr-xr-x  8 root dip       4096 2008-04-22 18:01 ppp
-rw-r--r--  1 root root       497 2008-04-22 17:49 profile
drwxr-xr-x  2 root root      4096 2008-04-15 05:53 profile.d
-rw-r--r--  1 root root      2510 2007-12-03 22:04 protocols
drwxr-xr-x  2 root root      4096 2008-04-22 18:03 pulse
drwxr-xr-x  2 root root      4096 2008-04-22 18:03 purple
drwxr-xr-x  2 root root      4096 2008-04-22 17:49 python
drwxr-xr-x  2 root root      4096 2008-04-22 17:49 python2.5
-rw-r--r--  1 root root      1018 2007-11-28 01:04 rarfiles.lst
drwxr-xr-x  2 root root      4096 2008-06-28 10:14 rc0.d
drwxr-xr-x  2 root root      4096 2008-06-28 10:14 rc1.d
drwxr-xr-x  2 root root      4096 2008-06-28 10:14 rc2.d
drwxr-xr-x  2 root root      4096 2008-06-28 10:14 rc3.d
drwxr-xr-x  2 root root      4096 2008-06-28 10:14 rc4.d
drwxr-xr-x  2 root root      4096 2008-06-28 10:14 rc5.d
drwxr-xr-x  2 root root      4096 2008-06-28 10:14 rc6.d
-rwxr-xr-x  1 root root       306 2008-04-22 17:49 rc.local
drwxr-xr-x  2 root root      4096 2008-06-24 08:45 rcS.d
drwxr-xr-x  2 root root      4096 2008-04-22 18:03 readahead
drwxr-xr-x  3 root root      4096 2008-04-22 17:53 resolvconf
-rw-r--r--  1 root root       169 2008-06-28 10:54 resolv.conf
-rwxr-xr-x  1 root root       268 2008-04-04 11:07 rmt
-rw-r--r--  1 root root       887 2007-12-03 22:04 rpc
drwxr-xr-x  2 root root      4096 2008-06-28 10:54 samba
drwxr-xr-x  3 root root      4096 2008-04-22 17:59 sane.d
drwxr-xr-x  2 root root      4096 2008-04-22 18:05 scim
-rw-r--r--  1 root root      3663 2007-10-23 16:02 screenrc
-rw-r--r--  1 root root        23 2007-12-06 13:20 scrollkeeper.conf
-rw-r--r--  1 root root      1024 2008-04-03 01:08 securetty
drwxr-xr-x  2 root root      4096 2008-06-24 08:47 security
-rw-r--r--  1 root root     18274 2007-12-03 22:04 services
drwxr-xr-x  3 root root      4096 2008-04-22 17:59 sgml
-rw-r--r--  1 root shadow     909 2008-06-26 08:18 shadow
-rw-r--r--  1 root root       909 2008-06-26 08:18 shadow-
-rw-r--r--  1 root root       192 2008-06-26 07:59 shells
drwxr-xr-x  2 root root      4096 2008-06-26 07:59 skel
drwxr-xr-x  3 root root      4096 2008-04-22 17:51 sound
drwxr-xr-x  2 root root      4096 2008-06-24 08:51 ssh
drwxr-xr-x  4 root root      4096 2008-06-27 06:54 ssl
-rw-r--r--  1 root root       470 2008-06-24 07:44 sudoers
-rw-r--r--  1 root root      2405 2008-03-13 22:24 sysctl.conf
-rw-r--r--  1 root root      1614 2007-11-23 09:06 syslog.conf
drwxr-xr-x  2 root root      4096 2008-04-22 17:49 terminfo
-rw-r--r--  1 root root        20 2008-06-24 08:45 timezone
-rw-r--r--  1 root root      1260 2008-02-21 07:22 ucf.conf
drwxr-xr-x  3 root root      4096 2008-04-22 17:49 udev
drwxr-xr-x  2 root root      4096 2008-06-24 08:52 ufw
-rw-r--r--  1 root root       142 2008-01-24 16:51 uniconf.conf
-rw-r--r--  1 root root       214 2008-03-08 18:22 updatedb.conf
drwxr-xr-x  2 root root      4096 2008-06-24 08:52 update-manager
drwxr-xr-x  2 root root      4096 2008-04-04 21:34 update-notifier
-rw-r--r--  1 root root       117 2008-06-24 07:45 usplash.conf
drwxr-xr-x  2 root root      4096 2008-04-22 17:49 vim
drwxr-xr-x  2 root root      4096 2008-04-22 18:01 w3m
-rw-r--r--  1 root root      4221 2007-06-18 09:45 wgetrc
-rw-r--r--  1 root root      1343 2007-01-09 18:39 wodim.conf
drwxr-xr-x  2 root root      4096 2008-04-22 17:49 wpa_supplicant
-rw-r--r--  1 root dialout     66 2008-04-22 18:05 wvdial.conf
drwxr-xr-x 10 root root      4096 2008-04-22 18:12 X11
drwxr-xr-x  5 root root      4096 2008-04-22 18:05 xdg
drwxr-xr-x  2 root root      4096 2008-04-22 17:54 xml
drwxr-xr-x  2 root root      4096 2008-06-24 08:53 xulrunner-1.9
-rw-r--r--  1 root root       461 2008-04-03 19:33 zsh_command_not_found

```

---

### Post by eryksun on 2008-06-30
> **4t0m1c_w07f said:**
> Thanks... I have spent hours configuring this system to be perfect... Is there anyway to only re-install the system files and keep all my home data?

I've never been in your shoes, so take this with a grain of salt. I assume your /home is on the boot partition, in which case reinstalling would overwrite /home. But wouldn't tar work to make a backup of /home to a thumb drive or USB HD that you can restore on a fresh install?

---

### Post by 4t0m1c_w07f on 2008-06-30
> **eryksun said:**
> I've never been in your shoes, so take this with a grain of salt. I assume your /home is on the boot partition, in which case reinstalling would overwrite /home. But wouldn't tar work to make a backup of /home to a thumb drive or USB HD that you can restore on a fresh install?

Well yeah I could do that

---

### Post by mempman on 2008-06-30
> **4t0m1c_w07f said:**
> Well yeah I could do that

Check this out: [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)


It basically talks about how to move your /home to a separate partition if you installed /home in the same partition as /.

---

### Post by 4t0m1c_w07f on 2008-06-30
> **mempman said:**
> Check this out: [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)


It basically talks about how to move your /home to a separate partition if you installed /home in the same partition as /.

Well back-up is easy but can I do a back-up of my packages?

Off the liveCD

---

### Post by eryksun on 2008-06-30
> **4t0m1c_w07f said:**
> Well back-up is easy but can I do a back-up of my packages?

Off the liveCD

Maybe you could try restoring the contents of 

```
/etc/apt  [correct permissions]
/var/cache/apt
/var/lib/apt
/var/lib/aptitude
/var/lib/dpkg
```

Then enable the CD repository (if some packages aren't in /var/cache/apt/archives for some reason), and do a reinstall of all installed packages with Synaptic or apt-get? I have no idea if this will work. But it's worth a shot on a fresh install.

---

### Post by smo0th on 2008-06-30
your listing looks very normal, however I agree that it's painless if you backup your data and reinstall the system from the live CD, it just depends on your patience and how bad you want to recover everything by hand :S good luck man.

---

### Post by 4t0m1c_w07f on 2008-07-01
> **smo0th said:**
> your listing looks very normal, however I agree that it's painless if you backup your data and reinstall the system from the live CD, it just depends on your patience and how bad you want to recover everything by hand :S good luck man.

Re-installed my system and no harm done except some lost time but thanks...

---

