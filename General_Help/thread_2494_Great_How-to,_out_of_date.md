---
title: "Great How-to, out of date"
date: 2004-10-28
forum: General Help
---

### Post by jcscar on 2004-10-28
I was doing the multamedia how to at:  [http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94)

However once I hit this line I started running into errors.
 $ sudo apt-get install libpng-dev

At this point it told me to pick a certain package, So I skipped it and went to the next. The next just sat there, like it could not locate the server to download from..  I read all the replies on the first page of about 5 and none mentioned this (probably all old).. Is there a new how to?




Have your Warty Warthog CD handy and accept any extra packages, e.g. the
libtool install will also install gcc. We'll use a US mirror for the
MPlayer packages and assume you're working in your home directory. Download
MPlayer, codecs, English fonts and the default blue skin.
Internationalization and slick graphics are up to you.

$ wget [http://ftp3.mplayerhq.hu/MPlayer/re...1.0pre5.tar.bz2](http://ftp3.mplayerhq.hu/MPlayer/re...1.0pre5.tar.bz2)
$ wget [http://ftp3.mplayerhq.hu/MPlayer/re...0040922.tar.bz2](http://ftp3.mplayerhq.hu/MPlayer/re...0040922.tar.bz2)
$ wget [http://ftp3.mplayerhq.hu/MPlayer/re...-8859-1.tar.bz2](http://ftp3.mplayerhq.hu/MPlayer/re...-8859-1.tar.bz2)
$ wget [http://ftp3.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2](http://ftp3.mplayerhq.hu/MPlayer/Skin/Blue-1.4.tar.bz2)

Using the README from mplayerhq.hu [3] as a baseline, install the codecs
with the following commands.

$ tar -xjf essential-20040922.tar.bz2
$ sudo mkdir -p /usr/local/lib/codecs
$ sudo cp essential-20040922/* /usr/local/lib/codecs/

Time to compile MPlayer. Issue these commands.

$ tar -xjf MPlayer-1.0pre5.tar.bz2
$ cd MPlayer-1.0pre5
$ ./configure --enable-gui
$ make
$ sudo make install

Now install the fonts and skin.

$ cd
$ tar -xjf font-arial-iso-8859-1.tar.bz2
$ sudo cp font-arial-iso-8859-1/font-arial-14-iso-8859-1/* /usr/local/share/mplayer/font/
$ tar -xjf Blue-1.4.tar.bz2
$ sudo mkdir -p /usr/local/share/mplayer/Skin/default
$ sudo cp -r Blue/* /usr/local/share/mplayer/Skin/default/

Finally, copy over the included conf files.

$ sudo cp MPlayer-1.0pre5/etc/* /usr/local/etc/mplayer/

Test your install by launching the graphical version of MPlayer.

$ gmplayer

QuickTime, WindowsMedia, MPEG, avi - you should be able to play just about
anything. Give yourself quick access to MPlayer by adding a launcher to
the top GNOME panel. Right click on the panel and click Add to Panel...
Select Custom Application Launcher and click Add. Use the following
information and click OK.

Name: MPlayer
Command: /usr/local/bin/gmplayer
Icon: /usr/local/share/mplayer/Skin/default/icons/32x32.png

---

### Post by jdong on 2004-10-28
Please reply to the original author about the problem, and make sure you give detailed error messages.

I'm locking this thread because the "fix" to the problem should go in the HOWTO's thread. Continue discussion at [the original thread](http://www.ubuntuforums.org/showthread.php?t=94)

---

