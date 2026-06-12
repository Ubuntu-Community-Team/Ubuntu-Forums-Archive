---
title: "Software recommendation"
date: 2018-04-22
forum: General Help
---

### Post by raaz2053 on 2018-04-22
I recently installed Openshot video editor on my ubuntu running machine but i'm unable to utilize my GeForce GT 520MX card for rendering. Cpu rendering is far slow and oveheat my laptop samsung 300v5A. How can i uitilize my gpu card for video editing and rendering? If it is'nt possible with openshot please recommend me a good video editing software. thanks in advance :) ):P
all necessary drivers for my gpu hardware is installed in my device.

---

### Post by HermanAB on 2018-04-22
Err... this is not actually due to Openshot.  It means that FFMPEG, OpenGL and other utilities are not installed properly and the machine is doing rendering on the CPU, but it will be so regardless of which video editor you use.   You need to work on the FFMPEG and OpenGL installation and verify the resulting fps with 'gears'.

---

