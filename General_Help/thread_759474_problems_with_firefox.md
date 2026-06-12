---
title: "problems with firefox"
date: 2008-04-19
forum: General Help
---

### Post by Despot Despondency on 2008-04-19
Hi,

I'm having quite a lot of problems with firefox. I think it's the embedded mplayer that is causing the problems. There are two main problems, namely

1) When I try to watch/listen to a stream on a website sometimes it connects to the stream and then automatically stops. When I press play again it tries to connect to the stream again and then stops again.

2) Sometimes firefox will crash completely. This usually happens on sites with video streams.

Has anyone else had this problem or have any suggestions? I'm using gutsy by the way.

---

### Post by ryanhaigh on 2008-04-19
Perhaps you could try removing the plugin you believe to be causing the problem and using an alternative such as vlc

```
sudo apt-get remove mozilla-mplayer
sudo apt-get install vlc mozilla-plugin-vlc
```

---

