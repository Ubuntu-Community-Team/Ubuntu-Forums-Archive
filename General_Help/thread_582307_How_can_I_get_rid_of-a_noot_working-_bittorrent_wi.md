---
title: "How can I get rid of-a noot working- bittorrent without loosing ubuntu-desktop..."
date: 2007-10-19
forum: General Help
---

### Post by offline on 2007-10-19
I clean-installed _feisty_, did an update and then installed some programs from the repositories.

One of them was [COLOR="DarkRed"]bittorrent[/COLOR]. But in the end

1)There is no entry in any menu
2)Can't run from the terminal or alt+F2 (bittorrent)
3)The installed parts are:

```
/var/lib/bittorrent
/var/log/bittorrent
/usr/share/doc/bash/completion-contrib/bittorrent
/usr/lib/mime/packages/bittorrent
/usr/share/bittorrent
/usr/share/doc/bittorrent
/usr/share/pycentral/python-bittorrent/site-packages/BitTorrent
/usr/lib/python2.5/site-packages/BitTorrent
/usr/share/man/man1/bittorrent-downloader.bittorrent.1.gz
/usr/lib/python2.5/site-packages/BitTorrent.egg-info
/usr/share/pycentral/python-bittorrent/site-packages/BitTorrent.egg-info
/var/lib/dpkg/info/bittorrent.list
/usr/share/doc/bittorrent/bittorrent_logo.png
/var/lib/dpkg/info/bittorrent.md5sums
/usr/share/man/man1/bittorrent-multi-downloader.bittorrent.1.gz
/var/lib/dpkg/info/bittorrent.postinst
/var/lib/dpkg/info/bittorrent.postrm
/var/lib/dpkg/info/bittorrent.prerm
/usr/bin/btcompletedir.bittorrent
/usr/share/man/man1/btcompletedir.bittorrent.1.gz
/usr/bin/btdownloadcurses.bittorrent
/usr/share/man/man1/btdownloadcurses.bittorrent.1.gz
/usr/bin/btdownloadheadless.bittorrent
/usr/share/man/man1/btdownloadheadless.bittorrent.1.gz
/usr/bin/btlaunchmany.bittorrent
/usr/share/man/man1/btlaunchmany.bittorrent.1.gz
/usr/bin/btlaunchmanycurses.bittorrent
/usr/share/man/man1/btlaunchmanycurses.bittorrent.1.gz
/usr/bin/btmakemetafile.bittorrent
/usr/share/man/man1/btmakemetafile.bittorrent.1.gz
/usr/bin/btreannounce.bittorrent
/usr/share/man/man1/btreannounce.bittorrent.1.gz
/usr/bin/btrename.bittorrent
/usr/share/man/man1/btrename.bittorrent.1.gz
/usr/bin/btshowmetainfo.bittorrent
/usr/share/man/man1/btshowmetainfo.bittorrent.1.gz
/usr/bin/bttrack.bittorrent
/usr/share/man/man1/bttrack.bittorrent.1.gz
/usr/share/doc/python-bittorrent
/usr/share/pycentral/python-bittorrent
/var/lib/dpkg/info/python-bittorrent.list
/var/lib/dpkg/info/python-bittorrent.md5sums
/var/lib/dpkg/info/python-bittorrent.postinst
/var/lib/dpkg/info/python-bittorrent.prerm
/usr/share/mime/application/x-bittorrent.xml
    
```

4)In /usr/bin if I remember well  there are many bt entries but nothing executable I suppose:

```
btflash
btcompletedir
btcompletedir.bittorrent
btcompletedirgui
btcompletedirgui.bittorrent
btdownloadcurses
btdownloadcurses.bittorrent
btdownloadgui
etc, etc...
```

5)At usr/bin/share there is an empty file called bittorrent

6)AT Synaptic after a reinstallation it continues to be shown as nicely installed(**bittorrent and bittorrent-gui**)

7)I [COLOR="DarkRed"]can't uninstall[/COLOR] with synaptic because with bittorent, 

[B]gnome-btdownload and
ubuntu-desktop[/B]

[COLOR="DarkRed"]will vanish![/COLOR]

If you can give me any instruction either

to find a way to use bittorrent
or completely uninstall without loosing desktop and such.

(I installed bittornado and amule with no problems(synaptic)  just to be sure that this kind of apps installs well)

Thank you.

---

### Post by por100pre1 on 2007-10-19
```
gnome-btdownload
```

is the command for Bittorrent.

Try [Deluge]("http://deluge-torrent.org/downloads").

---

### Post by offline on 2007-10-20
> **por100pre1 said:**
> ```
gnome-btdownload
```

is the command for Bittorrent.

.

I typed :

```
gnome-btdownload
```

but nautilous came up searching some sort of bit torrent meta file and showing me nothing(desktop, etc)

This was the error output of terminal:

```
GtkDeprecionWarning: gtkthreads-init is depreciated, use gtk.gdk.threads-init instead
```...

:confused:

---

### Post by offline on 2007-10-20
I wanted-at least for now- a clean machine not some parts spill over all over the place

---

### Post by LanDan on 2007-10-20
bittorrent is not with a GUI but so it will not show up in your menu, it is however used by programns such as gnome-btdownload (only shows if you open a .torrent file) or bittornade-gui or azuereas.


if you want to remove old dependencies simply type 
sudo apt-get autoremove (dont know if its in synaptic)

---

### Post by offline on 2007-10-20
> **LanDan said:**
> bittorrent is not with a GUI but so it will not show up in your menu

Yes but I have downloaded both bittorrent and bittorrent-gui

---

