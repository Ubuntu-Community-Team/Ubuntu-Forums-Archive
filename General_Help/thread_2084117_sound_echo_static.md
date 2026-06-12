---
title: "sound echo static"
date: 2012-11-14
forum: General Help
---

### Post by spiritech on 2012-11-14
i am having problems with my sound. both on the previous 12.04 and now on 12.10.
when i play something through vlc or watch something on youtube i get a horrible echoe static sound. normally it goes away after a minute or so, though sometimes it does not and i have to restart vlc or my browser.

not sure how to fix this problem.

---

### Post by coffeecat on 2012-11-19
I hope you're still around because I've only just found this thread. You are not alone. It's a common problem with VLC and probably the fault of pulseaudio. Try one or both of these:

Open VLC, Tools menu -> Preferences -> Audio.

1 - Under Volume, tick the "Always reset audio start level to" button and set the level to less than 100%. I use 98%.

2 - Under output, find an output that works which is neither "default" nor "pulseaudio". ALSA works for me.

Then save the new settings. You need to restart VLC after making those changes.

---

### Post by spiritech on 2012-11-19
> **coffeecat said:**
> 2 - Under output, find an output that works which is neither "default" nor "pulseaudio". ALSA works for me.

if i use ALSA in vlc, it works fine apart from the fact there is normally a long delay before the sound comes in after playing or resuming from pause. it is not a major problem and is best fix for now. i was just hoping i could find a solution to the pulseaudio.

thankyou for your help :)

---

