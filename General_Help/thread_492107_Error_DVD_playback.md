---
title: "Error DVD playback"
date: 2007-07-04
forum: General Help
---

### Post by Dark Ares on 2007-07-04
Hi. I have a problem with playing dvds. When I insert a dvd movie totem autostarts, but it cant play the movie because it gets this error. Here is a picture of my problem: [http://www.imagehosting.com/show.php/861914_error.jpg.html](http://www.imagehosting.com/show.php/861914_error.jpg.html)

---

### Post by tgm4883 on 2007-07-04
Well the picture is failing to load, so this is a complete guess.  But I would try this from ubuntuguide

>  How to install DVD playback capability

ironss: gstreamer dvd plugin is available as part of plugins-bad (or ugly?) and does not work reliably. However, Totem works with the xine backend to play back DVDs. This will keep you going until gstreamer gets dvd playback. Note that you do not have to install xine-ui or mplayer.

```
sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine
```
```

sudo apt-get install libdvdcss2
```


:EDIT:

Well, the picture finally loaded.  I would say do the above.

---

### Post by Dark Ares on 2007-07-05
i did the 4 commands from terminal. The first one said i already had the latest version, the second one downloaded libdvdcss2 and installed it. The third one sayd i already had the latest version, and so did the fourth one. But unfortunately i get the same error. Anything else i can do?

---

### Post by Ayuthia on 2007-07-05
You might also try libxine-extracodecs and w32codecs (might just be w32--I am currently running 64-bit so I am using w64codecs and I can't remember the 32-bit name).  I forgot what w32 is for though.

---

### Post by galileon on 2007-07-19
> **Dark Ares said:**
> i did the 4 commands from terminal. The first one said i already had the latest version, the second one downloaded libdvdcss2 and installed it. The third one sayd i already had the latest version, and so did the fourth one. But unfortunately i get the same error. Anything else i can do?

just to be sure, you did each and tried to use the dvd in between right? because the second one worked for me...

edit: sorry, they are differennt things!my bad.

the second one, followed by running vlc worked for me ftr.

---

### Post by IHateSnow on 2007-07-20
> **tgm4883 said:**
> Well the picture is failing to load, so this is a complete guess.  But I would try this from ubuntuguide



:EDIT:

Well, the picture finally loaded.  I would say do the above.

^^^ I did the same and it now works,

---

