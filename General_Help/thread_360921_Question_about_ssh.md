---
title: "Question about ssh"
date: 2007-02-13
forum: General Help
---

### Post by jdm2 on 2007-02-13
I have for only my account can be accessed with ssh.  I just started doing ssh again because I'm looking at getting it all set up for I can access it from school to get stuff I need from it.  When I just logged in on my network from a xp machine I got this output:

Linux  #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007 i686 GNU/Linux



The programs included with the Ubuntu system are free software;

the exact distribution terms for each program are described in the

individual files in /usr/share/doc/*/copyright.



Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by

applicable law.

Last login: 

mkdir: cannot create directory `/tmp/kde-jdm': File exists

mkdir: cannot create directory `/tmp/ksocket-jdm': File exists

jdm@jdm-desktop:~$ can't register Arts::MidiManager

There are already artsd objects registered, looking if they are active...



Error: Can't add object reference (probably artsd is already running).

       If you are sure it is not already running, remove the relevant files:



       /tmp/ksocket-jdm/Arts_SoundServerV2

       /tmp/ksocket-jdm/Arts_SoundServer

       /tmp/ksocket-jdm/Arts_SimpleSoundServer

       /tmp/ksocket-jdm/Arts_PlayObjectFactory

       /tmp/ksocket-jdm/Arts_AudioManager

I'm using drapper.  I read that I could get a graphical screen by starting the x seeson but when I do that I get this:

xauth:  creating new authority file /home/jdm/.serverauth.27755
X: user not authorized to run the X server, aborting.
xinit:  Server error.


Can you help me.  I just want to have a secure connection and be able to view,copy,paste files into my machine or from my machine from a xp machine.  Thanks for the help.

---

### Post by llamakc on 2007-02-13
You installed over an existing system and left an old /home partition possibly? You're having permission/ownership issues.

If you do `ls -al` in your home directory:

```

cd && ls -al

```

Check as to whether or not all of your files are owned by "jdm:jdm" and not some numbered UID.

---

### Post by llamakc on 2007-02-13
> **llamakc said:**
> You installed over an existing system and left an old /home partition possibly? You're having permission/ownership issues.

If you do `ls -al` in your home directory:

```

cd && ls -al

```Check as to whether or not all of your files are owned by "jdm:jdm" and not some numbered UID.

And I forgot to offer a fix.

```

cd && sudo chown -R jdm:jdm .

```

Not the trailing single dot on the above command. It is imperative that you are in /home/jdm when you execute that command and do so as posted above.

---

### Post by jdm2 on 2007-02-13
Here's the output for ls -al

jdm@jdm-desktop:~$ ls -al
total 3080
drwxr-xr-x 101 jdm  jdm      4096 2007-02-13 18:14 .
drwxr-xr-x   6 root root     4096 2006-12-09 15:28 ..
-rw-r--r--   1 jdm  root   133091 2007-01-09 17:31 .1161642358189.jpg
-rwxr--r--   1 jdm  root   641857 2006-08-04 10:05 30118-fyre-gimp.jpg
drwx------   2 jdm  root     4096 2006-11-11 23:11 .AbiSuite
-rw-r--r--   1 jdm  root  1544253 2006-11-11 13:32 .aegis.log
-rw-r--r--   1 jdm  root       34 2006-11-11 13:32 .aegisrc
drwx------   2 jdm  root     4096 2006-12-02 13:46 .alsaplayer
drwxr-xr-x   3 jdm  root     4096 2006-08-10 19:55 .armagetron
-rw-r--r--   1 jdm  root      344 2006-08-25 14:52 .audacity
drwxr-xr-x   2 jdm  root    16384 2007-02-12 18:13 .backgrounds
-rw-------   1 jdm  jdm     10174 2007-02-13 18:15 .bash_history
-rw-r--r--   1 jdm  jdm       220 2006-08-04 11:56 .bash_logout
-rw-r--r--   1 jdm  jdm       482 2006-12-02 15:10 .bash_profile
-rw-r--r--   1 jdm  jdm      2227 2006-08-04 11:56 .bashrc
drwxr-xr-x   5 jdm  root     4096 2006-08-10 19:42 .blender
drwxr-xr-x   4 jdm  root     4096 2006-08-12 09:37 .bzf
drwx------   4 jdm  root     4096 2006-09-14 17:39 .cache
drwx------   2 jdm  root     4096 2006-10-10 20:42 .camel_certs
-rw-------   1 jdm  root     3392 2007-01-31 14:58 .cgobanrc
drwx------   2 jdm  root     4096 2007-01-30 19:59 .clay
drwx------   9 jdm  root     4096 2006-12-22 21:23 .config
drwx------   2 jdm  root     4096 2006-09-14 17:55 .cups
-rw-------   1 jdm  root     1078 2006-11-11 16:10 .dead.letter
drwxr-xr-x   2 jdm  jdm      4096 2007-02-11 12:10 Desktop
drwxr-xr-x  11 jdm  root     4096 2006-12-04 20:45 deusex
drwxr-xr-x   5 jdm  root     4096 2006-08-10 19:43 .dia
-rw-------   1 jdm  jdm        26 2006-08-04 12:03 .dmrc
drwxr-xr-x   9 jdm  root     4096 2006-10-17 16:14 .dvdcss
drwxr-xr-x   5 jdm  root     4096 2006-10-28 23:42 .eboard
-rw-------   1 jdm  jdm        16 2006-08-04 12:03 .esd_auth
drwxr-xr-x   2 jdm  root     4096 2006-10-26 17:01 .ethereal
drwxr-xr-x   9 jdm  root     4096 2007-02-11 00:03 .evolution
lrwxrwxrwx   1 jdm  jdm        26 2006-08-21 14:37 .Examples -> /usr/share/example-content
-rw-r--r--   1 jdm  root     3796 2007-02-11 13:50 .fbhighlevelshistory
-rw-r--r--   1 jdm  root      545 2007-02-11 13:48 .fbrc
drwxr-xr-x   4 jdm  root     4096 2007-01-30 19:53 .fltk
-rw-r--r--   1 jdm  root        0 2007-01-12 17:16 .fonts.cache-1
-rw-r--r--   1 jdm  root      185 2006-12-22 21:13 .freespeak
drwx------   6 jdm  jdm      4096 2007-02-12 20:29 .gaim
drwx------   6 jdm  jdm      4096 2007-02-11 12:23 .gconf
drwx------   2 jdm  jdm      4096 2007-02-13 21:45 .gconfd
drwxr-xr-x   7 jdm  root     4096 2007-01-03 17:04 .gdesklets
drwx------   2 jdm  root     4096 2006-09-20 20:01 .gftp
drwxr-xr-x  21 jdm  root     4096 2007-02-04 20:14 .gimp-2.2
drwxr-xr-x   5 jdm  root     4096 2006-11-06 16:20 .gkrellm2
-rw-r-----   1 jdm  jdm         0 2007-02-13 16:52 .gksu.lock
drwxr-xr-x   2 jdm  root     4096 2007-02-13 18:30 .glchess
drwxr-xr-x   2 jdm  root     4096 2006-08-22 17:49 .gnochm
drwxr-xr-x   7 jdm  jdm      4096 2007-02-03 13:38 .gnome
drwx------  24 jdm  jdm      4096 2007-02-11 00:03 .gnome2
drwx------   2 jdm  jdm      4096 2006-10-10 20:41 .gnome2_private
drwx------   2 jdm  root     4096 2006-09-07 11:18 .gnome_private
drwx------   4 jdm  root     4096 2006-08-21 16:48 .gnomesword-2.0
drwx------   2 jdm  root     4096 2006-09-07 11:18 .gnupg
drwx------   2 jdm  root     4096 2006-08-25 14:58 .gnusound
drwx------   4 jdm  root     4096 2006-11-23 14:20 .googleearth
drwx------   2 jdm  root     4096 2006-11-29 18:08 .gpass
drwx------   2 jdm  root     4096 2006-09-16 20:50 .gpe
drwx------   2 jdm  root     4096 2006-11-04 18:07 .gpilotd
-rw-r--r--   1 jdm  root        5 2006-11-04 18:07 .gpilotd.pid
drwxr-xr-x   2 jdm  jdm      4096 2006-08-25 14:51 .gstreamer-0.10
drwxr-xr-x   2 jdm  root     4096 2006-08-11 16:11 .gstreamer-0.8
-rw-------   1 jdm  root       46 2007-02-13 18:00 .gtk-bookmarks
drwxr-xr-x   2 jdm  root     4096 2006-08-23 15:29 .gtkpod
-rw-r--r--   1 jdm  root       85 2006-10-28 17:15 .gtkrc-1.2-gnome2
drwx------   4 jdm  root     4096 2006-12-13 21:17 .gurlchecker
-rw-r--r--   1 jdm  root       95 2006-12-22 21:33 .gworldclock
drwx------   2 jdm  root     4096 2006-12-07 21:42 .gxine
drwxr-xr-x   2 jdm  root     4096 2006-08-10 20:30 .holotz-castle
-rw-r--r--   1 jdm  root       32 2006-12-02 13:18 .hwdb
-rw-------   1 jdm  root     7287 2007-02-11 14:09 .ICEauthority
-rw-r--r--   1 jdm  root      670 2007-01-30 20:01 .icebreaker
drwxr-xr-x   3 jdm  jdm      4096 2006-12-05 18:50 .icons
drwxr-xr-x   6 jdm  root     4096 2006-12-24 11:25 .ies4linux
drwxr-xr-x   3 jdm  root     4096 2006-08-21 16:59 .ipodder
lrwxrwxrwx   1 root root       17 2006-12-09 16:42 .isolinux.cfg -> isolinux.cfg.cpio
lrwxrwxrwx   1 root root       19 2006-12-09 16:42 .isolinux-H.cfg -> isolinux-H.cfg.cpio
-rw-r--r--   1 jdm  root      285 2007-01-31 14:48 .isomaster
drwxr-xr-x   3 jdm  root     4096 2006-12-25 22:49 .iTunes
drwxr-xr-x   3 jdm  root     4096 2006-08-24 14:38 .java
-rw-------   1 root root       42 2006-12-15 23:03 .john.pot
drwx------   3 jdm  jdm      4096 2006-12-02 19:22 .kde
drwxr-----   2 jdm  root     4096 2006-08-25 14:58 .kluppe
-rw-r--r--   1 jdm  root       33 2006-12-22 21:30 .leafpad
-rw-------   1 jdm  root        0 2007-02-13 18:02 .lesshst
drwx------   4 jdm  games    4096 2006-08-12 09:44 .lgames
drwxr-xr-x   5 jdm  root     4096 2006-12-17 11:33 .limewire
drwxr-xr-x   2 jdm  root     4096 2007-01-31 14:59 .livechatsupport
drwxr-xr-x   3 jdm  root     4096 2006-08-06 10:03 .local
drwx------   3 jdm  root     4096 2006-09-23 15:18 .loki
drwx------   4 jdm  root     4096 2006-12-03 11:29 .macromedia
drwxrw-rw-   3 jdm  jdm      4096 2006-08-04 16:22 .mcop
-rwxrw-rw-   1 jdm  root       31 2007-02-11 13:51 .mcoprc
drwx------   3 jdm  jdm      4096 2006-08-04 12:03 .metacity
drwxr-xr-x   2 jdm  root     4096 2007-02-10 16:31 Misc
-rw-r--r--   1 jdm  root       37 2007-01-30 19:39 .monster-masher
drwx------   5 jdm  jdm      4096 2006-08-25 05:07 .mozilla
drwx------   3 jdm  root     4096 2006-09-11 15:24 .mozilla-thunderbird
drwxr-xr-x   2 jdm  root     4096 2006-12-22 14:58 .mplayer
drwxr-xr-x   3 jdm  jdm      4096 2006-08-04 12:03 .nautilus
-rw-------   1 jdm  root      922 2006-12-13 21:15 .nessusrc
drwxr-xr-x   3 jdm  root     4096 2006-09-23 15:30 .netscape
drwxr-xr-x   2 jdm  root     4096 2007-01-30 19:40 .neverball
-rw-r--r--   1 jdm  root       15 2007-01-30 19:41 .njamconf
-rw-------   1 jdm  root      135 2007-01-20 10:32 .notifier.conf
drwx------   3 jdm  jdm      4096 2007-02-13 17:03 .openoffice.org2
drwx------   3 jdm  root     4096 2006-09-20 20:01 .pan
drwxr-xr-x   3 jdm  root     4096 2006-08-10 20:32 .parallelrealities
drwxr-xr-x   9 jdm  root     4096 2007-01-30 19:42 .pcsx
drwxr-xr-x   3 jdm  root     4096 2006-09-20 20:00 .penguintv
drwx------   2 jdm  root     4096 2007-02-13 16:55 .putty
drwxr-xr-x   2 jdm  root     4096 2006-09-14 18:41 .qdvdauthor
drwxr-xr-x   2 jdm  jdm      4096 2007-02-10 07:15 .qt
-rw-r--r--   1 jdm  root       58 2006-09-18 13:53 .rainbow-db.xml
-rw-------   1 jdm  root    36335 2007-01-20 11:19 .realplayerrc
-rw-------   1 jdm  jdm     88078 2007-02-13 18:12 .recently-used
-rw-------   1 root root       93 2006-12-15 23:52 .restore
-rw-------   1 jdm  root     1567 2006-08-27 17:08 .ripperXrc
-rw-r--r--   1 jdm  root     3249 2006-09-18 13:53 .roboradio-state
drwxr-xr-x   5 jdm  root     4096 2007-01-31 15:03 .scid
drwx------   4 jdm  root     4096 2006-09-23 15:03 .screem
drwxr-xr-x   2 jdm  root     4096 2006-10-19 16:52 .serpentine
-rw-------   1 jdm  root      112 2007-02-13 17:09 .serverauth.25850
-rw-------   1 jdm  root      168 2007-02-13 18:01 .serverauth.27368
drwxr-xr-x   2 jdm  root     4096 2007-01-31 15:05 .sjeng
drwxr-xr-x   3 jdm  root     4096 2007-02-13 18:31 .streamtuner
-rw-r--r--   1 jdm  jdm         0 2006-08-04 13:03 .sudo_as_admin_successful
drwxr-xr-x   4 jdm  root     4096 2006-08-12 09:44 .supertux
drwx------   4 jdm  root     4096 2006-08-21 16:48 .sword
-rw-------   1 jdm  root    12288 2006-11-14 18:02 .swp
drwxr-xr-x   2 jdm  root     4096 2006-08-11 16:44 .swscanner
lrwxrwxrwx   1 root root       17 2006-12-09 16:42 .syslinux.cfg -> syslinux.cfg.cpio
lrwxrwxrwx   1 root root       19 2006-12-09 16:42 .syslinux-H.cfg -> syslinux-H.cfg.cpio
drwxr-xr-x   9 jdm  jdm      4096 2007-01-09 20:30 .themes
drwx------   4 jdm  jdm      4096 2006-08-21 14:46 .thumbnails
drwxr-xr-x   3 jdm  root     4096 2006-08-06 09:19 .tomboy
drwx------   2 jdm  jdm      4096 2007-02-11 13:30 .Trash
drwx------   2 jdm  root     4096 2006-10-01 17:38 .tsclient
-rw-r--r--   1 jdm  root      149 2006-12-22 21:34 .tzlist
-rw-r--r--   1 jdm  root        0 2006-08-11 16:49 .ubuntustudio2config
drwx------   2 jdm  jdm      4096 2006-11-21 14:42 .update-notifier
-rw-------   1 jdm  root     8553 2006-12-02 19:22 .viminfo
drwxr-xr-x   3 jdm  root     4096 2006-08-25 14:16 .vlc
drwxr-xr-x   2 jdm  root     4096 2006-12-05 17:13 .vmware
drwxr-xr-x   2 jdm  root     4096 2006-11-11 22:36 .wapi
drwxr-xr-x   4 jdm  root     4096 2007-01-09 16:15 .wine
drwxr-x---   2 jdm  root     4096 2007-01-30 19:48 .wormux
-rw-------   1 jdm  root      171 2007-02-13 17:09 .Xauthority
drwx------   3 jdm  root     4096 2006-10-18 17:56 .xchat2
drwxr-xr-x   2 jdm  root     4096 2006-12-21 22:28 .xine
drwxr-xr-x   4 jdm  root     4096 2006-12-25 23:25 .xmms
drwx------   4 jdm  root     4096 2007-02-04 19:52 .xmoto
-rw-r--r--   1 jdm  root    68990 2007-02-13 18:38 .xsession-errors
drwxr-xr-x   2 jdm  root     4096 2007-01-30 19:57 .zsnes

Here's the output for cd && ls -al

jdm@jdm-desktop:~$ cd && ls -al
total 3080
drwxr-xr-x 101 jdm  jdm      4096 2007-02-13 18:14 .
drwxr-xr-x   6 root root     4096 2006-12-09 15:28 ..
-rw-r--r--   1 jdm  root   133091 2007-01-09 17:31 .1161642358189.jpg
-rwxr--r--   1 jdm  root   641857 2006-08-04 10:05 30118-fyre-gimp.jpg
drwx------   2 jdm  root     4096 2006-11-11 23:11 .AbiSuite
-rw-r--r--   1 jdm  root  1544253 2006-11-11 13:32 .aegis.log
-rw-r--r--   1 jdm  root       34 2006-11-11 13:32 .aegisrc
drwx------   2 jdm  root     4096 2006-12-02 13:46 .alsaplayer
drwxr-xr-x   3 jdm  root     4096 2006-08-10 19:55 .armagetron
-rw-r--r--   1 jdm  root      344 2006-08-25 14:52 .audacity
drwxr-xr-x   2 jdm  root    16384 2007-02-12 18:13 .backgrounds
-rw-------   1 jdm  jdm     10174 2007-02-13 18:15 .bash_history
-rw-r--r--   1 jdm  jdm       220 2006-08-04 11:56 .bash_logout
-rw-r--r--   1 jdm  jdm       482 2006-12-02 15:10 .bash_profile
-rw-r--r--   1 jdm  jdm      2227 2006-08-04 11:56 .bashrc
drwxr-xr-x   5 jdm  root     4096 2006-08-10 19:42 .blender
drwxr-xr-x   4 jdm  root     4096 2006-08-12 09:37 .bzf
drwx------   4 jdm  root     4096 2006-09-14 17:39 .cache
drwx------   2 jdm  root     4096 2006-10-10 20:42 .camel_certs
-rw-------   1 jdm  root     3392 2007-01-31 14:58 .cgobanrc
drwx------   2 jdm  root     4096 2007-01-30 19:59 .clay
drwx------   9 jdm  root     4096 2006-12-22 21:23 .config
drwx------   2 jdm  root     4096 2006-09-14 17:55 .cups
-rw-------   1 jdm  root     1078 2006-11-11 16:10 .dead.letter
drwxr-xr-x   2 jdm  jdm      4096 2007-02-11 12:10 Desktop
drwxr-xr-x  11 jdm  root     4096 2006-12-04 20:45 deusex
drwxr-xr-x   5 jdm  root     4096 2006-08-10 19:43 .dia
-rw-------   1 jdm  jdm        26 2006-08-04 12:03 .dmrc
drwxr-xr-x   9 jdm  root     4096 2006-10-17 16:14 .dvdcss
drwxr-xr-x   5 jdm  root     4096 2006-10-28 23:42 .eboard
-rw-------   1 jdm  jdm        16 2006-08-04 12:03 .esd_auth
drwxr-xr-x   2 jdm  root     4096 2006-10-26 17:01 .ethereal
drwxr-xr-x   9 jdm  root     4096 2007-02-11 00:03 .evolution
lrwxrwxrwx   1 jdm  jdm        26 2006-08-21 14:37 .Examples -> /usr/share/example-content
-rw-r--r--   1 jdm  root     3796 2007-02-11 13:50 .fbhighlevelshistory
-rw-r--r--   1 jdm  root      545 2007-02-11 13:48 .fbrc
drwxr-xr-x   4 jdm  root     4096 2007-01-30 19:53 .fltk
-rw-r--r--   1 jdm  root        0 2007-01-12 17:16 .fonts.cache-1
-rw-r--r--   1 jdm  root      185 2006-12-22 21:13 .freespeak
drwx------   6 jdm  jdm      4096 2007-02-12 20:29 .gaim
drwx------   6 jdm  jdm      4096 2007-02-11 12:23 .gconf
drwx------   2 jdm  jdm      4096 2007-02-13 21:46 .gconfd
drwxr-xr-x   7 jdm  root     4096 2007-01-03 17:04 .gdesklets
drwx------   2 jdm  root     4096 2006-09-20 20:01 .gftp
drwxr-xr-x  21 jdm  root     4096 2007-02-04 20:14 .gimp-2.2
drwxr-xr-x   5 jdm  root     4096 2006-11-06 16:20 .gkrellm2
-rw-r-----   1 jdm  jdm         0 2007-02-13 16:52 .gksu.lock
drwxr-xr-x   2 jdm  root     4096 2007-02-13 18:30 .glchess
drwxr-xr-x   2 jdm  root     4096 2006-08-22 17:49 .gnochm
drwxr-xr-x   7 jdm  jdm      4096 2007-02-03 13:38 .gnome
drwx------  24 jdm  jdm      4096 2007-02-11 00:03 .gnome2
drwx------   2 jdm  jdm      4096 2006-10-10 20:41 .gnome2_private
drwx------   2 jdm  root     4096 2006-09-07 11:18 .gnome_private
drwx------   4 jdm  root     4096 2006-08-21 16:48 .gnomesword-2.0
drwx------   2 jdm  root     4096 2006-09-07 11:18 .gnupg
drwx------   2 jdm  root     4096 2006-08-25 14:58 .gnusound
drwx------   4 jdm  root     4096 2006-11-23 14:20 .googleearth
drwx------   2 jdm  root     4096 2006-11-29 18:08 .gpass
drwx------   2 jdm  root     4096 2006-09-16 20:50 .gpe
drwx------   2 jdm  root     4096 2006-11-04 18:07 .gpilotd
-rw-r--r--   1 jdm  root        5 2006-11-04 18:07 .gpilotd.pid
drwxr-xr-x   2 jdm  jdm      4096 2006-08-25 14:51 .gstreamer-0.10
drwxr-xr-x   2 jdm  root     4096 2006-08-11 16:11 .gstreamer-0.8
-rw-------   1 jdm  root       46 2007-02-13 18:00 .gtk-bookmarks
drwxr-xr-x   2 jdm  root     4096 2006-08-23 15:29 .gtkpod
-rw-r--r--   1 jdm  root       85 2006-10-28 17:15 .gtkrc-1.2-gnome2
drwx------   4 jdm  root     4096 2006-12-13 21:17 .gurlchecker
-rw-r--r--   1 jdm  root       95 2006-12-22 21:33 .gworldclock
drwx------   2 jdm  root     4096 2006-12-07 21:42 .gxine
drwxr-xr-x   2 jdm  root     4096 2006-08-10 20:30 .holotz-castle
-rw-r--r--   1 jdm  root       32 2006-12-02 13:18 .hwdb
-rw-------   1 jdm  root     7287 2007-02-11 14:09 .ICEauthority
-rw-r--r--   1 jdm  root      670 2007-01-30 20:01 .icebreaker
drwxr-xr-x   3 jdm  jdm      4096 2006-12-05 18:50 .icons
drwxr-xr-x   6 jdm  root     4096 2006-12-24 11:25 .ies4linux
drwxr-xr-x   3 jdm  root     4096 2006-08-21 16:59 .ipodder
lrwxrwxrwx   1 root root       17 2006-12-09 16:42 .isolinux.cfg -> isolinux.cfg.cpio
lrwxrwxrwx   1 root root       19 2006-12-09 16:42 .isolinux-H.cfg -> isolinux-H.cfg.cpio
-rw-r--r--   1 jdm  root      285 2007-01-31 14:48 .isomaster
drwxr-xr-x   3 jdm  root     4096 2006-12-25 22:49 .iTunes
drwxr-xr-x   3 jdm  root     4096 2006-08-24 14:38 .java
-rw-------   1 root root       42 2006-12-15 23:03 .john.pot
drwx------   3 jdm  jdm      4096 2006-12-02 19:22 .kde
drwxr-----   2 jdm  root     4096 2006-08-25 14:58 .kluppe
-rw-r--r--   1 jdm  root       33 2006-12-22 21:30 .leafpad
-rw-------   1 jdm  root        0 2007-02-13 18:02 .lesshst
drwx------   4 jdm  games    4096 2006-08-12 09:44 .lgames
drwxr-xr-x   5 jdm  root     4096 2006-12-17 11:33 .limewire
drwxr-xr-x   2 jdm  root     4096 2007-01-31 14:59 .livechatsupport
drwxr-xr-x   3 jdm  root     4096 2006-08-06 10:03 .local
drwx------   3 jdm  root     4096 2006-09-23 15:18 .loki
drwx------   4 jdm  root     4096 2006-12-03 11:29 .macromedia
drwxrw-rw-   3 jdm  jdm      4096 2006-08-04 16:22 .mcop
-rwxrw-rw-   1 jdm  root       31 2007-02-11 13:51 .mcoprc
drwx------   3 jdm  jdm      4096 2006-08-04 12:03 .metacity
drwxr-xr-x   2 jdm  root     4096 2007-02-10 16:31 Misc
-rw-r--r--   1 jdm  root       37 2007-01-30 19:39 .monster-masher
drwx------   5 jdm  jdm      4096 2006-08-25 05:07 .mozilla
drwx------   3 jdm  root     4096 2006-09-11 15:24 .mozilla-thunderbird
drwxr-xr-x   2 jdm  root     4096 2006-12-22 14:58 .mplayer
drwxr-xr-x   3 jdm  jdm      4096 2006-08-04 12:03 .nautilus
-rw-------   1 jdm  root      922 2006-12-13 21:15 .nessusrc
drwxr-xr-x   3 jdm  root     4096 2006-09-23 15:30 .netscape
drwxr-xr-x   2 jdm  root     4096 2007-01-30 19:40 .neverball
-rw-r--r--   1 jdm  root       15 2007-01-30 19:41 .njamconf
-rw-------   1 jdm  root      135 2007-01-20 10:32 .notifier.conf
drwx------   3 jdm  jdm      4096 2007-02-13 17:03 .openoffice.org2
drwx------   3 jdm  root     4096 2006-09-20 20:01 .pan
drwxr-xr-x   3 jdm  root     4096 2006-08-10 20:32 .parallelrealities
drwxr-xr-x   9 jdm  root     4096 2007-01-30 19:42 .pcsx
drwxr-xr-x   3 jdm  root     4096 2006-09-20 20:00 .penguintv
drwx------   2 jdm  root     4096 2007-02-13 16:55 .putty
drwxr-xr-x   2 jdm  root     4096 2006-09-14 18:41 .qdvdauthor
drwxr-xr-x   2 jdm  jdm      4096 2007-02-10 07:15 .qt
-rw-r--r--   1 jdm  root       58 2006-09-18 13:53 .rainbow-db.xml
-rw-------   1 jdm  root    36335 2007-01-20 11:19 .realplayerrc
-rw-------   1 jdm  jdm     88078 2007-02-13 18:12 .recently-used
-rw-------   1 root root       93 2006-12-15 23:52 .restore
-rw-------   1 jdm  root     1567 2006-08-27 17:08 .ripperXrc
-rw-r--r--   1 jdm  root     3249 2006-09-18 13:53 .roboradio-state
drwxr-xr-x   5 jdm  root     4096 2007-01-31 15:03 .scid
drwx------   4 jdm  root     4096 2006-09-23 15:03 .screem
drwxr-xr-x   2 jdm  root     4096 2006-10-19 16:52 .serpentine
-rw-------   1 jdm  root      112 2007-02-13 17:09 .serverauth.25850
-rw-------   1 jdm  root      168 2007-02-13 18:01 .serverauth.27368
drwxr-xr-x   2 jdm  root     4096 2007-01-31 15:05 .sjeng
drwxr-xr-x   3 jdm  root     4096 2007-02-13 18:31 .streamtuner
-rw-r--r--   1 jdm  jdm         0 2006-08-04 13:03 .sudo_as_admin_successful
drwxr-xr-x   4 jdm  root     4096 2006-08-12 09:44 .supertux
drwx------   4 jdm  root     4096 2006-08-21 16:48 .sword
-rw-------   1 jdm  root    12288 2006-11-14 18:02 .swp
drwxr-xr-x   2 jdm  root     4096 2006-08-11 16:44 .swscanner
lrwxrwxrwx   1 root root       17 2006-12-09 16:42 .syslinux.cfg -> syslinux.cfg.cpio
lrwxrwxrwx   1 root root       19 2006-12-09 16:42 .syslinux-H.cfg -> syslinux-H.cfg.cpio
drwxr-xr-x   9 jdm  jdm      4096 2007-01-09 20:30 .themes
drwx------   4 jdm  jdm      4096 2006-08-21 14:46 .thumbnails
drwxr-xr-x   3 jdm  root     4096 2006-08-06 09:19 .tomboy
drwx------   2 jdm  jdm      4096 2007-02-11 13:30 .Trash
drwx------   2 jdm  root     4096 2006-10-01 17:38 .tsclient
-rw-r--r--   1 jdm  root      149 2006-12-22 21:34 .tzlist
-rw-r--r--   1 jdm  root        0 2006-08-11 16:49 .ubuntustudio2config
drwx------   2 jdm  jdm      4096 2006-11-21 14:42 .update-notifier
-rw-------   1 jdm  root     8553 2006-12-02 19:22 .viminfo
drwxr-xr-x   3 jdm  root     4096 2006-08-25 14:16 .vlc
drwxr-xr-x   2 jdm  root     4096 2006-12-05 17:13 .vmware
drwxr-xr-x   2 jdm  root     4096 2006-11-11 22:36 .wapi
drwxr-xr-x   4 jdm  root     4096 2007-01-09 16:15 .wine
drwxr-x---   2 jdm  root     4096 2007-01-30 19:48 .wormux
-rw-------   1 jdm  root      171 2007-02-13 17:09 .Xauthority
drwx------   3 jdm  root     4096 2006-10-18 17:56 .xchat2
drwxr-xr-x   2 jdm  root     4096 2006-12-21 22:28 .xine
drwxr-xr-x   4 jdm  root     4096 2006-12-25 23:25 .xmms
drwx------   4 jdm  root     4096 2007-02-04 19:52 .xmoto
-rw-r--r--   1 jdm  root    68990 2007-02-13 18:38 .xsession-errors
drwxr-xr-x   2 jdm  root     4096 2007-01-30 19:57 .zsnes

There was no output for the cd && sudo chown -R jdm:jdm . command.  Thanks for the help.

---

### Post by llamakc on 2007-02-14
You see what happened, right? Many of your dotfiles in your home directory were owned by root. That last command changed to your home directory and (&&) next it changed ownership (chown) recursively for the directory you were inside of.

It should work just fine now.

---

### Post by Ramses de Norre on 2007-02-14
To get GUI applications to run over ssh, you need an X server at the remote host (probably ok when using ubuntu) and an X client at the local host (so when using window you'll need to install an X client in windows, which is not too easy).
If both conditions are fulfilled you can start ssh with the -X option to enable X forwarding, you can then start GUI applications.

Note that the traffic needed for running GUI apps over the internet is _huge_ and you need a pretty fast connection for both machines to run the apps smoothly. When I use this in my local network at home you almost can't tell that I'm running over the network but when I try this at college for example it takes almost 30min to open a single menu..

---

### Post by jdm2 on 2007-02-14
I really don't need to run apps but what I really want is an easy wayto browse my docs and copy/paste to my machine or to the machine I'm on.  In the ubuntuguide.org drapper guide it has a program called FileZilla but it wouldn't work.  Also when I used putty on my home network to ssh into my box I played an music file with mplayer.  It came out of my ubuntu box.  How can I get it to play on the box I was using?  Thanks for the help.

---

