---
title: "Using v4l2-ctl to zoom in with webcam"
date: 2022-10-20
forum: General Help
---

### Post by Tom_Carr on 2022-10-20
I am a light weight user of ubuntu.  I rarely use the terminal.  I tend to leave well enough alone rather than risk breaking something.


I would like to zoom in with my webcam so my face is larger.  I have seen this command described as expanding the view to 200%


> $ v4l2-ctl -d /dev/video0 -c zoom_absolute=200


my question -  Is there any chance of breaking anything by using this command?  Can I just reboot to get back to the original webcam settings?

---

### Post by HermanAB on 2022-10-20
See this:
[https://man.archlinux.org/man/v4l2-ctl.1.en](https://man.archlinux.org/man/v4l2-ctl.1.en)

As far as I can tell v4l does not store the settings at all.

---

