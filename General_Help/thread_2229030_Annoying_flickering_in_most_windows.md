---
title: "Annoying flickering in most windows"
date: 2014-06-10
forum: General Help
---

### Post by juha-lumme on 2014-06-10
Recently my Ubuntu 14.04 installation has started showing annoying flicker in most of the windows. It seems as if like previous "frame" of the window would be shown for few millisecond, and then current one is shown again. This affects terminal windows, gtk windows and also pdf viewer. For some reason browser is not affected, nor are some apps (such as Spotify). I wonder if this is for all apps that use "custom rendering".

Anyway, I took a short video of the symptoms, and it can be seen here:

[http://youtu.be/U-jH6wmq1CM](http://youtu.be/U-jH6wmq1CM)

I have NVidia gtx560, and have tried updating to latest drivers (337.25)

I opened a question at askubuntu.com as well here, but so far no answers: [http://askubuntu.com/questions/481276/previous-frame-seems-to-flicker-in-any-type-of-window](http://askubuntu.com/questions/481276/previous-frame-seems-to-flicker-in-any-type-of-window)

---

### Post by juha-lumme on 2014-06-14
Just for the record if someone finds himself with same situation, I found a workaround for this. in Compiz manager/workarounds, select "**Force full screen redraws (buffer swap) on repaint**"

---

