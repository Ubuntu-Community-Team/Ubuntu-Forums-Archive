---
title: "utorrent window hidden"
date: 2007-06-28
forum: General Help
---

### Post by dansued on 2007-06-28
my utorrent is running under wine just fine but something happened and the window is now hidden somewhere. If I hover over the tray icon, it's still running and downloading. Obviously, I have right clicked the tray icon and did the show/hide utorrent option. I've tried alt-tabbing all the workspaces and it's not there.

I considered uninstalling and reinstalling the program but it wasn't really installed, utorrent is just a single exe that you run. It doesn't show up under wine software uninstaller. The .wine folder didn't have any config folders or anything so I wasn't sure what to do.

Thanks in advance.

---

### Post by AlexThomson_NZ on 2007-06-28
I use uTorrent in wine as well (for downloading distros of course! ;) ) and have the same problem.  I found by clicking, or double-clicking the taskbar icon and unminimising the window I can always get it back, but does seem to be very inconsistant.

OT- Anyone know of any good, native, lightweight Gnome BT clients that come close to uTorrent?  All the ones I've seen so far are very buggy, bloated or both...

---

### Post by dansued on 2007-06-28
my problem is now that it's not even in the taskbar.

I think utorrent is being ported to mac and eventually linux, which is excellent news.

EDIT: I fixed it by deleting the uTorrent folder from inside the .wine c drive. It sort of reinstalled it.

---

### Post by speaker219 on 2007-06-28
KTorrent is sort of a port of uTorrent to linux:
[http://en.wikipedia.org/wiki/KTorrent](http://en.wikipedia.org/wiki/KTorrent)

---

### Post by Wokm4n on 2007-06-30
I can't get it fixed :(
It worked really well first time.

I changed some preferences such as 'close to tray' and 'single click on tray icon to show', maybe that's it?
Still, I can't find any config files either.
uTorrent starts fine, it runs too (when I hover the icon I can see download speeds and stuff) but I can't get it to show up. Also tries some Alltray method which didn't work either. I just can't get the main window to appear :(

I hope someone knows how to fix this :'(

btw im on Gnome so I can't run KTorrent

---

### Post by wconstantine on 2007-06-30
Had the same problem when I ran uTorrent with Wine. Had to find another bittorrent client.

> btw im on Gnome so I can't run KTorrent

Sure you can. Just gotta download 100mb of kde-libs first. ;)

```
sudo apt-get install ktorrent
```

should do it all for you. Still it's a little disturbing because it starts so slow when not running kde. I use rtorrent (cli based) and I love it. The only feature that it doesn't have that uTorrent has is the ability to choose what files in the torrent you want to download. Kinda miss that, quite much.

Can't say I like ktorrent much either tbh. It feels like bloat and it's not so clean and neat looking.

---

### Post by Wokm4n on 2007-07-01
Thanks for your reply. I'll try rtorrent then but I'm not really good with command line stuff =/

---

### Post by shirilover on 2007-07-01
> **wconstantine said:**
> I use rtorrent (cli based) and I love it. The only feature that it doesn't have that uTorrent has is the ability to choose what files in the torrent you want to download. Kinda miss that, quite much.


Actually you can do that, at least with the latest stable release.
From the main view, arrow up/down to the torrent you want, then arrow right.
Arrow down to File List, then arrow right to the files.
Use the spacebar to toggle through the download options for each file (hig=high,normal,off=skip)

---

### Post by wconstantine on 2007-07-01
> **shirilover said:**
> Actually you can do that, at least with the latest stable release.
From the main view, arrow up/down to the torrent you want, then arrow right.
Arrow down to File List, then arrow right to the files.
Use the spacebar to toggle through the download options for each file (hig=high,normal,off=skip)

AWESOME! Thanks for letting me know! Baibai ktorrent! I've been using it for downloading large torrents I only need something specific from.

---

### Post by Eric the Grey on 2007-07-02
> **dansued said:**
> 
EDIT: I fixed it by deleting the uTorrent folder from inside the .wine c drive. It sort of reinstalled it.

Oooh, this fixed it for me.

The data folder for utorrent is at: 

.wine/drive_c/windows/profiles/USERNAME/Application Data

Delete that (obviously, substitute USERNAME for your login ID) folder and restart it.  You'll loose any settings, but it seems to work again.

Good thing too.  It's time to download my weekly Doctor Who fix. :D


:cool: Eric the Grey

---

### Post by Beatbreaker on 2007-07-06
> **Eric the Grey said:**
> Oooh, this fixed it for me.

The data folder for utorrent is at: 

.wine/drive_c/windows/profiles/USERNAME/Application Data

Delete that (obviously, substitute USERNAME for your login ID) folder and restart it.  You'll loose any settings, but it seems to work again.

Good thing too.  It's time to download my weekly Doctor Who fix. :D


:cool: Eric the Grey

I'm having the same problem, i'll give it a go too and see what happens!

thanks for the tip. I'm now wondering what happened in the first place to cause it, it was working fine before. I may have changed soem settings - the minimise to task bar setting maybe.

---

### Post by slamgauge on 2007-11-01
I have run into this problem as well so I have been backing the setting files up so when I can not bring it out of the tray I just copy the saved setting files and I still have all my settings saved.

This is handy for me because I have utorrent set up to move completed torrents to folders that correspond with their labels and it takes a few min to type in all the info after wiping out the settings.

---

### Post by neuralzen on 2008-03-20
Thanks for the tips about the app data folder!

Since I didn't want to loose my current partial downloads and torrents, I experimented and only deleted the settings.dat and settings.old.dat files to fix the problem.

Thanks again!

---

### Post by 6205 on 2008-03-20
Deluge is very very similar to uTorrent.

---

### Post by DjBones on 2008-03-20
+1 to deluge
seriously, it has a graph. what more could you want?

---

