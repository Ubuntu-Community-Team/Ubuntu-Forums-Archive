---
title: "I need a suggestion for a video player"
date: 2023-06-05
forum: General Help
---

### Post by stevermann on 2023-06-05
I need a suggestion for a video player that will open two instances.  VLC won't do that.
Here's what's happening- I am building our Halloween props and this year the theme is space.  I am making a space station/lab and inside there will be display screens in a lab wall.  I am using an Intel NUC running Ubuntu Desktop 20.04.  The two displays are plugged into HDMI ports (this NUC has two). One will be a POV video of a rover on a strange planet, and the other will be a rover picking up samples.  So, I am looking for a suggestion of a video player that I can run two instances, one on each screen.

Ideas, anyone?

---

### Post by Rubi1200 on 2023-06-05
Hi,

Not sure I can help but will this work?

Open a terminal and run:

```
vlc --no-one-instance file1.mp3 & vlc --no-one-instance file2.mp3
```

Obviously, you would replace file1 and file2 with the actual file names you want.

---

### Post by guiverc on 2023-06-05
Why can't vlc do that?

I'm not running 20.04 (but *mantic*); but on my newer release I opened two vlc sessions which are now playing on different screens (*they'll play **in windows or full-scree*n) on this box (*whilst I reply on a third screen*).

I'm currently logged in with my usual LXQt/Lubuntu session; but I'd expect it to work equally if using GNOME/Ubuntu, Xfce/Xubuntu etc.  Also FYI:  I'd have expected the same behavior years ago when I was running *focal* or 20.04 on this box.
[I]
edit:  I never ran focal on this box; but I meant the box that I was using until it's PSU died last year that then used these screens/keyboards that I use.[/I]

---

### Post by stevermann on 2023-06-06
Thanks. That does open two instances, but one was on top of the other.  But I can work with that.

---

### Post by stevermann on 2023-06-06
If you hadn't told me thay you did it, I wouldn't have looked further.  I found this on the VNC website: By default VNC will only open one session. There is an option in tools/preferences to allow multiple instances:

> Open the VLC Media Player.
Go to Tools &#8227; Preferences 
Select the Interface tab and scroll down to Playlists and Instances .
Uncheck the Allow only one instance option.
Uncheck the Use only one instance when started from file manager option.
Click on the Save button.


---

### Post by Rubi1200 on 2023-06-06
Happy to hear you found a solution that works for you.

Please use Thread Tools to mark as Solved so that others can also benefit.

Thanks.

---

### Post by TheFu on 2023-06-06
**mplayer**, **mpv**, also work. If you need a GUI for them, check out **smplayer**.

---

