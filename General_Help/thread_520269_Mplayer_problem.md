---
title: "Mplayer problem"
date: 2007-08-08
forum: General Help
---

### Post by logreeval on 2007-08-08
I want to increase the size of the video but if I say like full screen, or twice as big, it is the same size, but the white part is bigger. Can I increase the actual size of the playing video.

Thanks.

---

### Post by tbroderick on 2007-08-08
What video out driver are you using? If you are not using Compiz/Beryl etc. Try using the xv driver. You can start mplayer from the terminal to try it out or change the preferences from the GUI.

```

mplayer -vo xv video.avi
```

You can then drag the corners of the video window and it should enlarge the entire video.

---

### Post by logreeval on 2007-08-08
awesome, thanks...

is that the only driver that does that?

---

