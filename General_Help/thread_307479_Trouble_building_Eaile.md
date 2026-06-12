---
title: "Trouble building Eaile"
date: 2006-11-26
forum: General Help
---

### Post by DougieFresh4U on 2006-11-26
I am following the How-To on installing Exaile. In following the How-To and getting the error I'm posting, how can there not be directory when how to is making the directory. I think I am confused. If you need more info please ask. thanks                                        dougie@DougiesToyBox:~$ cd exaile*
bash: cd: exaile_0.2.5.tar.gz: Not a directory
dougie@DougiesToyBox:~$ make
make: *** No targets specified and no makefile found.  Stop.
dougie@DougiesToyBox:~$

---

### Post by ~LoKe on 2006-11-26
```
cd exaile_0.2.5 && make && sudo make install
```

---

### Post by DougieFresh4U on 2006-11-26
dougie@DougiesToyBox:~$ cd exaile_0.2.5 && make && sudo make install
bash: cd: exaile_0.2.5: No such file or directory
dougie@DougiesToyBox:~$ 
should I start at the beginning again? Also the How-To mentions a second way to install and I basically get the error

---

### Post by ~LoKe on 2006-11-26
Looks like you never extracted the tarball.

```
ls
```
See if **exaile_0.2.5.tar.gz** is in that list.  If it is, then..
```
tar xf exaile*.gz
```
If that is successful, then continue...
```
cd exaile* && make && sudo make install
```

---

### Post by DougieFresh4U on 2006-11-26
Thanks ~LoKe, gonna post my terminal from beginning and maybe you can see which step is failing for me,back in a few

---

