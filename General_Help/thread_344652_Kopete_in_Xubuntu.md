---
title: "Kopete in Xubuntu??"
date: 2007-01-23
forum: General Help
---

### Post by DougieFresh4U on 2007-01-23
Is it possible to use kopete in Xubuntu as when I use Add/Remove to install it, I see where it says unable to initialize gnome-frontend whatever that means. So what else do I need besides just installing Kopete? thanks):P

---

### Post by Pobega on 2007-01-23
Run> sudo aptitude install kopeteThat should install all of the dependencies you'll need.

---

### Post by DougieFresh4U on 2007-01-23
Thanks, will try that. also what does **"dcopserver"** me as I get this message when trying to use Ksnapshot. I says to make it's running or some thing to that effect                               Also in terminal getting this message::[B]dougie@DougiesToyBox:~$ kopete
kdeinit: Aborting. No write access to $HOME directory (/home/dougie).
kopete: ERROR: KUniqueApplication: Can't setup DCOP communication.
dougie@DougiesToyBox:~$ [/B]

---

### Post by taurus on 2007-01-23
```
ls -la ~
```

---

### Post by DougieFresh4U on 2007-01-23
dougie@DougiesToyBox:~$ ls -la ~
total 12840
drwxr-xr-x 49 root   root      4096 2003-01-10 11:16 .
drwxr-xr-x  3 root   root      4096 2007-01-09 21:56 ..
drwxr-xr-x  3 dougie dougie    4096 2007-01-15 23:44 .adobe
-rw-r--r--  1 dougie dougie 1118089 2003-08-27 09:51 aim-1.5.286.tgz
drwx------  8 dougie dougie    4096 2007-01-12 01:37 .amsn
drwx------  2 dougie dougie    4096 2007-01-12 01:33 amsn_received
-rw-r--r--  1 dougie dougie     283 2007-01-16 01:51 .audacity
drwxr-xr-x  2 dougie root      4096 2007-01-09 23:30 .automatix
-rw-r--r--  1 dougie dougie  454656 2007-01-11 03:34 avatar13.gif
-rw-r--r--  1 dougie dougie    4388 2007-01-11 03:40 avatar_46.jpg
-rw-------  1 dougie dougie    6819 2007-01-23 09:54 .bash_history
-rw-r--r--  1 dougie dougie     220 2007-01-09 21:56 .bash_logout
-rw-r--r--  1 dougie dougie     414 2007-01-09 21:56 .bash_profile
-rw-r--r--  1 dougie dougie    2227 2007-01-09 21:56 .bashrc
drwxr-xr-x  4 dougie dougie    4096 2007-01-10 02:24 .bmp
drwx------  5 dougie dougie    4096 2007-01-10 04:22 .cache
drwx------  7 dougie dougie    4096 2007-01-18 05:36 .config
-rw-r--r--  1 dougie dougie      51 2007-01-16 05:44 .current-song
drwx------  2 dougie dougie    4096 2007-01-23 09:18 Desktop
-rw-r--r--  1 dougie dougie      24 2007-01-09 22:12 .dmrc
drwxr-xr-x  5 dougie dougie    4096 2007-01-23 08:23 .exaile
lrwxrwxrwx  1 dougie dougie      26 2007-01-09 21:56 Examples -> /usr/share/example-content
drwxr-xr-x  2 dougie dougie    4096 2007-01-13 09:26 .fontconfig
-rw-r--r--  1 dougie dougie  483359 2007-01-09 23:12 .fonts.cache-1
drwxr-xr-x  4 dougie dougie    4096 2007-01-23 02:11 .frostwire
drwx------  6 dougie dougie    4096 2007-01-23 09:02 .gaim
drwx------  4 dougie dougie    4096 2007-01-23 09:53 .gconf
drwx------  2 dougie dougie    4096 2007-01-23 09:53 .gconfd
drwxr-xr-x 21 dougie dougie    4096 2007-01-23 09:15 .gimp-2.2
-rw-r-----  1 dougie dougie       0 2007-01-23 09:21 .gksu.lock
drwx------  5 dougie dougie    4096 2007-01-14 19:47 .gnome2
drwx------  2 dougie dougie    4096 2007-01-09 23:37 .gnome2_private
drwx------  2 dougie dougie    4096 2007-01-09 22:48 .gnupg
drwxr-xr-x  5 dougie dougie    4096 2007-01-23 09:42 .gqview
drwxr-xr-x  2 dougie dougie    4096 2007-01-22 14:42 .gstreamer-0.10
drwx------  2 dougie dougie    4096 2007-01-16 01:53 .gxine
-rw-------  1 dougie dougie    1647 2007-01-21 16:42 .ICEauthority
drwxr-xr-x 13 dougie dougie    4096 2006-10-22 11:26 iceweasel-1.5.0.7-g2-i386
-rw-r--r--  1 dougie dougie 7236984 2006-10-22 11:24 iceweasel-1.5.0.7-g2-i386.tar.bz2
drwxr-xr-x  2 dougie dougie    4096 2007-01-09 23:51 .icons
drwxr-xr-x  2 dougie dougie    4096 2007-01-23 02:37 Incomplete
drwxr-xr-x  3 dougie dougie    4096 2007-01-14 19:22 .java
drwx------  3 dougie dougie    4096 2007-01-10 02:22 .kde
-rw-r--r--  1 dougie dougie    1730 2007-01-07 16:34 key.gpg.asc
drwxr-xr-x  3 dougie dougie    4096 2007-01-16 05:19 .listen
drwxr-xr-x  3 dougie dougie    4096 2007-01-09 22:12 .local
drwxr-xr-x  4 dougie dougie    4096 2007-01-10 22:26 .lyrics
drwx------  3 dougie dougie    4096 2007-01-09 23:56 .macromedia
drwxr-xr-x  3 dougie dougie    4096 2007-01-10 15:56 .mcop
-rw-------  1 dougie dougie      31 2007-01-19 10:41 .mcoprc
drwx------  3 dougie dougie    4096 2007-01-10 01:58 .mozilla
drwx------  3 dougie dougie    4096 2007-01-10 01:58 .mozilla-thunderbird
drwxr-xr-x  2 dougie dougie    4096 2007-01-14 19:30 .mplayer
drwxr-xr-x  2 dougie dougie    4096 2007-01-16 01:48 NewName
drwxr-xr-x  2 dougie dougie    4096 2007-01-16 05:16 Podcasts
drwxr-xr-x  2 dougie dougie    4096 2007-01-17 22:43 .qt
drwxr-xr-x  2 dougie dougie    4096 2007-01-23 02:33 Shared
-rw-r--r--  1 dougie dougie  442392 2007-01-15 11:24 snapshot10.png
-rw-r--r--  1 dougie dougie  333006 2007-01-17 22:43 snapshot11.png
-rw-r--r--  1 dougie dougie   70646 2007-01-17 23:41 snapshot12.png
-rw-r--r--  1 dougie dougie  357661 2007-01-18 01:10 snapshot13.png
-rw-r--r--  1 dougie dougie  181942 2007-01-18 01:28 snapshot14.png
-rw-r--r--  1 dougie dougie  271200 2007-01-18 10:45 snapshot15.png
-rw-r--r--  1 dougie dougie  177783 2007-01-18 11:10 snapshot16.png
-rw-r--r--  1 dougie dougie  202494 2007-01-18 12:28 snapshot17.png
-rw-r--r--  1 dougie dougie  203141 2007-01-19 16:10 snapshot18.png
-rw-r--r--  1 dougie dougie  274019 2007-01-15 10:09 snapshot8.png
-rw-r--r--  1 dougie dougie  437878 2007-01-15 10:26 snapshot9.png
drwxr-xr-x  5 dougie dougie    4096 2007-01-16 01:00 src
drwxr-xr-x  3 dougie dougie    4096 2007-01-21 22:11 .streamtuner
-rw-r--r--  1 dougie dougie       0 2007-01-09 22:13 .sudo_as_admin_successful
-rw-r--r--  1 dougie dougie  492997 2007-01-13 08:47 Swiftfox_wallpaper.png
drwxr-xr-x  4 dougie dougie    4096 2007-01-19 12:10 .thumbnails
drwxr-xr-x  2 dougie dougie    4096 2007-01-09 22:18 .update-manager
drwxr-xr-x  4 root   root      4096 2003-01-10 11:16 usr
drwxr-xr-x  3 dougie dougie    4096 2007-01-18 05:25 .vlc
drwxr-xr-x  4 dougie dougie    4096 2007-01-10 05:30 .wine
-rw-------  1 dougie dougie     124 2007-01-21 16:42 .Xauthority
drwxr-xr-x  2 dougie dougie    4096 2007-01-10 04:28 .xine
drwxr-xr-x  4 dougie dougie    4096 2007-01-11 03:52 .xmms
-rw-r--r--  1 dougie dougie   11416 2007-01-09 23:47 .xscreensaver
-rw-r--r--  1 dougie dougie   29899 2007-01-21 22:12 .xsession-errors
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-23
How come your $HOME directory is owned by root now?  Did you change the ownership or something?

