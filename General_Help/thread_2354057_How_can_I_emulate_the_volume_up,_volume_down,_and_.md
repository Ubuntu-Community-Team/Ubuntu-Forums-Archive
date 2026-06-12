---
title: "How can I emulate the volume up, volume down, and play/pause buttons on my keyboard?"
date: 2017-02-27
forum: General Help
---

### Post by jonathan90 on 2017-02-27
I have a laptop which lets me use play/pause, volume up, and volume down using Fn + F9, Fn + F11, and Fn + F12 respectively. I'm using a USB keyboard without any multimedia keys with my laptop and I want to bind certain key combinations to execute the play/pause, volume up, and volume down. So if I, for example, pressed Ctrl + Alt + Ins, it would execute Fn + F9. Any ideas? Thanks!

---

### Post by jonathan90 on 2017-02-28
After searching on Google for quite a while, I figured it out!

I found that the command "xdotool key XF86AudioPlay" toggles between play/pause on the system, doing the same function as the built in audio play/pause. It worked perfectly when I ran the command form the terminal, but when I tried to set a keyboard shortcut to execute the command, it would often not respond. Eventually, I discovered that you need to run the command with "--clearmodifiers" for the shortcut to work correctly. I set the shortcut to run "xdotool key --clearmodifiers XF86AudioPlay", and now it works perfectly! I went into dconf (dconf->org->gnome->settings-daemon->plugins->media-keys) and found the "xdotool" key for all the other media commands. Just to save anyone else the trouble, here are the ones I used. 

```
xdotool key --clearmodifiers XF86AudioPlay
xdotool key --clearmodifiers XF86AudioPrev
xdotool key --clearmodifiers XF86AudioNext
xdotool key --clearmodifiers XF86AudioLowerVolume
xdotool key --clearmodifiers XF86AudioRaiseVolume
xdotool key --clearmodifiers XF86AudioMute
```

In particular, using the system's raise and lower volume commands let the volume pop-up bar appear whenever I change the volume, and it will allow me to change the volume by the same increments as the audio keys on my laptop.

---

### Post by kingneutron on 2017-03-01
Thanks for that :) Please be sure to mark your thread as Solved.

---

