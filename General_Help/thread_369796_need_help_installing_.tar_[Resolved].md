---
title: "need help installing .tar [Resolved]"
date: 2007-02-25
forum: General Help
---

### Post by DougieFresh4U on 2007-02-25
Can some one please guide me on installing this: "xfmedia-0.9.2.tar.bz2" I never have any luck with tar files, thanks

---

### Post by taurus on 2007-02-25
```
tar xvjf xfmedia-0.9.2.tar.bz2
cd xfmedia-0.9.2
```
And either look at the README or INSTALL.

```
more INSTALL
```

---

### Post by DougieFresh4U on 2007-02-25
> **taurus said:**
> ```
tar xvjf xfmedia-0.9.2.tar.bz2
cd xfmedia-0.9.2
```
And either look at the README or INSTALL.

```
more INSTALL
```

Sorry for being a dumb_ss, but I can not open the read me or install

---

### Post by taurus on 2007-02-25
You see the second icon that says Open.  There should be an INSTALL as well so you actually want to read that.  Just highlight it and click Open.  However, looks like you have to build it so open a terminal, change to that new directory with the **cd** command, and run

```
sudo aptitude update
sudo aptitude install build-essential checkinstall
./configure
make
sudo make checkinstall
```

---

### Post by DougieFresh4U on 2007-02-25
Can't do it

---

### Post by taurus on 2007-02-25
Can you at least try to do it from a terminal?

```
cd /tmp/xfmedia-0.9.2
more INSTALL
```
In case you forget since we went through this before, everything in /tmp will be gone if you reboot your machine so don't be surprise if you can't find your xfmedia-0.9.2 there anymore the next time you boot your machine.  ;)

---

### Post by DougieFresh4U on 2007-02-25
> **taurus said:**
> Can you at least try to do it from a terminal?

```
cd /tmp/xfmedia-0.9.2
more INSTALL
```
In case you forget since we went through this before, everything in /tmp will be gone if you reboot your machine so don't be surprise if you can't find your xfmedia-0.9.2 there anymore the next time you boot your machine.  ;)

I'm trying my best:::dougie@DougiesToyBox:/tmp/xfmedia-0.9.2$ sudo aptitude install build-essential checkinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
dougie@DougiesToyBox:/tmp/xfmedia-0.9.2$ ./configure
bash: ./configure: No such file or directory
dougie@DougiesToyBox:/tmp/xfmedia-0.9.2$

---

### Post by taurus on 2007-02-25
What's the output of this command then?

```
ls -la
```

---

### Post by DougieFresh4U on 2007-02-25
> **taurus said:**
> What's the output of this command then?

```
ls -la
```