```
sudo chown dougie:dougie /home/dougie
ls -la /home/dougie
```

---

### Post by DougieFresh4U on 2007-01-23
I am a dummy, I wouldn't know how to change that. Must have been when I was playing with installing AIM, which is** 'dead in the water'** So here is after your new codes. Is it corrected now? Thank you=D>             dougie@DougiesToyBox:~$ sudo chown dougie:dougie /home/dougie
Password:
dougie@DougiesToyBox:~$ ls -la /home/dougie
total 12840
drwxr-xr-x 49 dougie dougie    4096 2003-01-10 11:16 .
drwxr-xr-x  3 root   root      4096 2007-01-09 21:56 ..
drwxr-xr-x  3 dougie dougie    4096 2007-01-15 23:44 .adobe
-rw-r--r--  1 dougie dougie 1118089 2003-08-27 09:51 aim-1.5.286.tgz
drwx------  8 dougie dougie    4096 2007-01-12 01:37 .amsn
drwx------  2 dougie dougie    4096 2007-01-12 01:33 amsn_received
-rw-r--r--  1 dougie dougie     283 2007-01-16 01:51 .audacity
drwxr-xr-x  2 dougie root      4096 2007-01-09 23:30 .automatix
-rw-r--r--  1 dougie dougie  454656 2007-01-11 03:34 avatar13.gif
-rw-r--r--  1 dougie dougie    4388 2007-01-11 03:40 avatar_46.jpg
-rw-------  1 dougie dougie    6819 2007-01-23 09:54 .bash_history
-rw-r--r--  1 dougie dougie     220 2007-01-09 21:56 .bash_logout
-rw-r--r--  1 dougie dougie     414 2007-01-09 21:56 .bash_profile
-rw-r--r--  1 dougie dougie    2227 2007-01-09 21:56 .bashrc
drwxr-xr-x  4 dougie dougie    4096 2007-01-10 02:24 .bmp
drwx------  5 dougie dougie    4096 2007-01-10 04:22 .cache
drwx------  7 dougie dougie    4096 2007-01-18 05:36 .config
-rw-r--r--  1 dougie dougie      51 2007-01-16 05:44 .current-song
drwx------  2 dougie dougie    4096 2007-01-23 09:18 Desktop
-rw-r--r--  1 dougie dougie      24 2007-01-09 22:12 .dmrc
drwxr-xr-x  5 dougie dougie    4096 2007-01-23 08:23 .exaile
lrwxrwxrwx  1 dougie dougie      26 2007-01-09 21:56 Examples -> /usr/share/example-content
drwxr-xr-x  2 dougie dougie    4096 2007-01-13 09:26 .fontconfig
-rw-r--r--  1 dougie dougie  483359 2007-01-09 23:12 .fonts.cache-1
drwxr-xr-x  4 dougie dougie    4096 2007-01-23 02:11 .frostwire
drwx------  6 dougie dougie    4096 2007-01-23 09:02 .gaim
drwx------  4 dougie dougie    4096 2007-01-23 09:53 .gconf
drwx------  2 dougie dougie    4096 2007-01-23 09:53 .gconfd
drwxr-xr-x 21 dougie dougie    4096 2007-01-23 09:15 .gimp-2.2
-rw-r-----  1 dougie dougie       0 2007-01-23 09:21 .gksu.lock
drwx------  5 dougie dougie    4096 2007-01-14 19:47 .gnome2
drwx------  2 dougie dougie    4096 2007-01-09 23:37 .gnome2_private
drwx------  2 dougie dougie    4096 2007-01-09 22:48 .gnupg
drwxr-xr-x  5 dougie dougie    4096 2007-01-23 09:42 .gqview
drwxr-xr-x  2 dougie dougie    4096 2007-01-22 14:42 .gstreamer-0.10
drwx------  2 dougie dougie    4096 2007-01-16 01:53 .gxine
-rw-------  1 dougie dougie    1647 2007-01-21 16:42 .ICEauthority
drwxr-xr-x 13 dougie dougie    4096 2006-10-22 11:26 iceweasel-1.5.0.7-g2-i386
-rw-r--r--  1 dougie dougie 7236984 2006-10-22 11:24 iceweasel-1.5.0.7-g2-i386.tar.bz2
drwxr-xr-x  2 dougie dougie    4096 2007-01-09 23:51 .icons
drwxr-xr-x  2 dougie dougie    4096 2007-01-23 02:37 Incomplete
drwxr-xr-x  3 dougie dougie    4096 2007-01-14 19:22 .java
drwx------  3 dougie dougie    4096 2007-01-10 02:22 .kde
-rw-r--r--  1 dougie dougie    1730 2007-01-07 16:34 key.gpg.asc
drwxr-xr-x  3 dougie dougie    4096 2007-01-16 05:19 .listen
drwxr-xr-x  3 dougie dougie    4096 2007-01-09 22:12 .local
drwxr-xr-x  4 dougie dougie    4096 2007-01-10 22:26 .lyrics
drwx------  3 dougie dougie    4096 2007-01-09 23:56 .macromedia
drwxr-xr-x  3 dougie dougie    4096 2007-01-10 15:56 .mcop
-rw-------  1 dougie dougie      31 2007-01-19 10:41 .mcoprc
drwx------  3 dougie dougie    4096 2007-01-10 01:58 .mozilla
drwx------  3 dougie dougie    4096 2007-01-10 01:58 .mozilla-thunderbird
drwxr-xr-x  2 dougie dougie    4096 2007-01-14 19:30 .mplayer
drwxr-xr-x  2 dougie dougie    4096 2007-01-16 01:48 NewName
drwxr-xr-x  2 dougie dougie    4096 2007-01-16 05:16 Podcasts
drwxr-xr-x  2 dougie dougie    4096 2007-01-17 22:43 .qt
drwxr-xr-x  2 dougie dougie    4096 2007-01-23 02:33 Shared
-rw-r--r--  1 dougie dougie  442392 2007-01-15 11:24 snapshot10.png
-rw-r--r--  1 dougie dougie  333006 2007-01-17 22:43 snapshot11.png
-rw-r--r--  1 dougie dougie   70646 2007-01-17 23:41 snapshot12.png
-rw-r--r--  1 dougie dougie  357661 2007-01-18 01:10 snapshot13.png
-rw-r--r--  1 dougie dougie  181942 2007-01-18 01:28 snapshot14.png
-rw-r--r--  1 dougie dougie  271200 2007-01-18 10:45 snapshot15.png
-rw-r--r--  1 dougie dougie  177783 2007-01-18 11:10 snapshot16.png
-rw-r--r--  1 dougie dougie  202494 2007-01-18 12:28 snapshot17.png
-rw-r--r--  1 dougie dougie  203141 2007-01-19 16:10 snapshot18.png
-rw-r--r--  1 dougie dougie  274019 2007-01-15 10:09 snapshot8.png
-rw-r--r--  1 dougie dougie  437878 2007-01-15 10:26 snapshot9.png
drwxr-xr-x  5 dougie dougie    4096 2007-01-16 01:00 src
drwxr-xr-x  3 dougie dougie    4096 2007-01-21 22:11 .streamtuner
-rw-r--r--  1 dougie dougie       0 2007-01-09 22:13 .sudo_as_admin_successful
-rw-r--r--  1 dougie dougie  492997 2007-01-13 08:47 Swiftfox_wallpaper.png
drwxr-xr-x  4 dougie dougie    4096 2007-01-19 12:10 .thumbnails
drwxr-xr-x  2 dougie dougie    4096 2007-01-09 22:18 .update-manager
drwxr-xr-x  4 root   root      4096 2003-01-10 11:16 usr
drwxr-xr-x  3 dougie dougie    4096 2007-01-18 05:25 .vlc
drwxr-xr-x  4 dougie dougie    4096 2007-01-10 05:30 .wine
-rw-------  1 dougie dougie     124 2007-01-21 16:42 .Xauthority
drwxr-xr-x  2 dougie dougie    4096 2007-01-10 04:28 .xine
drwxr-xr-x  4 dougie dougie    4096 2007-01-11 03:52 .xmms
-rw-r--r--  1 dougie dougie   11416 2007-01-09 23:47 .xscreensaver
-rw-r--r--  1 dougie dougie   29899 2007-01-21 22:12 .xsession-errors
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-23
Looks fine now.  Try to run kopete again to see if you still get the same error message as before.

