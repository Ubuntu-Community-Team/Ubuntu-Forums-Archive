---
title: "mplayer error opening -vo"
date: 2005-03-30
forum: General Help
---

### Post by batteryacid on 2005-03-30
I recently upgraded the driver for my video card from the default driver that came with Ubuntu to the ATI fglrx driver. Since then, Mplayer will not work properly. If i load it up and try to open a file, i get the error message : 
      Error opening/initializing the selected video_out (-vo) device. 
Interestingly, if i right-click a video file and click "open with mplayer," it will play but without sound. Does anyone know what could be wrong? I'm sure it has to do with the recent video driver change, but i'm a bit of a n00b so the inner workings of linux are foreign to me. 

info on my machine:
Dell inspiron 8200
ati radeon 9000 
p4 2.0, 512mb ram

Thanks a bunch.

---

### Post by fdoving on 2005-03-30
[QUOTE=batteryacid]I recently upgraded the driver for my video card from the default driver that came with Ubuntu to the ATI fglrx driver. Since then, Mplayer will not work properly. If i load it up and try to open a file, i get the error message : 
      Error opening/initializing the selected video_out (-vo) device. 
Interestingly, if i right-click a video file and click "open with mplayer," it will play but without sound. Does anyone know what could be wrong? I'm sure it has to do with the recent video driver change, but i'm a bit of a n00b so the inner workings of linux are foreign to me. 

info on my machine:
Dell inspiron 8200
ati radeon 9000 
p4 2.0, 512mb ram

Thanks a bunch.[/QUOTE]
 Hi.

That's because -vo xv doesn't support 24bit colordepth.. only 16.
try: mplayer -vo x11 -zoom file.mpg
If that works you can consider putting the settings in /home/youruser/.mplayer/config
like this:
```

vo=x11
zoom=yes

```


Hope this helps.

---

### Post by tube on 2005-04-02
If the x11-driver is too slow for you, you could try -vo xvidix:radeon (I assume you have a radeon as you're using the fglrx driver) to get hardware acceleration. This only works as root for me though. If anyone knows how to make it work as a normal user, I'd be very interested.

---

### Post by batteryacid on 2005-04-03
[QUOTE=fdoving]Hi.

That's because -vo xv doesn't support 24bit colordepth.. only 16.
try: mplayer -vo x11 -zoom file.mpg
If that works you can consider putting the settings in /home/youruser/.mplayer/config
like this:
```

vo=x11
zoom=yes

```


Hope this helps.[/QUOTE]

Thank you very much. Initially it only worked in command line, but then I realized that gmplayer uses guiconf instead of config as its configuration file. Now it works perfectly. 

Thanks again!

---

### Post by tube on 2005-04-03
[QUOTE=tube]If the x11-driver is too slow for you, you could try -vo xvidix:radeon[/QUOTE]That's -vo xvidix:radeon_vid.so of course... sorry about that.

---

