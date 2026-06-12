---
title: "Mplayer &amp; mp3"
date: 2006-10-27
forum: General Help
---

### Post by marcozs on 2006-10-27
Hi

I use mplayer to play videos, but something strange happens: when I open a movie using the mp3 codec, it says 
```
Requested audio codec family [mp3] (afm=mp3lib) not available. Enable it at compilation.
```

But mplayer plays the movie correctly with sound anyway... anyone knows how to remove the problem or has packed the latest mplayer (1.0rc1) for edgy and can post the deb (if it solves the issue)?

---

### Post by Pri0n on 2006-10-28
In mplayer, go into your preferences, click on the **Codecs & demuxer tab**, in the field **Audio Codec Family**, select **FFmpeg/libavcodec audio decoders**.  Restart mplayer and try again.

---

### Post by marcozs on 2006-10-29
It worked thanks!
Another question: how do I set mplayer as the default video player instead of totem?

---

### Post by marcozs on 2006-10-29
I found out how (it was easy) but wouldn't it be easier to have the possibility to select the media player in the "preferred application" screen?

---

### Post by Completenutter2 on 2006-10-29
For anyone that comes here from google or somewhere else, looking to change default player to mplayer (or other), you just do the following:

Right click a file of the type you want to change
Select Properties
4th Tab along is 'Open With'
Select the application you want to default to

---

### Post by PhoenixAndy on 2006-11-05
> **Pri0n said:**
> In mplayer, go into your preferences, click on the **Codecs & demuxer tab**, in the field **Audio Codec Family**, select **FFmpeg/libavcodec audio decoders**.  Restart mplayer and try again.

Well, that stopped the error message appearing, but I'm still getting no sound on files that I could play fine before the upgrade to edgy.

---