dougie@DougiesToyBox:~$ ls -la
total 2388
drwxr-xr-x 68 dougie dougie   4096 2007-02-25 00:37 .
drwxr-xr-x  3 root   root     4096 2007-01-09 21:56 ..
drwxr-xr-x  3 dougie dougie   4096 2007-01-15 23:44 .adobe
drwx------  4 dougie dougie   4096 2007-02-07 07:35 .aim
drwx------  8 dougie dougie   4096 2007-02-16 08:04 .amsn
drwx------  2 dougie dougie   4096 2007-01-12 01:33 amsn_received
-rw-r--r--  1 dougie dougie    283 2007-01-16 01:51 .audacity
drwxr-xr-x  2 dougie root     4096 2007-01-09 23:30 .automatix
-rw-------  1 dougie dougie  14547 2007-02-25 01:05 .bash_history
-rw-r--r--  1 dougie dougie    220 2007-01-09 21:56 .bash_logout
-rw-r--r--  1 dougie dougie    414 2007-01-09 21:56 .bash_profile
-rw-r--r--  1 dougie dougie   2227 2007-01-09 21:56 .bashrc
drwxr-xr-x  4 dougie dougie   4096 2007-01-10 02:24 .bmp
drwx------  5 dougie dougie   4096 2007-01-10 04:22 .cache
drwx------  8 dougie dougie   4096 2007-02-08 17:53 .config
-rw-r--r--  1 dougie dougie     39 2007-02-15 00:31 .current-song
-rw-r--r--  1 dougie dougie     60 2007-02-23 18:11 .DCOPserver_DougiesToyBox__0
lrwxrwxrwx  1 dougie dougie     41 2007-02-16 11:00 .DCOPserver_DougiesToyBox_:0 -> /home/dougie/.DCOPserver_DougiesToyBox__0
drwx------  2 dougie dougie   4096 2007-02-24 23:52 Desktop
-rw-r--r--  1 dougie dougie     24 2007-01-09 22:12 .dmrc
drwx------  2 dougie games    4096 2007-02-18 23:26 .emilia
drwxr-xr-x  5 dougie dougie   4096 2007-02-22 20:44 .exaile
lrwxrwxrwx  1 dougie dougie     26 2007-01-09 21:56 Examples -> /usr/share/example-content
drwxr-xr-x  2 dougie dougie   4096 2007-02-17 21:54 .fblevels
-rw-r--r--  1 dougie dougie   1197 2007-02-17 21:53 .fbrc
drwxr-xr-x  2 dougie dougie   4096 2007-02-23 17:51 .fontconfig
-rw-r--r--  1 dougie dougie 483359 2007-01-09 23:12 .fonts.cache-1
drwxr-xr-x  4 dougie dougie   4096 2007-02-14 08:27 .frostwire
drwx------  6 dougie dougie   4096 2007-02-23 10:53 .gaim
drwxr-xr-x  9 dougie dougie   4096 2007-02-04 18:46 gaim-2.0.0beta6
drwx------  5 dougie dougie   4096 2007-02-24 19:13 .gconf
drwx------  2 dougie dougie   4096 2007-02-25 01:05 .gconfd
drwxr-xr-x 21 dougie dougie   4096 2007-02-19 10:17 .gimp-2.2
-rw-r-----  1 dougie dougie      0 2007-02-25 00:12 .gksu.lock
drwxr-xr-x  4 dougie dougie   4096 2007-02-19 15:02 .gnome
drwx------  8 dougie dougie   4096 2007-02-24 19:13 .gnome2
drwx------  2 dougie dougie   4096 2007-01-09 23:37 .gnome2_private
-rw-r--r--  1 dougie dougie   4254 2007-02-18 21:18 .gnumericrc
drwx------  2 dougie dougie   4096 2007-01-09 22:48 .gnupg
drwx------  3 dougie dougie   4096 2007-01-23 11:20 .gnuzilla
drwx------  4 dougie dougie   4096 2007-02-24 23:24 .googleearth
drwxr-xr-x  9 dougie dougie   4096 2007-02-19 15:02 google-earth
drwxr-xr-x  5 dougie dougie   4096 2007-02-17 06:55 .gqview
drwxr-xr-x  2 dougie dougie   4096 2007-02-23 10:30 .gstreamer-0.10
drwxr-xr-x  5 dougie dougie   4096 2007-02-08 18:15 .gtkboard
drwx------  2 dougie dougie   4096 2007-01-16 01:53 .gxine
-rw-------  1 dougie dougie    267 2007-02-08 17:27 .hplip.conf
-rw-r--r--  1 dougie dougie      0 2007-02-04 23:19 .hwdb
-rw-------  1 dougie dougie   9083 2007-02-23 18:11 .ICEauthority
drwxr-xr-x 13 dougie dougie   4096 2007-01-23 13:02 iceweasel-1.5.0.7-g2-i386
drwxr-xr-x  2 dougie dougie   4096 2007-01-09 23:51 .icons
drwxr-xr-x  2 dougie dougie   4096 2007-02-19 23:18 Incomplete
drwxr-xr-x  4 dougie dougie   4096 2007-02-17 19:53 .java
drwx------  3 dougie dougie   4096 2007-01-10 02:22 .kde
-rw-r--r--  1 dougie dougie   1730 2007-01-07 16:34 key.gpg.asc
-rw-------  1 root   root       35 2007-02-04 18:48 .lesshst
lrwxrwxrwx  1 root   root       40 2007-02-04 21:26 libstdc++-libc6.1-1.so.2 -> /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so
drwxr-xr-x  4 dougie dougie   4096 2007-02-20 07:00 .listen
drwxr-xr-x  3 dougie dougie   4096 2007-01-09 22:12 .local
drwx------  3 dougie dougie   4096 2007-02-19 15:02 .loki
drwxr-xr-x  8 dougie dougie   4096 2007-02-20 06:57 .lyrics
drwx------  3 dougie dougie   4096 2007-01-09 23:56 .macromedia
drwxr-xr-x  2 dougie dougie   4096 2007-01-24 03:09 .Mah_MahJong-1.0
drwxr-xr-x  3 dougie dougie   4096 2007-01-10 15:56 .mcop
-rw-------  1 dougie dougie     31 2007-02-18 23:26 .mcoprc
-rw-r--r--  1 dougie dougie    340 2007-02-11 04:18 .mime.types
drwx------  3 dougie dougie   4096 2007-01-10 01:58 .mozilla
drwx------  3 dougie dougie   4096 2007-01-10 01:58 .mozilla-thunderbird
drwxr-xr-x  2 dougie dougie   4096 2007-01-14 19:30 .mplayer
drwxr-xr-x  2 dougie dougie   4096 2007-02-11 04:18 MyMusic
drwxr-xr-x  2 dougie dougie   4096 2007-01-16 01:48 NewName
-rw-r--r--  1 dougie dougie   5120 2007-01-24 12:44 .OpenYahtzee
drwxr-xr-x  2 dougie dougie   4096 2007-01-16 05:16 Podcasts
drwxr-xr-x  2 dougie dougie   4096 2007-02-23 18:11 .qt
-rw-r--r--  1 dougie dougie   9044 2007-02-17 22:13 .recently-used.xbel
-rw-------  1 root   root     1024 2007-02-14 14:07 .rnd
drwxr-xr-x  2 dougie dougie   4096 2007-02-19 17:13 .sdljump
drwxr-xr-x  2 dougie dougie   4096 2007-02-19 23:17 Shared
-rw-r--r--  1 dougie dougie 172596 2007-02-23 18:11 snapshot36.png
-rw-r--r--  1 dougie dougie 193639 2007-02-25 00:19 snapshot37.png
-rw-r--r--  1 dougie dougie 224031 2007-02-25 00:37 snapshot38.png
-rw-r--r--  1 dougie dougie 224031 2007-02-25 00:37 snapshot39.png
drwxr-xr-x  5 dougie dougie   4096 2007-01-16 01:00 src
drwx------  2 dougie dougie   4096 2007-01-24 02:30 .ssh
drwxr-xr-x  3 dougie dougie   4096 2007-02-15 09:25 .streamtuner
-rw-r--r--  1 dougie dougie      0 2007-01-09 22:13 .sudo_as_admin_successful
-rw-r--r--  1 dougie dougie 492997 2007-01-13 08:47 Swiftfox_wallpaper.png
drwxr-xr-x  5 dougie dougie   4096 2007-01-24 10:23 .thumbnails
drwx------  2 dougie dougie   4096 2007-02-17 19:41 .tomatoes
drwxr-xr-x  2 dougie dougie   4096 2007-01-09 22:18 .update-manager
drwx------  2 dougie dougie   4096 2007-01-29 01:32 .update-notifier
drwxr-xr-x  4 root   root     4096 2003-01-10 11:16 usr
drwxr-xr-x  3 dougie dougie   4096 2007-01-18 05:25 .vlc
drwxr-xr-x  2 dougie dougie   4096 2007-01-24 11:11 .wapi
drwxr-xr-x  4 dougie dougie   4096 2007-02-24 23:52 .wine
-rw-------  1 dougie dougie    124 2007-02-23 17:51 .Xauthority
drwxr-xr-x  2 dougie dougie   4096 2007-01-10 04:28 .xine
drwxr-xr-x  4 dougie dougie   4096 2007-01-11 03:52 .xmms
drwx------  5 dougie dougie   4096 2007-02-19 19:37 .xmoto
-rw-r--r--  1 dougie dougie  11416 2007-01-09 23:47 .xscreensaver
-rw-r--r--  1 dougie dougie 200067 2007-02-24 23:29 .xsession-errors
drwx------  3 dougie dougie   4096 2007-02-11 04:18 .zinf