```
kopete
```

---

### Post by DougieFresh4U on 2007-01-23
Thank you as it opened. Now, one other favor-see the iceweasel in all that out put, I would like to install it as it appears to be there, again thanks

---

### Post by taurus on 2007-01-23
```
cd ~/iceweasel-1.5.0.7-g2-i386
ls -la
```

---

### Post by DougieFresh4U on 2007-01-23
Ok, next please:;                                                                                     dougie@DougiesToyBox:~$ cd ~/iceweasel-1.5.0.7-g2-i386
dougie@DougiesToyBox:~/iceweasel-1.5.0.7-g2-i386$ ls -la
total 13524
drwxr-xr-x 13 dougie dougie    4096 2006-10-22 11:26 .
drwxr-xr-x 49 dougie dougie    4096 2007-01-23 10:57 ..
-rwxr-xr-x  1 dougie dougie     101 2006-09-26 07:20 browserconfig.properties
drwxr-xr-x  2 dougie dougie    4096 2006-10-22 11:25 chrome
-rwxr-xr-x  1 dougie dougie    2716 2006-10-22 11:24 chrome.manifest
drwxr-xr-x  3 dougie dougie    4096 2006-10-22 11:25 components
drwxr-xr-x  6 dougie dougie    4096 2006-10-22 11:25 defaults
drwxr-xr-x  4 dougie dougie    4096 2006-10-22 11:25 extensions
drwxr-xr-x  2 dougie dougie    4096 2006-10-22 11:23 greprefs
-rwxr-xr-x  1 dougie dougie    5231 2006-10-22 11:25 iceweasel
-rwxr-xr-x  1 dougie dougie 9937948 2006-10-22 09:47 iceweasel-bin
drwxr-xr-x  2 dougie dougie    4096 2006-10-22 11:25 icons
drwxr-xr-x  2 dougie dougie    4096 2006-10-22 11:25 init.d
-rwxr-xr-x  1 dougie dougie  602140 2006-10-22 07:15 libmozjs.so
-rwxr-xr-x  1 dougie dougie  197480 2006-10-22 07:12 libnspr4.so
-rwxr-xr-x  1 dougie dougie  569903 2006-10-22 09:27 libnss3.so
-rwxr-xr-x  1 dougie dougie  286195 2006-10-22 09:28 libnssckbi.so
-rwxr-xr-x  1 dougie dougie   15788 2006-10-22 07:12 libplc4.so
-rwxr-xr-x  1 dougie dougie    9056 2006-10-22 07:12 libplds4.so
-rwxr-xr-x  1 dougie dougie  187059 2006-10-22 09:28 libsmime3.so
-rwxr-xr-x  1 dougie dougie     476 2006-10-22 09:29 libsoftokn3.chk
-rwxr-xr-x  1 dougie dougie  541373 2006-10-22 09:25 libsoftokn3.so
-rwxr-xr-x  1 dougie dougie  165029 2006-10-22 09:27 libssl3.so
-rwxr-xr-x  1 dougie dougie   95156 2006-10-22 07:20 libxpcom_compat.so
-rwxr-xr-x  1 dougie dougie  647236 2006-10-22 07:20 libxpcom_core.so
-rwxr-xr-x  1 dougie dougie   10264 2006-10-22 07:20 libxpcom.so
-rwxr-xr-x  1 dougie dougie    7832 2006-10-22 09:22 libxpistub.so
-rwxr-xr-x  1 dougie dougie   11468 2006-10-22 09:18 mozilla-xremote-client
drwxr-xr-x  2 dougie dougie    4096 2006-10-22 11:22 plugins
-rwxr-xr-x  1 dougie dougie   31716 2006-10-22 07:20 regxpcom
drwxr-xr-x  8 dougie dougie    4096 2006-10-22 11:23 res
-rwxr-xr-x  1 dougie dougie   10494 2006-10-22 11:25 run-iceweasel.sh
drwxr-xr-x  2 dougie dougie    4096 2006-10-22 11:25 searchplugins
-rwxr-xr-x  1 dougie dougie   82740 2006-10-22 09:48 TestGtkEmbed
-rwxr-xr-x  1 dougie dougie   75784 2006-10-22 09:19 updater
drwxr-xr-x  3 dougie dougie    4096 2006-10-22 11:26 updates
-rwxr-xr-x  1 dougie dougie   20668 2006-10-22 07:27 xpcshell
-rwxr-xr-x  1 dougie dougie   24276 2006-10-22 09:22 xpicleanup
-rwxr-xr-x  1 dougie dougie   74120 2006-10-22 07:13 xpidl
-rwxr-xr-x  1 dougie dougie   27260 2006-10-22 07:13 xpt_dump
-rwxr-xr-x  1 dougie dougie   21528 2006-10-22 07:13 xpt_link
dougie@DougiesToyBox:~/iceweasel-1.5.0.7-g2-i386$

