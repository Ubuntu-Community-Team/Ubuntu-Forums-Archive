---
title: "[SOLVED] Gutsy:  Utorrent problem"
date: 2008-05-30
forum: General Help
---

### Post by robelliott2125 on 2008-05-30
Hi guys,

I'm running Utorrent in gutsy, through Wine, and for some reason its starting up straight to tray, and not allowing me to use it.
If I right click, I'm able to click on everything, and Exit works, but when trying to show / hide, it doesn't do anything.

I'm just wondering if anyone else has had the same problem, as this is becoming rather annoying now.

Thanks,

---

### Post by danwood76 on 2008-05-30
Theres no need to run utorrent through wine when there are linux alternatives that are equally as good.

Ubuntu ships with transmission which is pretty good, though doesnt have many advanced features.
I personally use Azureus (the version in the repositories is the one without VUSE so its simple)
Ktorrent is similar to Utorrent though its for KDE.

-- edit --

Deluge is also pretty good, quite like utorrent and is GNOME native

---

### Post by wdaniels on 2008-05-30
Yes, I used to have this problem with uTorrent before I switched to using Deluge. You have to turn off in the preferences "minimise to tray". The only way I know of to fix it once it gets stuck like that is to delete the files settings.dat and settings.dat.old from ~/.wine/drive_c/windows/Application Data/uTorrent which does mean that you will have to reconfigure it again. Basically, you need to avoid using the minimise button on the window and instead click on the tray icon to show/hide.

---

### Post by robelliott2125 on 2008-05-30
> **danwood76 said:**
> Theres no need to run utorrent through wine when there are linux alternatives that are equally as good.

Ubuntu ships with transmission which is pretty good, though doesnt have many advanced features.
I personally use Azureus (the version in the repositories is the one without VUSE so its simple)
Ktorrent is similar to Utorrent though its for KDE.

-- edit --

Deluge is also pretty good, quite like utorrent and is GNOME native

I'm running utorrent, as I haven't yet found an equally powerful torrent program.  Transmission I ran for about two weeks, and it would leech slowly, and never seed back.  I checked my ports, and my settings for uploading, but it continued to do this.
Azureus is a resource hog.

I believe few places would accept Deluge.

Ktorrent.  Ahhhh, this was a pain in the perverbial tbh.
I ran it, it ran full speeds, was a fantastic program, however, if you're adding things which have already completed, which your needing to seed, it tries to redownload it.
I've checked time and time again that the folders are correct, and that i'm not downloading into the folder (ie. storage/downloads/file123/file123)
I've also added it so its within the main folder, (ie. storage/downloads) thinking it would find the file, and add it all.

On occasions it would find the folder, but not the data within, when using the same .torrent and knowing its the same data inside.

So i reinstalled Wine and ran utorrent.

wdaniels

Thanks for your info bud, do you know if this'll lose all my torrents within?  I don't mind re-sorting all the settings, just the torrents will be a pain in the ***.

Thank you,

---

### Post by wdaniels on 2008-05-30
> **robelliott2125 said:**
> Thanks for your info bud, do you know if this'll lose all my torrents within?  I don't mind re-sorting all the settings, just the torrents will be a pain in the ***.

I don't *believe* it will affect the torrents, only the settings, but I honestly don't remember for sure.

---

### Post by robelliott2125 on 2008-05-30
I've just tried to delete the conf files, and they aren't there in the latest utorrent build.  I forgot it no longer installs, its just a quick loader.

Any more suggestions?

I've just installed ktorrent as a last resort, but without utorrent allowing me to open it to see whats actually downloading / and finished, i haven't a clue what needs added and what doesn't.

---

### Post by wdaniels on 2008-05-30
> **robelliott2125 said:**
> without utorrent allowing me to open it to see whats actually downloading / and finished, i haven't a clue what needs added and what doesn't.

I just went to check the appdb at winehq and saw some comment that the webUI is installed by default now (it was beta when I last used utorrent but I used to install it manually as a safeguard in case I accidentally lost the window) so maybe you could use that just to check?

I will have a look for more info for you...

---

### Post by wdaniels on 2008-05-30
> **robelliott2125 said:**
> I've just tried to delete the conf files, and they aren't there in the latest utorrent build.

I just downloaded the latest build and it does seem to use the settings.dat file still only I told you slightly the wrong path, it's ~/.wine/drive_c/windows/profiles/<user>/Application Data/uTorrent.

---

### Post by robelliott2125 on 2008-05-30
You are a pure GEEEEEEEEEEEEEEENIUS!!!

I did start looking through the folders in WINE, but i'm tired, so left it.

I won't just be shunning danwood76's advice, I've installed ktorrent, and over time, I'll unload the torrents and then start using ktorrent more.
However, Utorrent are also considering porting it across to Linux after they've created the Mac OSX port.  Hopefully they do it, and i'll be much happier...  However, in the meantime, ktorrent will have to do after this load is gone.

Thank you everyone!  Problem solved.

---

