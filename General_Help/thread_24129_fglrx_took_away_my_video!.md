---
title: "fglrx took away my video!"
date: 2005-04-05
forum: General Help
---

### Post by teumima on 2005-04-05
Hi

ever since I installed fglrx (ati drivers) i cant play my movie players. The error i get is: Error opening/initializing the selected video_out (-vo) device.

This is with mplayer.

Can anyone help me?

When I choose XWindows (X11/XShm/Xv) as output I get this error:

Failed to construct test pipeline for 'XWindows (X11/XShm/Xv)

---

### Post by whatever on 2005-04-05
xorg.conf, Section "Device":
```
    Option "VideoOverlay"               "on"
    Option "OpenGLOverlay"              "off"
```

---

### Post by Zwack on 2005-04-05
A More detailed explanation... 

The fglrx driver will either do DRI (openGL) or XVideo.  It doesn't seem as if mplayer likes the output options you are trying to give it.  My personal advice is to install Xine (totem-Xine too) and then you can use that.  At least it works for me.

Z.

---

### Post by teumima on 2005-04-06
Whatever was right. I forgot to add those options under my device. This fixes the issue. Thanks all the help guys.

---

