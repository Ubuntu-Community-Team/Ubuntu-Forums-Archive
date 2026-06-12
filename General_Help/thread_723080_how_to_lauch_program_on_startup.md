---
title: "how to lauch program on startup ?"
date: 2008-03-13
forum: General Help
---

### Post by Jethro_uk on 2008-03-13
Hi guys,

I'm trying to create a download server, which will be fairly inaccessible (in the loft). I'm experimenting with NXclient to control it, which seems to be working OK. However, one of my requirements is that in the event of a power failure, when the machine restarts, it carries on where it left off.

IIUC, the the NXClient session will restart automatically. However, the applications running don't. Well, the gnome-torrent app, which is my main concern. I tried using the "sessions" tool to remember running apps, but that just caused the torrent app to pop up, looking for the .torrent file.

Now coming from a windows backgound, it should be possible to put the .torrent file in a "startup" folder, which would cause the associated app to be lauched automatically ?

DOes this make sense, and if so, how would I go about it ?

thanks in advance

---

### Post by BlowflyBob on 2008-03-13
Sytem -> Preferences -> Session is pretty much the equivalent of the startup folder.

You can add launchers there for programs you want to launch, not sure about files.

Though, I would recomment looking at rTorrent and its documentation if you are primarily wanting it to download torrents. It has the ability to watch a folder and automatically start .torrent files that it finds there. [http://libtorrent.rakshasa.no/](http://libtorrent.rakshasa.no/)

---

### Post by Arthur Archnix on 2008-03-13
I think for this purpose you should look into rtorrent and deluge, both of which can actively scan folders and be remotely administered.

So, when you want to add a torrent you just copy the file to /remove/box/torrents and either rtorrrent or deluge sees it and starts it. When its done then can also then move the file to some other location, perhaps on your local machine.

---

