---
title: "compiz eating up huge amount of CPU"
date: 2018-03-29
forum: General Help
---

### Post by dciotoli on 2018-03-29
Hey folks,

I'm running 16.04 on some pretty good hardware (8 i7 cores), and compiz is using 20% CPU of each core!

Here's a screenshot of the top command, and my system monitor:

[ATTACH=CONFIG]279129[/ATTACH]

[ATTACH=CONFIG]279130[/ATTACH]



What can i do to reduce this huge CPU draw?

---

### Post by deadflowr on 2018-03-29
Since xvfb is in use it seems likely you don't have a proper display driver in use. I would think.
Run inxi and see what the graphics card says.
```
sudo apt install inxi
inxi -G
```
the first line will install inxi if from some reason it is not already installed (if it is it'll tell you so)
the second outputs information about the gpu on the machine.
Please post back any results.

This is an assumption that the system is running all on a single machine.
If, however, the system is running remotely, then that would be something else and would make sense as compiz would indeed be heavy as it's not very good for remote sessions.

---

### Post by dciotoli on 2018-03-29
Resulting output after running the commands (seem to be correctly detecting my GPU):

daniel@daniel-XPS-8920:~$ inxi -G
Graphics:  Card-1: Intel Device 5912
           Card-2: NVIDIA Device 1c82
           Display Server: X.Org 1.19.5 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz, 1920x1080@60.00hz
           GLX Renderer: GeForce GTX 1050 Ti/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 384.111

---

### Post by QIII on 2018-03-29
Hello!

Please do not paste large images.  Some users are on mobile devices, some have slow connections and some have data limits.  Please let those people decide whether or not to view the images full sized.

I have reduced your images to thumbnails that can be enlarged.

To do so next time, please use the attachment functionality provided by the "paperclip" icon in the toolbars above the text entry box.

Thanks.

---

### Post by dciotoli on 2018-03-29
> **QIII said:**
> Hello!

Please do not paste large images.  Some users are on mobile devices, some have slow connections and some have data limits.  Please let those people decide whether or not to view the images full sized.

I have reduced your images to thumbnails that can be enlarged.

To do so next time, please use the attachment functionality provided by the "paperclip" icon in the toolbars above the text entry box.

Thanks.

Sorry about that! Will be sure to do so in the future.

---

### Post by ansgar.snow on 2018-03-29
Maybe try to disable your integrated gpu via bios.Reainstalling nvidia drivers also can help sometimes in cases like this.

---

### Post by dciotoli on 2018-04-02
Solved the issue, turns out Chrome's remote desktop extension was virtualizing a desktop using the CPU. Disabled it and compiz is back to normal!

---

