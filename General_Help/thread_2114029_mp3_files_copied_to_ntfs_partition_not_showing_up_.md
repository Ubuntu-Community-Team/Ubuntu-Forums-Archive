---
title: "mp3 files copied to ntfs partition not showing up in music library"
date: 2013-02-08
forum: General Help
---

### Post by arunthegr8 on 2013-02-08
I have recently installed Ubuntu and have removed any trace of Windows from my PC. I haven't formatted my partitions to ext though because I don't have a spare drive to take backups.

My problem is that when I am copying new music files to my NTFS partitions, they are not showing up in any of the Music players (Clementine and gmusicbrowser) even after repeated scans though I can play them when I manually go to the directory and play them using VLC. I am even unable to add them to the play list of the music players by drag-drop.

Can someone tell me what's the problem here and how can I debug it?

Thanks,
Arun

---

### Post by carl4926 on 2013-02-09
The partition where the files are located must be mounted when the music player is asked to scan and the directory of the files must be in the settings for scan of the music player...

---

### Post by arunthegr8 on 2013-02-09
> **carl4926 said:**
> The partition where the files are located must be mounted when the music player is asked to scan and the directory of the files must be in the settings for scan of the music player...

Well, I have taken care of that. The drives are automounted as I have edited fstab to do so and the folder is included in the section where the music player scans the files to include in its library. Can you suggest why even after doing so I am neither able to browse the files from the music player nor am I able to find them in the music library even after repeated scans, even though I can access them from the normal file browser.

---

### Post by arunthegr8 on 2013-02-12
Bounce. Anyone?

---

### Post by carl4926 on 2013-02-13
If the partition is correctly mounted and you can navigate the files in the file manager. There should be no problem. The only possible thing you might check is to try a different music player.
In Ubuntu I use Rhythmbox or Banshee

---

### Post by Yellow Pasque on 2013-02-13
clementine and gmusicbrowser both use gstreamer (so do rbox and banshee). Make sure you have the appropriate gstreamer plugins:
```
sudo apt-get install ubuntu-restricted-extras
```

---

