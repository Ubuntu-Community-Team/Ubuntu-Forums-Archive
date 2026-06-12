---
title: "Wayland freezes when video is played on VLC"
date: 2019-05-29
forum: General Help
---

### Post by meetdilip on 2019-05-29
I tried to play a couple of video files using VLC while on Wayland session in 18.04. Whenever I trie to do that, they whole system freezes. I am forced to restart using the physical power button. Is there a fix ? How to get out of this ? Thanks.

---

### Post by HermanAB on 2019-05-29
Ayup - there are several fixes: Mplayer, Xine, fflplay, gst-play...

---

### Post by meetdilip on 2019-05-29
Thanks @HermanAB . It's a VLC error then ?

---

### Post by HermanAB on 2019-05-30
In my experience (I pretty much do military video streaming for a living), VLC is just plain terrible and best avoided.

---

### Post by SeijiSensei on 2019-05-30
I strongly recommend using SMPlayer with mpv as the engine:

```
sudo apt install smplayer mpv
```

---

### Post by meetdilip on 2019-05-31
Thanks guys. I will try.

---

