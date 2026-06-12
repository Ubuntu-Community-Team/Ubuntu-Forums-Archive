---
title: "Dell XPS 13 4K monitor issues"
date: 2020-05-25
forum: General Help
---

### Post by timdepauw on 2020-05-25
Not sure where to post this because it touches upon a number of things: hardware, GDM, GNOME, to name but a few.

So I have this Dell XPS 13 laptop. It's got an Intel UHD Graphics 620 and a 4K monitor. I'm also connecting a 4K monitor via HDMI (through a USB-C dongle). Once I've got it working, it's great. However...

I like to press Win+P now and then to alternate between using both monitors and only using the external one. But the behavior is... erratic:


[LIST]
[*]Selecting Extend will often keep both monitors active.
[*]Usually, switching will forget that I had both monitors set to 200% zoom. Reapplying it works, luckily.
[/LIST]

And then, there's an even more annoying issue that doesn't relate to Win+P at all. If I walk away from my machine and come back after a while, both monitors will always be active, but the external one will have switched to a lower resolution. The only way to get it back to 4K is to disconnect my dongle and plug it in again.

I believe at least part of the reason is that the Intel GPU can only output 4K at 30 Hz rather than 60 Hz. This is confirmed by xrandr output. 30 Hz doesn't bother me though (or at least less than blurry text), so if some component insists on only using 60 Hz-capable resolutions, I'd sure like to disable it.

I'm really hoping someone has a fix for this, or at least some ideas toward diagnosing and debugging the issue(s). Thanks!

---

