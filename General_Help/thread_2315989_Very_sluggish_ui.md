---
title: "Very sluggish ui"
date: 2016-03-04
forum: General Help
---

### Post by hseyin_fahri_uzu on 2016-03-04
I'm using ubuntu 15.10 with fglrx-updates driver on amd 7850k, 8GB RAM and SSD drive. I was using openSUSE for a long time and i had no problem about ui and graphical performance on os level even i turned on pretty much all effects in openGL. On ubuntu 16.04 Beta i had also no problem at all(i had to switch to 15.10). But for ubuntu 15.10 some (but not all) ui animations lags a lot. I'm uploading a short video so you may see it. Sometimes resizing windows lags about a second. I can watch 1080p 60fps videos without any issue on youtube full screen but whenever i want to exit full screen it may take 10 seconds because the animation lags a lot.Scrolling is sluggish on firefox. I also had to turned on AMD CCC v-sync because screen tearing was a problem but i don't think it may effect the performance. Glxgears is outputting 60fps on the terminal so i don't know what is the issue here.

[https://vid.me/A14d](https://vid.me/A14d)

    ```
glxinfo | grep OpenGL
    OpenGL vendor string: Advanced Micro Devices, Inc.
    OpenGL renderer string: AMD Radeon(TM) R7 Graphics  
    OpenGL core profile version string: 4.4.13399 Core Profile Context 15.201.1151
    OpenGL core profile shading language version string: 4.40
    OpenGL core profile context flags: (none)
    OpenGL core profile profile mask: core profile
    OpenGL core profile extensions:
    OpenGL version string: 4.5.13399 Compatibility Profile Context 15.201.1151
    OpenGL shading language version string: 4.40
    OpenGL context flags: (none)
    OpenGL profile mask: compatibility profile
    OpenGL extensions:
```
 --

    ```
fglrxinfo
    display: :0  screen: 0
    OpenGL vendor string: Advanced Micro Devices, Inc.
    OpenGL renderer string: AMD Radeon(TM) R7 Graphics  
    OpenGL version string: 4.5.13399 Compatibility Profile Context 15.201.1151

```


Thank you

---

### Post by s0urCr34m on 2016-03-05
"Scrolling is sluggish on firefox"  Have you tried Chrome?

---

### Post by QIII on 2016-03-05
Unfortunately, trying Chrome does not solve the problem with Firefox.

In any case, the question is about the UI in general.

---