---

### Post by taurus on 2007-02-25
How come you keep moving back to your $HOME directory when you want to build xfmedia which is in /tmp?

```
cd /tmp/xfmedia-0.9.2
ls -la
```

---

### Post by DougieFresh4U on 2007-02-25
> **taurus said:**
> How come you keep moving back to your $HOME directory when you want to build xfmedia which is in /tmp?

```
cd /tmp/xfmedia-0.9.2
ls -la
```

dougie@DougiesToyBox:/tmp/xfmedia-0.9.2$ ls -la
total 24
drwxr-xr--  2 dougie dougie 4096 2007-02-25 00:36 .
drwxrwxrwt 12 root   root   4096 2007-02-25 01:05 ..
-rw-r--r--  1 dougie dougie 9240 2006-11-27 02:21 INSTALL
-rw-r--r--  1 dougie dougie 2079 2006-11-27 02:21 README
dougie@DougiesToyBox:/tmp/xfmedia-0.9.2$

---

### Post by aysiu on 2007-02-25
Do you really need 0.9.2? 0.9.1 is in the repositories and can be installed easily (if you have the Universe repositories enabled) with one command ```
sudo apt-get update && sudo apt-get install xfmedia
```

---

### Post by DougieFresh4U on 2007-02-25
> **aysiu said:**
> Do you really need 0.9.2? 0.9.1 is in the repositories and can be installed easily (if you have the Universe repositories enabled) with one command ```
sudo apt-get update && sudo apt-get install xfmedia
```

Wow! that was easy, thanks

---

