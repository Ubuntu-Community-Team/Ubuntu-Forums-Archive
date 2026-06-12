---
title: "easy"
date: 2006-09-29
forum: General Help
---

### Post by SpikeyMike on 2006-09-29
Hi

After installing Ubuntu I used the easyubuntu utility which I understood would install all the necessary updates, codec and plugins and video drivers so that I could p lay audio and video files but I still cannot play mp3's or DVD's. I read on the forum that Automatix is better so I want to try that instead, do I first need to uninstall whatever easyubuntu installed or can I just run Automatix?  Also which are the best media players to use for audio and video?

Regards

MIkey

---

### Post by Old Pink on 2006-09-29
mPlayer is the best for video.
amaroK is the best for audio. :) 

And no, you shouldn't have to remove easy ubuntu's modifications. 

amaroK should add it's own mp3 support. :)

---

### Post by Anonii on 2006-09-29
> **Matt.H said:**
> mPlayer is the best for video.
amaroK is the best for audio. :) 

And no, you shouldn't have to remove easy ubuntu's modifications. 

amaroK should add it's own mp3 support. :)
Amarok is not the best if he uses GNOME. And he installed Ubuntu, so I guess he does. Amarok would make him load the Qt libs etc, that would **** up his performance. I suggest Rhythmbox, or the extremely buggy Listen, which is really popular nowdays.

---

### Post by Old Pink on 2006-09-29
> **Anonii said:**
> Amarok is not the best if he uses GNOME. And he installed Ubuntu, so I guess he does. Amarok would make him load the Qt libs etc, that would **** up his performance.

Heck, I use amaroK and GNOME, and they work perfectley together, no system performance change at all. :D

---

### Post by SpikeyMike on 2006-09-30
Hi

I installed amarok and mplayer but amarok won't play mp3's, do I need to install something else to get it to play them? also mplayer won't play dvd's properly, if I open it and point it to my dvd player it doesn't do anything :( 

Mikey

---

### Post by 3rdalbum on 2006-10-01
You need to install libdvdread and libdvdcss for commercial DVD playback.

For MP3 support:

```
sudo apt-get install gstreamer-0.10-plugins, gstreamer-0.10-plugins-bad, gstreamer-0.10-plugins-bad-multiverse, gstreamer-0.10-plugins-good, gstreamer-0.10-plugins-ugly, gstreamer-0.10-plugins-ugly-multiverse, gstreamer-0.10-ffmpeg, gstreamer-0.10-fluendo-mp3
```

This will give you more than just MP3 codecs too.

---

### Post by SpikeyMike on 2006-10-02
Hi

I tried that but I get the following message  "Couldn't find package gstreamer-0.10-plugins"  If I look at the synaptic package manager there are alot of gstreamer packages already installed even the Fluendo mp3 decoder package neither Amarok or Rhythmbox will play mp3's

Regards

Mikey

---

### Post by SpikeyMike on 2006-10-02
Sorry the above post is badly written, I will try again:

I tried that but I get the following message "Couldn't find package gstreamer-0.10-plugins" If I look at the synaptic package manager there are alot of gstreamer packages already installed including the Fluendo mp3 decoder package but Amarok or Rhythmbox still won't play mp3's

Regards

Mikey

---

### Post by boban on 2006-10-02
> **Matt.H said:**
> Heck, I use amaroK and GNOME, and they work perfectley together, no system performance change at all. :D

Same here :)

---

