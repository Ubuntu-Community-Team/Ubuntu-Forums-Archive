---
title: "[SOLVED] Fresh install, old home partition"
date: 2007-12-31
forum: General Help
---

### Post by ~LoKe on 2007-12-31
Well, I've re-installed Gutsy and went from 32bit to 64bit, and I'm left with one problem.  The GTK theme I was using previously is all blocky now, ugly as sin.  I've installed all the engines, as far as I know, and even tried downloading it and installing it again.  No luck.

So...I'm wondering if there's a file in my home directory that I should have removed before re-installing?  Here's the list:
```

drwx------   3 loke loke     4096 2007-10-02 16:13 .adobe
-rw-r--r--   1 loke loke      585 2007-04-05 21:29 .apport-ignore.xml
drwx------   2 loke loke     4096 2007-12-31 02:36 .aptitude
-rwxrwxr-x   1 loke loke    43416 2007-12-31 18:29 .bash_history
-rwxrwxr-x   1 loke loke      220 2006-11-29 17:13 .bash_logout
-rwxrwxr-x   1 loke loke      414 2006-11-29 17:13 .bash_profile
-rwxrwxr-x   1 loke loke     4906 2007-12-10 14:51 .bashrc
drwxr-xr-x   6 loke loke     4096 2007-09-09 22:27 .cache
drwxr-xr-x   5 loke loke     4096 2007-10-22 17:38 .cddb
drwxrwxr-x  17 loke loke     4096 2007-12-22 18:12 .config
-rw-------   1 loke loke      197 2006-12-12 19:17 .cvspass
drwx------   3 loke loke     4096 2007-03-17 12:46 .dbus
drwx------   2 loke loke     4096 2007-12-12 20:27 .dbus-keyrings
-rw-------   1 loke loke       28 2007-12-31 02:11 .dmrc
drwxr-xr-x  10 loke loke     4096 2007-12-30 22:28 .dvdcss
drwxr-xr-x   2 loke loke     4096 2007-08-05 18:00 .dvdrip
-rw-r--r--   1 loke loke    25778 2007-01-14 13:39 .dvdriprc
-rw-------   1 loke loke       16 2007-12-30 23:24 .esd_auth
drwxr-xr-x   8 loke loke     4096 2007-12-31 01:34 .evolution
-rw-r--r--   1 loke loke    21954 2007-01-05 15:57 .face
-rw-r--r--   1 loke loke     4727 2007-04-17 13:51 .face.icon
drwxr-xr-x   2 loke loke     4096 2007-07-06 22:54 .font
drwxr-xr-x   2 loke loke     4096 2007-12-31 03:03 .fontconfig
-rw-r--r--   1 loke loke    31651 2006-12-26 16:52 .fonts.cache-1
-rw-r--r--   1 loke loke      620 2007-04-17 14:04 .fonts.conf
drwx------   6 loke loke     4096 2007-12-31 18:30 .gconf
drwx------   2 loke loke     4096 2007-12-31 18:30 .gconfd
-rw-------   1 loke loke        0 2007-06-20 05:01 .githistory
-rwxrwxr-x   1 loke loke        0 2007-12-31 01:56 .gksu.lock
-rw-r--r--   1 loke loke      270 2007-09-01 23:34 .gmrun_history
drwx------   2 loke loke     4096 2007-01-20 12:33 .gnome2_private
drwx------   2 loke games    4096 2007-11-28 03:43 .gnome_private
drwx------   3 loke loke     4096 2007-02-26 17:08 .gnucash
drwx------   2 loke loke     4096 2007-06-22 10:57 .gnupg
drwx------   2 loke loke     4096 2006-12-28 21:36 .gphoto
-rwxr--r--   1 loke loke      178 2007-11-20 17:56 .gputemp
-rw-------   1 loke loke       34 2007-12-25 07:35 .gtk-bookmarks
-rw-r--r--   1 loke loke      153 2007-12-07 20:52 .gtkrc
-rwxrwxr-x   1 loke loke       86 2006-11-29 17:13 .gtkrc-1.2-gnome2
-rw-r--r--   1 loke loke      172 2007-09-04 22:53 .gtkrc-2.0
-rw-r--r--   1 loke loke      164 2007-09-04 22:53 .gtkrc-2.0.bak
-rw-r--r--   1 loke loke        0 2007-12-07 20:52 .gtkrc.bak
-rw-r--r--   1 loke loke        0 2007-02-02 14:30 .hwdb
-rw-------   1 loke loke    25128 2007-12-31 02:03 .ICEauthority
drwxrwxr-x   3 loke loke     4096 2007-12-17 17:15 .icons
drwxr-xr-x   3 loke loke     4096 2007-01-01 21:18 .java
prw-r--r--   1 loke loke        0 2007-09-25 15:49 .kaxclient.ts
drwxr-xr-x   2 loke loke     4096 2007-12-17 16:44 .kernelcheck
drwx------   3 loke loke     4096 2007-06-05 03:49 .keytouch2
-rw-------   1 loke loke       35 2007-07-03 02:19 .lesshst
drwxrwxr-x   3 loke loke     4096 2006-11-29 17:12 .local
drwxr-xr-x   2 loke loke     4096 2007-03-04 22:01 .lyrics
-rwxrwxr-x   1 loke loke      114 2006-11-29 17:13 .mailcap
drwxrwxr-x   3 loke loke     4096 2006-11-29 17:14 .mcop
-rwxrwxr-x   1 loke loke       31 2007-12-23 01:27 .mcoprc
-rwxrwxr-x   1 loke loke       31 2007-08-27 22:59 .mcoprcYAvPUb.new
drwxrwxr-x   3 loke loke     4096 2006-11-29 14:59 .metacity
-rwxrwxr-x   1 loke loke      230 2006-11-29 17:14 .mime.types
drwxr-xr-x   5 loke loke     4096 2007-09-15 13:36 .miro
drwxrwxr-x   4 loke loke     4096 2007-08-29 17:00 .mozilla
drwxr-xr-x   4 root root     4096 2007-11-20 21:35 .mozillabackup
drwxr-xr-x   2 loke loke     4096 2007-03-10 18:07 .mplayer
-rw-------   1 loke loke       31 2007-12-31 15:43 .nano_history
drwxrwxr-x   4 loke loke     4096 2007-09-13 22:00 .nautilus5-3.tar.gz
drwxrwxr-x   2 loke loke     4096 2006-11-29 17:13 .ntrc_2
-rwxrwxr-x   1 loke loke     1380 2007-11-20 18:15 .nvidia-settings-rc
-rw-r--r--   1 loke loke      116 2007-08-04 21:36 .oth
drwxr-xr-x   4 loke loke     4096 2007-08-10 22:56 .pan2
-rw-r--r--   1 loke loke    11693 2007-08-28 01:54 .pypanelrc
-rw-r--r--   1 loke loke        0 2007-01-18 02:17 .qemu_history
drwxrwxr-x   2 loke loke     4096 2007-12-22 18:17 .qt
-rwxrwxr-x   1 loke loke   101367 2007-12-14 15:11 .recently-used
-rw-r--r--   1 loke loke   919133 2007-12-31 17:10 .recently-used.xbel
-rw-r--r--   1 loke loke      237 2007-05-18 05:25 .registry
-rw-------   1 loke loke     1024 2007-12-13 23:25 .rnd
drwx------   2 loke loke     4096 2007-01-11 21:29 .scim
-rw-------   1 loke loke      147 2007-12-31 18:29 .serverauth.12056
-rw-------   1 loke loke      147 2007-12-30 23:45 .serverauth.13005
-rw-------   1 loke loke      147 2007-12-30 23:33 .serverauth.6738
-rw-------   1 loke loke      147 2007-12-30 23:24 .serverauth.6834
-rw-------   1 loke loke       98 2007-12-31 02:11 .serverauth.7079
drwx------   4 loke loke     4096 2007-09-22 14:56 .smc
drwxr-xr-x   2 loke loke     4096 2007-02-24 20:12 .spumux
drwxrwxr-x   3 loke loke     4096 2006-11-29 17:12 .subversion
-rw-r--r--   1 loke loke        0 2007-05-06 21:28 .sudo_as_admin_successful
drwxrwxr-x   2 loke loke     4096 2006-11-29 17:12 .synaptic
-rw-r--r--   1 loke loke     2608 2007-01-15 21:31 .tdfsb
drwxrwxr-x   5 loke loke     4096 2007-12-31 02:10 .themes
drwxrwxr-x   5 loke loke     4096 2006-11-29 17:13 .thumbnails
drwxrwxr-x   2 loke loke     4096 2007-10-30 19:31 .Trash
drwxrwxr-x   2 loke loke     4096 2006-11-29 17:13 .update-manager
drwxr-xr-x   2 loke loke     4096 2007-04-05 17:39 .update-manager-core
drwxrwxr-x   2 loke loke     4096 2006-11-29 17:12 .update-notifier
-rw-------   1 loke loke      749 2007-04-21 20:32 .viminfo
drwxrwxr-x   3 loke loke     4096 2006-12-15 11:42 .vlc
drwx------   2 loke loke     4096 2007-08-09 14:09 .w3m
drwxrwxr-x   2 loke loke     4096 2007-12-27 19:21 .wapi
-rwxrwxr-x   1 loke loke        4 2006-11-29 17:13 .windows-label
drwxr-xr-x   2 loke loke     4096 2007-04-17 12:06 .wmii-3
drwxr-xr-x   2 loke loke     4096 2007-05-22 01:49 .wmii-3.5
drwxr-x---   3 loke loke     4096 2007-03-04 22:26 .xarchive
-rw-------   1 loke loke       98 2007-12-31 02:11 .Xauthority
drwxr-xr-x   3 loke loke     4096 2007-02-24 20:27 .xbindkeys_config
-rw-r--r--   1 loke loke      244 2007-12-12 17:54 .xbindkeysrc
-rw-r--r--   1 loke loke     4099 2007-12-06 14:39 .Xdefaults
-rw-r--r--   1 root root  4436553 2007-06-30 01:38 .xfce4.installer-log
drwxr-xr-x   3 loke loke     4096 2007-12-30 22:47 .xine
-rw-r--r--   1 loke loke      306 2007-12-19 20:13 .xinitrc
drwxr-xr-x   2 loke loke     4096 2007-09-25 13:51 .xmltv
-rw-r--r--   1 loke loke      623 2007-12-31 02:11 .xsession-errors
-rw-r--r--   1 loke loke    25043 2007-08-23 13:43 .zcompdump
-rw-------   1 loke loke    21381 2007-09-21 17:59 .zhistory
-rw-r--r--   1 loke loke     2173 2007-09-04 17:20 .zshrc
```

**EDIT**: I loaded up Sonata and it's displaying my GTK theme just fine, so it must be a problem with Firefox Beta 3 (the only other app I run with GTK theme support).

---

### Post by taurus on 2007-12-31
Try changing both .gnome2_private & .gnome_private to something else.

```
mv .gnome2_private .gnome2_private.bak
mv .gnome_private .gnome_private.bak
```
Then, log out and back in again and see what happens.

---

### Post by ~LoKe on 2007-12-31
Hm...unfortunately that doesn't seem to help.  I removed .gnome and gnome2 (not sure how I missed these two).  Still the same.  I'm guessing it's a bug with Firefox 3, as it's still in beta.

Thanks for the help!

---

### Post by ~LoKe on 2007-12-31
Removed Firefox/Firefox-3.0, every single "firefox" file I could find, everything.  Installed the AMD64 debs for xulrunner, nss and firefox-3.0 from launchpad and **all is well**!

---

