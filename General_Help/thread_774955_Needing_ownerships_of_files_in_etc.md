---
title: "Needing ownerships of files in /etc"
date: 2008-04-29
forum: General Help
---

### Post by Questor21 on 2008-04-29
Don't laugh.  

While in / I accidentally did a:

```
sudo chown -R username:username *
```

:shock:

I stopped it as quickly as I could, but it still got to /boot, /dev, /bin, /etc, and /cdrom.

I tried doing undoing the damage by chowning those back to root:root, but I wasn't surprised when I had problems.  Before everyone left work, I got one of them to send me the directory contents of /dev and with a bit of scripting have restored the correct ownerships of /dev.

I can boot into my desktop again, but when my screen locks I cannot unlock it.  I have read the posts here about 'just passwd yourself' and that does not work.  

I suspect that there are non-root:root objects within /etc.  

**Please just copy/paste the contents of ls -alR /etc, or at least provide me with a list of which files within /etc are non-root:root and what they should be.**

Currently running 8.04.

THANKS.

---

### Post by sujoy on 2008-04-30
well its a long list, but here ya go,

> total 1452
drwxr-xr-x  3 root   root     4096 2008-04-03 08:34 acpi
-rw-r--r--  1 root   root     2975 2008-04-03 08:31 adduser.conf
-rw-r--r--  1 root   root       46 2008-04-30 16:46 adjtime
-rw-r--r--  1 root   root      197 2008-04-03 09:10 aliases
drwxr-xr-x  3 root   root     4096 2008-04-03 08:51 alsa
drwxr-xr-x  2 root   root    12288 2008-04-21 21:41 alternatives
-rw-r--r--  1 root   root      395 2006-10-14 19:09 anacrontab
drwxr-xr-x  6 root   root     4096 2008-04-03 08:51 apm
drwxr-xr-x  4 root   root     4096 2008-04-23 11:25 apt
-rw-r-----  1 root   daemon    144 2006-01-03 12:45 at.deny
drwxr-xr-x  3 root   root     4096 2008-04-03 09:11 avahi
-rw-r--r--  1 root   root     1071 2008-02-10 04:02 bash.bashrc
-rw-r--r--  1 root   root   215618 2008-03-23 04:39 bash_completion
drwxr-xr-x  2 root   root     4096 2008-04-20 04:42 bash_completion.d
-rw-r--r--  1 root   root      332 2008-01-12 23:34 bindresvport.blacklist
drwxr-xr-x  2 root   root     4096 2008-04-03 09:10 bonobo-activation
-rw-r--r--  1 root   root     4867 2008-04-17 04:51 ca-certificates.conf
drwxr-xr-x  2 root   root     4096 2008-04-03 08:31 calendar
drwxr-xr-x  2 root   root     4096 2008-04-03 09:11 canna
drwxr-s---  2 root   dip      4096 2008-04-20 04:42 chatscripts
-rw-r--r--  1 root   root     6485 2006-10-05 21:43 Chinput.ad
drwxr-xr-x  2 root   root     4096 2008-04-20 04:20 compizconfig
-rw-r--r--  1 root   root    55367 2006-07-04 02:28 complete.tcsh
drwxr-xr-x  2 root   root     4096 2008-04-03 08:31 console
drwxr-xr-x  2 root   root     4096 2008-04-03 08:31 console-tools
drwxr-xr-x  2 root   root     4096 2008-04-20 05:32 cron.d
drwxr-xr-x  2 root   root     4096 2008-04-20 05:49 cron.daily
drwxr-xr-x  2 root   root     4096 2008-04-20 05:32 cron.hourly
drwxr-xr-x  2 root   root     4096 2008-04-20 05:32 cron.monthly
-rw-r--r--  1 root   root      724 2008-01-16 00:24 crontab
drwxr-xr-x  2 root   root     4096 2008-04-20 05:49 cron.weekly
drwxr-xr-x  3 root   root     4096 2008-04-03 08:50 csh
-rw-r--r--  1 root   root      428 2006-07-04 02:28 csh.cshrc
-rw-r--r--  1 root   root      275 2006-07-04 02:28 csh.login
-rw-r--r--  1 root   root       67 2006-07-04 02:28 csh.logout
drwxr-xr-x  4 root   lp       4096 2008-04-03 04:44 cups
drwxr-xr-x  5 root   root     4096 2008-04-20 04:42 dbus-1
-rw-r--r--  1 root   root     2969 2008-01-30 06:53 debconf.conf
-rw-r--r--  1 root   root       10 2007-04-01 17:17 debian_version
drwxr-xr-x  3 root   root     4096 2008-04-20 06:21 default
drwxr-xr-x  4 root   root     4096 2008-04-03 09:12 defoma
-rw-r--r--  1 root   root      600 2007-08-31 20:59 deluser.conf
drwxr-xr-x  4 root   root     4096 2008-04-20 05:32 dhcp3
drwxr-xr-x  2 root   root     4096 2008-04-17 05:05 dictionaries-common
-rw-r--r--  1 root   root      630 2007-12-31 21:29 discover.conf
-rw-r--r--  1 root   root      197 2007-12-31 21:29 discover.conf-2.6
drwxr-xr-x  3 root   root     4096 2008-04-03 08:52 discover.d
drwxr-xr-x  2 root   root     4096 2008-01-08 20:16 dm
drwxr-xr-x  3 root   root     4096 2008-04-03 09:32 doc-base
drwxr-xr-x  3 root   root     4096 2008-04-20 04:42 dpkg
drwxr-xr-x  2 root   root     4096 2008-04-21 13:59 elinks
drwxr-xr-x  3 root   root     4096 2008-04-03 08:49 emacs
-rw-r--r--  1 root   root      312 2008-01-30 14:21 email-addresses
drwxr-xr-x  2 root   root     4096 2008-04-03 09:10 esound
drwxr-xr-x  3 root   root     4096 2008-04-03 09:58 exim4
drwxr-xr-x  4 root   root     4096 2008-04-22 05:59 fonts
drwxr-xr-x  3 root   root     4096 2008-04-03 09:12 foomatic
-rw-r--r--  1 root   root     1001 2008-04-17 21:22 fstab
-rw-r--r--  1 root   root      132 2006-10-26 13:43 ftpusers
-rw-r--r--  1 root   root     2349 2008-01-12 23:35 gai.conf
drwxr-xr-x  5 root   root     4096 2008-04-03 08:50 gconf
drwxr-xr-x  7 root   root     4096 2008-04-23 11:14 gdm
drwxr-xr-x  2 root   root     4096 2008-04-03 10:24 gftp
drwxr-xr-x  3 root   root     4096 2008-04-03 08:53 gimp
drwxr-xr-x  3 root   root     4096 2008-04-03 08:51 gnome
drwxr-xr-x  2 root   root     4096 2008-03-25 20:32 gnome-app-install
drwxr-xr-x  3 root   root     4096 2008-04-03 09:11 gnome-vfs-2.0
-rw-r--r--  1 root   root    10852 2007-04-04 14:44 gnome-vfs-mime-magic
drwxr-xr-x  2 root   root     4096 2008-04-03 12:06 gre.d
drwxr-xr-x  2 root   root     4096 2008-04-03 08:31 groff
-rw-r--r--  1 root   root      759 2008-04-21 20:57 group
-rw-------  1 root   root      746 2008-04-21 20:57 group-
drwxr-xr-x  2 root   root     4096 2008-04-17 04:30 grub.d
-rw-r-----  1 root   shadow    619 2008-04-21 20:57 gshadow
-rw-------  1 root   root      609 2008-04-21 20:57 gshadow-
-rw-r--r--  1 root   root      899 2007-09-12 04:58 gssapi_mech.conf
drwxr-xr-x  2 root   root     4096 2008-04-14 23:42 gtk-2.0
drwxr-xr-x  2 root   root     4096 2008-04-03 09:32 gtkmathview
drwxr-xr-x  3 root   root     4096 2008-04-03 08:54 hal
-rw-r--r--  1 root   root     6747 2008-03-03 00:04 hddtemp.db
-rw-r--r--  1 root   root      421 2008-04-03 09:11 hesiod.conf
drwxr-xr-x  3 root   root     4096 2008-04-20 06:23 hibernate
-rw-r--r--  1 root   root        9 2006-08-07 22:44 host.conf
-rw-r--r--  1 root   root        7 2008-04-03 08:29 hostname
-rw-r--r--  1 root   root      297 2008-04-14 23:57 hosts
-rw-r--r--  1 root   root      579 2008-04-03 08:31 hosts.allow
-rw-r--r--  1 root   root      878 2008-04-03 08:31 hosts.deny
drwxr-xr-x  4 root   root     4096 2008-04-20 04:42 iceweasel
-rw-r--r--  1 root   root     1749 2007-08-19 14:03 identd.conf
-rw-------  1 identd root     1024 2008-04-03 09:10 identd.key
-rw-r--r--  1 root   root      145 2008-02-05 03:50 idmapd.conf
drwxr-xr-x  2 root   root     4096 2008-04-03 09:10 imlib
-rw-r--r--  1 root   root     1180 2008-04-21 20:57 inetd.conf
drwxr-xr-x  2 root   root     4096 2008-04-21 21:41 init.d
drwxr-xr-x  5 root   root     4096 2008-04-03 08:33 initramfs-tools
-rw-r--r--  1 root   root     2008 2008-02-02 00:08 inittab
-rw-r--r--  1 root   root     1723 2007-05-25 03:27 inputrc
drwxr-xr-x  2 root   root     4096 2008-04-03 09:11 iproute2
-rw-r--r--  1 root   root       34 2007-11-19 23:51 issue
-rw-r--r--  1 root   root       27 2007-11-19 23:51 issue.net
drwxr-xr-x  3 root   root     4096 2008-04-03 08:51 java
drwxr-xr-x  4 root   root     4096 2008-04-20 04:20 kde3
-rw-r--r--  1 root   root      240 2008-04-03 09:19 kernel-img.conf
drwxr-xr-x  2 root   root     4096 2008-04-03 08:31 ldap
-rw-r--r--  1 root   root    73498 2008-04-22 06:16 ld.so.cache
-rw-r--r--  1 root   root       34 2008-04-03 08:30 ld.so.conf
drwxr-xr-x  2 root   root     4096 2008-04-03 08:30 ld.so.conf.d
-rw-r--r--  1 root   root       20 2008-02-09 05:04 libao.conf
drwxr-xr-x  2 root   root     4096 2008-04-03 09:11 libgda
drwxr-xr-x  2 root   root     4096 2007-09-28 22:14 libpaper.d
-rw-r--r--  1 root   root     2586 2008-01-12 22:56 locale.alias
-rw-r--r--  1 root   root     8249 2008-04-03 08:31 locale.gen
lrwxrwxrwx  1 root   root       32 2008-04-22 07:16 localtime -> /usr/share/zoneinfo/Asia/Kolkata
drwxr-xr-x  3 root   root     4096 2008-04-16 20:31 logcheck
-rw-r--r--  1 root   root     9681 2008-01-13 23:44 login.defs
-rw-r--r--  1 root   root      599 2005-09-03 18:19 logrotate.conf
drwxr-xr-x  2 root   root     4096 2008-04-20 06:23 logrotate.d
drwxr-xr-x  2 root   root     4096 2007-07-25 19:27 lsb-base
-rw-r--r--  1 root   root      111 2008-02-11 01:37 magic
-rw-r--r--  1 root   root      111 2008-02-11 01:37 magic.mime
-rw-r--r--  1 root   root    21992 2008-04-22 05:49 mailcap
-rw-r--r--  1 root   root      449 2006-12-05 08:52 mailcap.order
-rw-r--r--  1 root   root       17 2008-04-03 09:58 mailname
-rw-r--r--  1 root   root      125 2008-01-09 04:04 mail.rc
-rw-r--r--  1 root   root     4624 2008-01-29 05:09 manpath.config
drwxr-xr-x  2 root   root     4096 2008-04-20 05:49 menu
drwxr-xr-x  2 root   root     4096 2008-04-20 05:49 menu-methods
-rw-r--r--  1 root   root    21014 2008-02-22 18:56 mime.types
-rw-r--r--  1 root   root      417 2008-02-10 10:57 mke2fs.conf
drwxr-xr-x  2 root   root     4096 2008-04-03 09:11 mlterm
drwxr-xr-x  3 root   root     4096 2008-04-21 20:57 modprobe.d
-rw-r--r--  1 root   root      200 2008-04-03 08:31 modules
drwxr-xr-x  4 root   root     4096 2008-04-21 21:41 mono
lrwxrwxrwx  1 root   root       13 2008-04-03 08:30 motd -> /var/run/motd
-rw-r--r--  1 root   root      286 2008-04-03 08:30 motd.tail
-rw-r-----  1 mpd    audio    8053 2008-04-03 13:05 mpd.conf
drwxr-xr-x  2 root   root     4096 2008-04-16 19:37 mplayer
-rw-r--r--  1 root   root     1104 2008-04-30 15:28 mtab
-rw-r--r--  1 root   root      624 2007-08-08 16:44 mtools.conf
-rw-r--r--  1 root   root     4450 2008-01-15 04:55 Muttrc
drwxr-xr-x  2 root   root     4096 2008-04-03 09:10 Muttrc.d
drwxr-xr-x  3 root   root     4096 2008-04-19 02:52 mysql
-rw-r--r--  1 root   root     7672 2007-12-24 20:11 nanorc
-rw-r--r--  1 root   root     2064 2006-11-24 01:03 netscsid.conf
drwxr-xr-x  7 root   root     4096 2008-04-03 08:31 network
drwxr-xr-x  3 root   root     4096 2008-04-03 08:56 NetworkManager
-rw-r--r--  1 root   root       80 2008-04-03 08:29 networks
-rw-r--r--  1 root   root      513 2008-04-03 09:14 nsswitch.conf
-rw-r--r--  1 root   root       60 2007-11-30 22:06 openalrc
drwxr-xr-x  2 root   root     4096 2008-04-20 04:22 openoffice
drwxr-xr-x  2 root   root     4096 2008-04-03 08:30 opt
-rw-r--r--  1 root   root      552 2007-08-27 07:46 pam.conf
drwxr-xr-x  2 root   root     4096 2008-04-20 06:06 pam.d
drwxr-xr-x  2 root   root     4096 2008-04-03 09:12 pango
-rw-r--r--  1 root   root        3 2008-04-03 08:58 papersize
-rw-r--r--  1 root   root     1325 2008-04-21 20:57 passwd
-rw-------  1 root   root     1325 2008-04-21 20:57 passwd-
drwxr-xr-x  2 root   root     4096 2008-04-20 05:49 pekwm
drwxr-xr-x  4 root   root     4096 2008-04-03 08:49 perl
drwxr-xr-x  5 root   root     4096 2008-04-03 08:54 pm
-rw-r--r--  1 root   root      343 2008-04-03 08:35 popularity-contest.conf
drwxr-xr-x  7 root   root     4096 2008-04-20 11:04 ppp
-rw-r--r--  1 root   root      475 2006-10-28 19:12 profile
-rw-r--r--  1 root   root     2510 2007-07-29 04:36 protocols
drwxr-xr-x  2 root   root     4096 2008-04-03 09:32 psiconv
drwxr-xr-x  2 root   root     4096 2008-04-03 12:48 pulse
drwxr-xr-x  2 root   root     4096 2008-04-17 04:38 purple
drwxr-xr-x  2 root   root     4096 2008-04-03 08:49 python
drwxr-xr-x  2 root   root     4096 2008-04-20 04:42 python2.4
drwxr-xr-x  2 root   root     4096 2008-04-20 04:19 python2.5
drwxr-xr-x  2 root   root     4096 2008-04-20 06:06 rc0.d
drwxr-xr-x  2 root   root     4096 2008-04-20 06:06 rc1.d
drwxr-xr-x  2 root   root     4096 2008-04-21 21:41 rc2.d
drwxr-xr-x  2 root   root     4096 2008-04-21 21:41 rc3.d
drwxr-xr-x  2 root   root     4096 2008-04-21 21:41 rc4.d
drwxr-xr-x  2 root   root     4096 2008-04-21 21:41 rc5.d
drwxr-xr-x  2 root   root     4096 2008-04-20 06:06 rc6.d
-rwxr-xr-x  1 root   root      306 2008-04-03 08:30 rc.local
drwxr-xr-x  2 root   root     4096 2008-04-20 06:06 rcS.d
-rw-r--r--  1 root   root     2625 2008-04-04 02:59 reportbug.conf
drwxr-xr-x  3 root   root     4096 2008-04-03 08:51 resolvconf
-rw-r--r--  1 root   root       69 2008-04-20 11:04 resolv.conf
-rwxr-xr-x  1 root   root      268 2007-10-22 00:07 rmt
-rw-r--r--  1 root   root      887 2007-07-29 04:36 rpc
drwxr-xr-x  3 root   root     4096 2008-04-21 20:57 sane.d
drwxr-xr-x  2 root   root     4096 2008-04-03 09:15 scim
-rw-r--r--  1 root   root     3663 2007-09-27 03:27 screenrc
-rw-r--r--  1 root   root       23 2007-12-18 19:32 scrollkeeper.conf
-rw-r--r--  1 root   root      666 2007-08-06 09:42 scsi_id.config
-rw-r--r--  1 root   root     1254 2008-04-03 05:27 securetty
drwxr-xr-x  2 root   root     4096 2008-04-03 08:30 security
drwxr-xr-x  3 root   root     4096 2008-04-20 06:06 selinux
-rw-r--r--  1 root   root    85602 2008-01-03 13:00 sensors.conf
-rw-r--r--  1 root   root    18274 2007-07-29 04:36 services
-rw-r--r--  1 root   root      216 2007-05-07 11:46 sestatus.conf
drwxr-xr-x  3 root   root     4096 2008-04-17 05:01 sgml
-rw-r-----  1 root   shadow    877 2008-04-21 20:57 shadow
-rw-------  1 root   root      877 2008-04-21 20:57 shadow-
-rw-r--r--  1 root   root      171 2008-04-03 12:33 shells
drwxr-xr-x  2 root   root     4096 2008-04-03 08:30 skel
drwxr-xr-x  3 root   root     4096 2008-04-03 08:50 sound
drwxr-xr-x  2 root   root     4096 2008-04-20 04:42 ssh
drwxr-xr-x  4 root   root     4096 2008-04-20 04:42 ssl
-r--r-----  1 root   root      548 2008-04-18 23:22 sudoers
-rw-r--r--  1 root   root     1924 2008-02-01 17:32 sysctl.conf
-rw-r--r--  1 root   root     1614 2008-01-08 14:22 syslog.conf
drwxr-xr-x  2 root   root     4096 2008-04-03 08:30 terminfo
drwxr-xr-x  3 root   root     4096 2008-04-03 08:50 texmf
-rw-r--r--  1 root   root      165 2008-01-17 10:06 tidy.conf
-rw-r--r--  1 root   root       13 2008-04-22 07:16 timezone
-rw-r--r--  1 root   root      645 2008-02-04 00:37 ts.conf
-rw-r--r--  1 root   root     1260 2007-11-30 15:04 ucf.conf
drwxr-xr-x  4 root   root     4096 2008-04-20 04:42 udev
drwxr-xr-x  2 root   root     4096 2008-04-03 09:11 uim
-rw-r--r--  1 root   root      203 2007-11-25 21:06 updatedb.conf
drwxr-xr-x  2 root   root     4096 2007-09-05 06:20 update-notifier
drwxr-xr-x  4 root   root     4096 2008-04-03 09:31 usbmount
-rw-r--r--  1 root   root      204 2008-04-03 09:12 uswsusp.conf
drwxr-xr-x  2 root   root     4096 2008-04-03 09:11 vga
drwxr-xr-x  2 root   root     4096 2008-04-20 05:49 vim
-rw-r--r--  1 root   root     5069 2008-04-03 11:20 vsftpd.conf
drwxr-xr-x  2 root   root     4096 2008-04-03 09:10 w3m
-rw-r--r--  1 root   root     4221 2007-06-16 19:53 wgetrc
-rw-r--r--  1 root   root     1343 2007-01-10 00:09 wodim.conf
drwxr-xr-x  2 root   root     4096 2008-04-20 06:06 wpa_supplicant
drwxr-xr-x 10 root   root     4096 2008-04-23 11:38 X11
drwxr-xr-x  5 root   root     4096 2008-04-16 11:17 xdg
drwxr-xr-x  2 root   root     4096 2008-04-03 09:15 xml


---

