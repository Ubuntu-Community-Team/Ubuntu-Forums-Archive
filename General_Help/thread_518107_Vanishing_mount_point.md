---
title: "Vanishing mount point?"
date: 2007-08-05
forum: General Help
---

### Post by T'sora on 2007-08-05
I'm probably missing something pretty basic here, but I've dug aruond the forums and I'm not coming up with anything.

I have a second hard drive (formatted as ext3) that I use for music storage - and I finally got around to plugging it in. Followed this guide:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

and the drive showed up in /media as "Main Drive" (what it was called on my old system) right away. 

However, whenever I reboot, the drive isn't recognized by programs that use it - i.e. my playlists in Amarok. 

Looking at df -h doesn't show it mounted, but fdisk and blkid show it fine. Then, if I use Nautilus and hit Places > Computer - it will then show up, be recognized by everything, and all is well. But the minute I shutdown or reboot again the drive is "gone" until I repeat the above.

Help? :confused:

---