---

### Post by taurus on 2007-01-23
```
./iceweasel
```

---

### Post by DougieFresh4U on 2007-01-23
your the greatest!! Now It's not in my applications>Networking. how do I get it there or should I just make desktop launcher?:grin:

---

### Post by DougieFresh4U on 2007-01-23
ok where did it go:::dougie@DougiesToyBox:~$ ./iceweasel
bash: ./iceweasel: No such file or directory
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-23
```
/iceweasel-1.5.0.7-g2-i386/iceweasel
-or
./iceweasel-1.5.0.7-g2-i386/iceweasel
```
Make a desktop launcher for it since you already have a few on your desktop.

---

### Post by DougieFresh4U on 2007-01-23
The second command worked. But when I close terminal, Iceweasel disapears and then I can not find where to open it again/:confused:

---

### Post by taurus on 2007-01-23
Since you run it from a terminal, exiting that terminal will kill the app too.  The binary for iceweasel is in ~/iceweasel-1.5.0.7-g2-i386/ so you need to specify the path instead of just typing iceweasel at the prompt (UNLESS you are in iceweasel-1.5.0.7-g2-i386 already).

<Alt>F2 -> ./iceweasel-1.5.0.7-g2-i386/iceweasel

---

### Post by DougieFresh4U on 2007-01-23
I am ready to give up and stick with Swiftfox!! Iceweasel wants to have gnash and there is nothing in Applications menu to open Iceweasel and I do not want to use terminal every time to open Iceweasel, thanks for your help

