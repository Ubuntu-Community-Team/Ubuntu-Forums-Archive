---
title: "Video without sound"
date: 2022-06-30
forum: General Help
---

### Post by py-ohayo on 2022-06-30
Hello,
Some videos, which I downloaded, play with "Videos" without sound.
When I start such a video, the volume of "Videos" is 0. Increasing the volume does not help - the video remains silent.
When I play the same video on Windows, the sound is present.
Any suggestions ?
Thanks.

---

### Post by TheFu on 2022-06-30
Do any videos play with sound?  Just a few don't?

Use mpv or VLC to playback the videos.

"Videos" is a very, very, generic term. There must be 150 different combinations of popular video and audo encodings for "videos" today.  Some are better supported than others.  Which audio encoding is being used in the problem videos?  

Do any music files playback fine?

Is all sound broken or just in specific videos?

---

### Post by Holger_Gehrke on 2022-06-30
This means you're missing some audio codecs. Since you don't say which video player you're trying to use and on what version and flavor of Ubuntu and not all players use the same codecs, I'm going to assume you're using the default video player on a reasonably recent version of the Ubuntu. Try running 
```

sudo apt install gstreamer1.0-plugins-{base,good,bad,ugly}

```
in the terminal. This will install the four major sets of plugins for the gstreamer multimedia framework and their dependencies. Alternatively you can use the Software Application and search for 'gstreamer1.0-plugins' and install whichever of the four are not yet installed. If this doesn't clear up the problem, knowing the version and flavour of Ubuntu and the player you're using would help us help you ...

Holger

---

