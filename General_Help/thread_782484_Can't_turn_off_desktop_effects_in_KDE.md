---
title: "Can't turn off desktop effects in KDE"
date: 2008-05-05
forum: General Help
---

### Post by HunterThomson on 2008-05-05
Aloha,
I turned on some window effects in KDE and now I can not watch videos in any media player I have. All the default players and VLC play no video only sound. I know this is a problem with the driver for my video card. I would like to just turn the effects off. When I try to do so in the GUI it doesn't work, not on reboot or any conmen scents ways to turn them off. I even stared the GUI with sudo in the comand line and the effects still do not turn off. I have run out of ideas. If you have any suggestions pleas let me know. I was thinking maybe some comand line argument mite do the trick or turning something off in start up. I guess if it is just stuck on, I guess, I could just go through the steps to get the video working with compiz for my video card.

Mahalo,

---

### Post by Zorael on 2008-05-05
So if you enable those desktop effects, can you then again watch video content?

We'd need to know some more stuff, like what videocard you're using. Paste the output of the following command.
```
$ lshw -C video
```

---

### Post by zip_000 on 2008-08-14
I had exactly the same problem, but I found a solution - it's a dumb solution, but it works.

Problem:
Video won't play properly. In Kaffiene I get sound but no video. In VLC I get video and sound, but if I enlarge the video to full screen (or even just a bit bigger than the small window) it crashes.

I guessed that this was caused by the Desktop Effects that I had played around with earlier. The problem was that even though I turned off the effects in the Compiz Desktop Effects console, the effects were still happening: windows were still flipping, etc. So, repeating, the radio button beside "No Effects" was selected, yet I still had effects...which was spoiling video watching.

I don't know enough about the Desktop effects to know how to fix the problem or where to look. I tried uninstalling compiz-kde and restarting X..amazingly, I still had the same Desktop Effects!  

Solution:
So I reinstalled compiz-kde. Turned on Desktop Effects, and then turned it off again.  Problem solved.

This is a ridiculous solution...the sort of problem that I used to get in Windows....which is why I don't use Windows anymore.

Graphics card is Nvidia (an older model, I don't remember which) using the Nvidia driver.

---

