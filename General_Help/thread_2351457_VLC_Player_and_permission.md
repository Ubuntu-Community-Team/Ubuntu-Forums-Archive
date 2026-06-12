---
title: "VLC Player and permission?"
date: 2017-02-03
forum: General Help
---

### Post by jaytt on 2017-02-03
Hi

If I copy an MP4 from my mounted drive to my home directory, I can open it in VLC and it plays.
I have some media on a mounted drive (mounted to /mnt/hdd1 in fstab) that I can double click to open/play with video player, but when I open with other application and select VLC it will not play.

If I open up VLC and try to browse, it only sees home directory so im guessing its a permission issue.

Any help please.
Thanks

---

### Post by mc4man on 2017-02-03
You are probably using the snap version of vlc which is confined to your home folder.  So remove it with, 
sudo snap remove vlc
Then either install the deb package version or reinstall the snap as such, 
```
sudo snap install --devmode vlc
```

---

### Post by jaytt on 2017-02-03
sorted it a slightly different way though - thanks

removed it via Ubuntu Software GUI (how i originally found and installed it), then installed it by
sudo apt-get update
sudo apt-get install vlc browser-plugin-vlc

Not sure what the diff is between your way and mine but its now working

Cheers

---

### Post by bayvista on 2017-03-06
Tried that but still does not work. Any more ideas?

---

### Post by cariboo on 2017-03-07
> **bayvista said:**
> Tried that but still does not work. Any more ideas?

WHat have you done yourself? It may be better to start a new thread, describing your problem, and what you have tried to solve it.

---

