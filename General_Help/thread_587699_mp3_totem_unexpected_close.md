---
title: "mp3 totem unexpected close"
date: 2007-10-23
forum: General Help
---

### Post by s-lime on 2007-10-23
When I play mp3, player immediatelly closes. This does not happen with avi.

Error:

> ** (totem:5289): CRITICAL **: bacon_video_widget_common_get_vis_quality: assertion `q < G_N_ELEMENTS (vis_qualities)' failed
JACK tmpdir identified as [/dev/shm]

** (totem:5289): CRITICAL **: bacon_video_widget_common_get_vis_quality: assertion `q < G_N_ELEMENTS (vis_qualities)' failed
Segmentation fault (core dumped)

Please help

---

### Post by s-lime on 2007-10-23
anyone? This is serious problem, because it is appaearing until **update to 7.10!!!**

---

### Post by resli on 2007-11-25
I had the same problem, and it was solved by defining the size for the visual effects, Since I have a german version of totem I can't guide you exactly, but if you open totem and go into options, on the second panel there are two options: one defining what visualization to use and the other one the size of the visualization, In my case the second one wasn't defined.

greatings Resli

---

### Post by guixmax on 2008-01-27
I had the same problem. And I solved as resli suggeted.
I have English version of totem.
In the "edit" menu select "preferences". In the "Display" tab choose the "Visualization size"

---

