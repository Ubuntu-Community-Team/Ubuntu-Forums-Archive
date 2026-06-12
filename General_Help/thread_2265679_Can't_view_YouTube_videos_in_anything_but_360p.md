---
title: "Can't view YouTube videos in anything but 360p?"
date: 2015-02-16
forum: General Help
---

### Post by rimside2 on 2015-02-16
Due to a pc error I got back into using Ubuntu, at least for a little while, and can't remember how I fixed a problem with viewing videos in more than 360p with Firefox. I am using 14.04 now, instead of the 12.10 I was at the time. Maybe that has to do with it?

I also read around and realized that I could just use chrome, but I can't install chrome. It comes up with miscelaneous errors.

---

### Post by grier-devon on 2015-02-16
1. Q: What graphics card or chip does this computer have?
A: If Nvidia or Radeon then use the driver utility to install proprietary drivers

2. Q: Do you have problems when installing anything other then chrome?
A: If it is only chrome then more then likely it is a messed up config, open a file manager and go to view > show hidden files > .config. Once there find the "google-chrome" folder and delete the folder. Once you have done this then try to install chrome again.

A part 2: If you are having an issue installing any application then run.....
```
sudo apt-get install -f
```

This will install any broken dependencies you might have. If none of this works let me know.

---

### Post by fred.sauze on 2015-05-28
Two options:
1) Easiest method is install flash.
```
sudo apt-get install flashplugin-installer
```

2) It is recommended to use HTML5 instead.
Go to "about:config" on you firefox, and set following settings to "true" (double-click)
```

media.mediasource.enabled 
media.mediasource.webm.enabled 
media.mediasource.mp4.enabled 
media.fragmented-mp4.exposed 
media.fragmented-mp4.ffmpeg.enabled 
media.fragmented-mp4.gmp.enabled 
media.peerconnection.video.h264_enabled 

```

---