---

### Post by taurus on 2007-01-23
Since you decided to install it by hand, you need to add an entry in the menu yourself or create a launcher on the desktop.  You've got a bunch of launchers on your desktop so create another one shouldn't be a problem but hey, it's up to you since it's your machine.

---

### Post by DougieFresh4U on 2007-01-23
Ok you win:D  I created a launcher. Good! Now I need a flash and it wants to install gnash. I am really not a quitter:lolflag:

---

### Post by taurus on 2007-01-23
Have you already installed flash on your machine?  If you have, just copy the flash plugins to ~/iceweasel-1.5.0.7-g2-i386/iceweasel/plugins.

---

### Post by DougieFresh4U on 2007-01-23
lest we forget I am a dummy-as in how to copy, thank you,

---

### Post by taurus on 2007-01-23
Have you installed flash plugin on your machine at all?

---

### Post by DougieFresh4U on 2007-01-23
> **taurus said:**
> Have you installed flash plugin on your machine at all?

Yes, it;s been in Firefox & Swiftfox, through Automatix long time ago

---

### Post by taurus on 2007-01-23
```
ls -la /usr/lib/firefox/plugins
```

---

### Post by DougieFresh4U on 2007-01-23
dougie@DougiesToyBox:~$ ls -la /usr/lib/firefox/plugins
total 6776
drwxr-xr-x 2 root root    4096 2007-01-23 11:58 .
drwxr-xr-x 5 root root    4096 2007-01-19 12:36 ..
-rwxr-xr-x 1 root root 6904912 2007-01-09 23:24 libflashplayer.so
lrwxrwxrwx 1 root root      29 2007-01-23 11:58 libgnashplugin.so -> ../../gnash/libgnashplugin.so
lrwxrwxrwx 1 root root      39 2007-01-22 14:34 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root      36 2007-01-22 14:30 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root      37 2007-01-22 14:30 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root      34 2007-01-22 14:30 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root      35 2007-01-22 14:30 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root      36 2007-01-22 14:30 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root      37 2007-01-22 14:30 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root      42 2007-01-22 14:30 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root      43 2007-01-22 14:30 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root    8936 2007-01-18 10:24 libunixprintplugin.so
lrwxrwxrwx 1 root root      37 2007-01-14 21:14 libvlcplugin.so -> ../../mozilla/plugins/libvlcplugin.so
lrwxrwxrwx 1 root root      50 2007-01-09 23:23 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-23
```
cp /usr/lib/firefox/plugins/libflashplayer.so  ~/iceweasel-1.5.0.7-g2-i386/iceweasel/plugins
```
Now, launch iceweasel and see if you have flash.