### Post by DougieFresh4U on 2006-11-26
dougie@DougiesToyBox:~$ wget [http://exaile.org/files/exaile_0.2.6.tar.gz](http://exaile.org/files/exaile_0.2.6.tar.gz)
--18:28:55--  [http://exaile.org/files/exaile_0.2.6.tar.gz](http://exaile.org/files/exaile_0.2.6.tar.gz)
           => `exaile_0.2.6.tar.gz.1'
Resolving exaile.org... 64.251.22.233
Connecting to exaile.org|64.251.22.233|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 291,850 (285K) [application/x-tar]

100%[====================================>] 291,850       53.98K/s    ETA 00:00

18:29:21 (53.32 KB/s) - `exaile_0.2.6.tar.gz.1' saved [291850/291850]

dougie@DougiesToyBox:~$ tar xvfz exaile_0.2.6.tar.gz
exaile_0.2.6/
exaile_0.2.6/debian/
exaile_0.2.6/debian/changelog
exaile_0.2.6/debian/control
exaile_0.2.6/debian/compat
exaile_0.2.6/debian/menu
exaile_0.2.6/debian/watch
exaile_0.2.6/debian/README.Debian
exaile_0.2.6/debian/copyright
exaile_0.2.6/debian/docs
exaile_0.2.6/debian/rules
exaile_0.2.6/xl/
exaile_0.2.6/xl/dbusinterface.py
exaile_0.2.6/xl/common.py
exaile_0.2.6/xl/shoutcast.py
exaile_0.2.6/xl/trackslist.py
exaile_0.2.6/xl/__init__.py
exaile_0.2.6/xl/media.py
exaile_0.2.6/xl/prefs.py
exaile_0.2.6/xl/audioscrobbler.py
exaile_0.2.6/xl/xlmisc.py
exaile_0.2.6/xl/covers.py
exaile_0.2.6/xl/panels.py
exaile_0.2.6/xl/config.py
exaile_0.2.6/xl/track.py
exaile_0.2.6/xl/tracks.py
exaile_0.2.6/xl/db.py
exaile_0.2.6/exaile.desktop
exaile_0.2.6/package.py
exaile_0.2.6/exaile.glade
exaile_0.2.6/scripts/
exaile_0.2.6/scripts/exaile_xchat.pl
exaile_0.2.6/scripts/exaile_irssi.pl
exaile_0.2.6/changelog
exaile_0.2.6/sql/
exaile_0.2.6/sql/db.sql
exaile_0.2.6/sql/changes0001.sql
exaile_0.2.6/sql/changes0002.sql
exaile_0.2.6/sql/changes0003.sql
exaile_0.2.6/TODO
exaile_0.2.6/exaile.py
exaile_0.2.6/merge
exaile_0.2.6/exaile.gladep
exaile_0.2.6/license.txt
exaile_0.2.6/mmkeys/
exaile_0.2.6/mmkeys/mmkeys.override
exaile_0.2.6/mmkeys/mmkeys.defs
exaile_0.2.6/mmkeys/mmkeys.c
exaile_0.2.6/mmkeys/COPYING
exaile_0.2.6/mmkeys/mmkeys.h
exaile_0.2.6/mmkeys/mmkeysmodule.c
exaile_0.2.6/mmkeys/Makefile
exaile_0.2.6/mmkeys/README
exaile_0.2.6/images/
exaile_0.2.6/images/largeicon.png
exaile_0.2.6/images/genre.png
exaile_0.2.6/images/playlist.png
exaile_0.2.6/images/default_theme/
exaile_0.2.6/images/default_theme/go-forward.png
exaile_0.2.6/images/default_theme/remove.png
exaile_0.2.6/images/default_theme/refresh.png
exaile_0.2.6/images/default_theme/go-back.png
exaile_0.2.6/images/default_theme/media-pause.png
exaile_0.2.6/images/default_theme/clear.png
exaile_0.2.6/images/default_theme/gnome-fs-directory-accept.png
exaile_0.2.6/images/default_theme/gnome-dev-ipod.png
exaile_0.2.6/images/default_theme/stock_volume.png
exaile_0.2.6/images/default_theme/gnome-fs-directory.png
exaile_0.2.6/images/default_theme/media-play.png
exaile_0.2.6/images/default_theme/gnome-dev-cdrom-audio.png
exaile_0.2.6/images/default_theme/go-up.png
exaile_0.2.6/images/default_theme/add.png
exaile_0.2.6/images/default_theme/media-previous.png
exaile_0.2.6/images/default_theme/media-next.png
exaile_0.2.6/images/default_theme/gnome-globe.png
exaile_0.2.6/images/track.png
exaile_0.2.6/images/close.png
exaile_0.2.6/images/artist.png
exaile_0.2.6/images/icon.xpm
exaile_0.2.6/images/nocover.png
exaile_0.2.6/images/media-audiofile.png
exaile_0.2.6/images/exailelogo-sml.png
exaile_0.2.6/images/trayicon.png
exaile_0.2.6/images/icon.png
exaile_0.2.6/images/exailelogo.png
exaile_0.2.6/images/splash.png
exaile_0.2.6/images/ipod.png
exaile_0.2.6/checklist
exaile_0.2.6/exaile.1
exaile_0.2.6/exaile
exaile_0.2.6/po/
exaile_0.2.6/po/de_DE/
exaile_0.2.6/po/de_DE/LC_MESSAGES/
exaile_0.2.6/po/de_DE/LC_MESSAGES/de_DE.mo
exaile_0.2.6/po/zh_CN/
exaile_0.2.6/po/zh_CN/LC_MESSAGES/
exaile_0.2.6/po/zh_CN/LC_MESSAGES/exaile.mo
exaile_0.2.6/po/messages.pot
exaile_0.2.6/po/sv.po
exaile_0.2.6/po/sv/
exaile_0.2.6/po/sv/LC_MESSAGES/
exaile_0.2.6/po/sv/LC_MESSAGES/exaile.mo
exaile_0.2.6/po/pl.po
exaile_0.2.6/po/pl/
exaile_0.2.6/po/pl/LC_MESSAGES/
exaile_0.2.6/po/pl/LC_MESSAGES/exaile.mo
exaile_0.2.6/po/es_ES.po
exaile_0.2.6/po/es_ES/
exaile_0.2.6/po/es_ES/LC_MESSAGES/
exaile_0.2.6/po/es_ES/LC_MESSAGES/exaile.mo
exaile_0.2.6/po/createpot.py
exaile_0.2.6/po/de_DE.po
exaile_0.2.6/po/zh_CN.po
exaile_0.2.6/Makefile
dougie@DougiesToyBox:~$ sudo apt-get install build-essential dpkg-dev debhelper libgstreamer0.10-0 gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly python-gst0.10 gstreamer0.10-esd gstreamer0.10-alsa python2.4 python2.4-dev python2.4-gtk2 python-gtk2-dev python-glade2 python2.4-dbus python-pyvorbis python-mutagen python-pysqlite2 python-elementtree python2.4-gnome2-extras python-cddb streamripper
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
dpkg-dev is already the newest version.
debhelper is already the newest version.
libgstreamer0.10-0 is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
python-gst0.10 is already the newest version.
gstreamer0.10-esd is already the newest version.
gstreamer0.10-alsa is already the newest version.
python2.4 is already the newest version.
python2.4-dev is already the newest version.
Note, selecting python-gtk2 instead of python2.4-gtk2
python-gtk2 is already the newest version.
python-gtk2-dev is already the newest version.
python-glade2 is already the newest version.
Note, selecting python-dbus instead of python2.4-dbus
python-dbus is already the newest version.
python-pyvorbis is already the newest version.
python-mutagen is already the newest version.
python-pysqlite2 is already the newest version.
python-elementtree is already the newest version.
Note, selecting python-gnome2-extras instead of python2.4-gnome2-extras
python-gnome2-extras is already the newest version.
python-cddb is already the newest version.
streamripper is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dougie@DougiesToyBox:~$ cd exaile*
bash: cd: exaile_0.2.5.tar.gz: Not a directory
dougie@DougiesToyBox:~$

---

### Post by taurus on 2006-11-26
You just unpacked it so it is now exaile_0.2.6.

```
cd exaile_0.2.6
```
Then

```
./exaile
```

---

### Post by ~LoKe on 2006-11-26
```
cd exaile_0.2.6 && make && sudo make install
```

---

### Post by DougieFresh4U on 2006-11-26
Thanks !LoKe & taurus, than did the trick,so I typed in exaile and it popped open and terminal did the following, can I close terminal as it doesn' look like it's finished  <<<< dougie@DougiesToyBox:~/exaile_0.2.6$ exaile
mmkeys are available.
loading tracks...
done loading tracks...
loading songs
Clearing tracks cache

---

### Post by ~LoKe on 2006-11-26
Close the terminal.  I suggest not running applications directly from the terminal, because you lose use of it unless you put an ampersand at the end, ex. **exaile &** and you'll still be able to use your terminal.  However, it may echo messages every now and then.  So...I would suggest running it from the applications menu or alt+F2.

---

### Post by DougieFresh4U on 2006-11-26
Thank both and I'm good to go. I shall mark solved

---

### Post by ~LoKe on 2006-11-26
No problem.  In the future I would suggest looking around for a .deb file to make installation easier.  There is one available for Exaile, but I wanted you to know how to build from source.  It's good practice, but you should do it another way from now on, to make things cleaner.  This is how I would have done it...
```
sudo apt-get install checkinstall && tar xf exaile*.gz && cd exaile* && make && sudo checkinstall
```

---

