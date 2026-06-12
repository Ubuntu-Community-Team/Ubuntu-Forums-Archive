---
title: "Choppy videos and animations since 18.04"
date: 2018-05-15
forum: General Help
---

### Post by stepheny on 2018-05-15
Since upgrading from 17.10 to 18.04 my video streaming and amimations have become choppy. Running glxgears it can be seen that the animation stops and then starts again every 3 seconds or so. The same with video streaming, the picture stutters every 3 seconds. This happens using the Intel GPU and also using the nVidia GPU via Bumblebee (Optirun).

Anybody have an idea what could be causing this?

---

### Post by stepheny on 2018-05-16
I fixed the problem by removing nvidia-settings and disabling the gnome extension "NVIDIA GPU Stats Tool".

---

### Post by cb2018 on 2018-06-29
removing nvidia settings also removes CUDA, which i need.

so this solution wont wor for me

 does this have something to do with window preview ?

---

