---
title: "rtorrent error"
date: 2007-03-10
forum: General Help
---

### Post by AngryGnome on 2007-03-10
Hello again.

I installed rtorrent using this HOWTO: 

[http://ubuntuforums.org/showthread.php?t=371275](http://ubuntuforums.org/showthread.php?t=371275)

and whenever I start rtorrent I get this error:  Could not read resource file: ~/.rtorrent.rc

This does not seem to prevent rtorrent from working... but it doesn't detect any changes I make to the rtorrent.rc file... thus I can't change the port and various other options.

There is probably a really obvious answer... but I'm fairly new to linux.

Any help would be appreciated.

---

### Post by konsole on 2007-03-10
> **AngryGnome said:**
> Hello again.

I installed rtorrent using this HOWTO: 

[http://ubuntuforums.org/showthread.php?t=371275](http://ubuntuforums.org/showthread.php?t=371275)

and whenever I start rtorrent I get this error:  Could not read resource file: ~/.rtorrent.rc

This does not seem to prevent rtorrent from working... but it doesn't detect any changes I make to the rtorrent.rc file... thus I can't change the port and various other options.

There is probably a really obvious answer... but I'm fairly new to linux.

Any help would be appreciated.

Have you checked the ownership and permissions of the rc file?

---

### Post by AngryGnome on 2007-03-11
It's not permissions... I just don't think rtorrent can find the file... but i don't know where to put it where it could.

---

### Post by Kateikyoushi on 2007-03-11
Do you have in in ~/ ? Please post the output of this command.

```
 ls -a ~/
```

---

### Post by AngryGnome on 2007-03-11
This is what I get with that command:

```
.
..
.armagetron
.automatix
.bash_history
.bash_logout
.bash_profile
.bashrc
.BitTornado
block.cfg
Blues Traveler - Roseland, NYC 10-31-91 SDB A+
.config
.dc
.dc++
.dctc
Desktop
.dmrc
Downloads
Downloadszorro - 02 - flash flood.avi.4LYWVW7AMRYMI7SMJ7W4UHKVIIJWOFERXX37I6I.dctmp
.esd_auth
.evolution
.exaile
Examples
.fonts.cache-1
.gaim
.gconf
.gconfd
.gdesklets
.gftp
.gimp-2.2
.gksu.lock
.gnome
.gnome2
.gnome2_private
.grip
.grip-flac
.grip-oggenc
.gstreamer-0.10
.gtk-bookmarks
.gtkrc-1.2-gnome2
hubs_fav.cfg
.ICEauthority
.icons
Incompletes.txt
.irssi
jamshub
jamshub~
.java
jericho.s01e14.hr.hdtv.ac3.5.1.xvid-nbs.avi
libtorrent-0.11.1
libtorrent-0.11.1.tar.gz
.local
.lopster
.macromedia
.metacity
.mozilla
Music
.nautilus
.openoffice.org2
.qt
queues.cfg
.recently-used
.recently-used.xbel
rtorrent-0.7.1
rtorrent-0.7.1.tar.gz
settings.txt
Settings.xml
sleeperbanlist
.sudo_as_admin_successful
.themes
.thumbnails
Torrent Files
.Trash
.tsclient
.update-manager
.update-notifier
.vlc
Wallpapers
.windows-label
.wine
.Xauthority
.xchat2
.xine
.xsession-errors
```

---

### Post by Kateikyoushi on 2007-03-11
You do not have the .rtorrent.rc file in the ~/directory so it can not be found by rtorrent.

---

### Post by chomafin on 2007-03-13
> **AngryGnome said:**
> This is what I get with that command:

```
.
...
.recently-used
.recently-used.xbel
rtorrent-0.7.1
rtorrent-0.7.1.tar.gz
settings.txt
... 
```

It seems the default install does not include the rtorrent settings.  If you go to the official website of libtorrent, there is a default .rtorrent.rc file.  Just grab and edit that to your likeing.  The rtorrent.rc file is pretty easy to follow w/ the comments, and if not check the FAQ [http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide)

To get the Default settings, this *should* work.: 
```

cd ~/
wget http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest
mv rtorrent.rc\?rev\=latest .rtorrent.rc

```and then to Edit the settings of rTorrent, 
```

gedit ~/.rtorrent.rc

```

---