---

### Post by DougieFresh4U on 2007-01-23
> **taurus said:**
> ```
cp /usr/lib/firefox/plugins/libflashplayer.so  ~/iceweasel-1.5.0.7-g2-i386/iceweasel/plugins
```
Now, launch iceweasel and see if you have flash.

NO!                          dougie@DougiesToyBox:~$ cp /usr/lib/firefox/plugins/libflashplayer.so  ~/iceweasel-1.5.0.7-g2-i386/iceweasel/plugins
cp: accessing `/home/dougie/iceweasel-1.5.0.7-g2-i386/iceweasel/plugins': Not a directory
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-23
Sorry.  Got an extra _iceweasel_ in there.

```

cp /usr/lib/firefox/plugins/libflashplayer.so  ~/iceweasel-1.5.0.7-g2-i386/plugins

```

---

### Post by DougieFresh4U on 2007-01-23
> **taurus said:**
> Sorry.  Got an extra _iceweasel_ in there.

```

cp /usr/lib/firefox/plugins/libflashplayer.so  ~/iceweasel-1.5.0.7-g2-i386/plugins

```

No problem. Your doing an excellent job. Flash is working=D> =D> =D>    now one LAST question: how do I make this picture smaller from my digital camera for upload as I want to post something in the "Cafe"?

---

