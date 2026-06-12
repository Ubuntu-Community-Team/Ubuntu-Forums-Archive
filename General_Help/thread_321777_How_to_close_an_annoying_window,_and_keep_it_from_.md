---
title: "How to close an annoying window, and keep it from opening at startup?"
date: 2006-12-19
forum: General Help
---

### Post by maruchan on 2006-12-19
Ever since I installed...Hoary? Dapper? I have had this strange artifact on the top left of my screen. It has persisted even after an Edgy upgrade. Today I came to my senses and ran XWinInfo on it - turns out it's actually a window! I've pasted the output below.

Can anybody help me figure out what this is and how I can keep it from starting up with my desktop? It's a small white area that's 1x16 pixels in size. When I turn Beryl on, it gets a drop-shadow, which is *really* annoying. :D

Anyway, here's the window info:

```

xwininfo: Window id: 0x4400101 "."

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1
  Height: 16
  Depth: 24
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: yes
  Map State: IsViewable
  Override Redirect State: yes
  Corners:  +0+0  -1919+0  -1919-1184  +0-1184
  -geometry 1x16+0+0

```

The interesting thing is that the window is identified as "." - thanks for any help with this!

---

### Post by raul_ on 2006-12-19
Have you tried removing it from Systems->Preferences->Sessions->Startup programs ? Check if you have something that you don't know what it is...

---

### Post by maruchan on 2006-12-19
Thanks for your advice. I'm still not sure why it's starting at startup (it's not in any session manager) but I know what it is now: I ran "xprop" and clicked on it, which gave me the process ID number. I looked up the process ID and found:

wxvlc

So I killed VLC and whoosh, gone. I have VLC running all the time so at least now I know what causes the problem and who to complain to ;)

I'll probably delete .vlc or wherever the settings are and restart. :)

---

