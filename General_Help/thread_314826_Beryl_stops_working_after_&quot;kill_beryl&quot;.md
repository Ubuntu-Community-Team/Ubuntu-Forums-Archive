---
title: "Beryl stops working after &quot;kill beryl&quot;"
date: 2006-12-08
forum: General Help
---

### Post by Nelson-Ray on 2006-12-08
Hello,
I had Beryl running fairly smoothly. One time I was using Gnome's System Monitor and decided to kill/end the beryl process. Beryl-Manager was still running. After I ended the beryl process, desktop seemed to lock up, although the mouse moved. Even on reboot now if I launch beryl-manager, the same thing happens. Beryl seems to be turning on, window border disappears then the desktop freezes up, although the mouse works. 

The strange thing is I repeated this same procedure on another Edgy desktop I have, running the similar setup (Nvidia 6600 GT video card). I killed the beryl process while beryl & beryl-manager were running and the same thing happened. Also on this computer, even on reboot, when beryl-manager is launched the desktop locks up although mouse still moves.

Anybody would have some idea on how to fix this?

---

### Post by endersshadow on 2006-12-08
Well, when you kill Beryl, it dies.  It is *not* loaded as a restarting program by default for a variety of reasons (one being that it's still in *very* active development). When Beryl dies, your window managing abilities go out the window, so all that you have is a mouse and no way to move windows from top to bottom, aka "desktop freeze."  So, in the terminal:

```
emerald &
beryl &
```

Welcome back to the world of Beryl :)

---

