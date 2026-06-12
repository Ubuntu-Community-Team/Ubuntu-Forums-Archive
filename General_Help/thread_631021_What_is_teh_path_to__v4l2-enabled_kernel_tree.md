---
title: "What is teh path to  v4l2-enabled kernel tree"
date: 2007-12-04
forum: General Help
---

### Post by yinglcs2 on 2007-12-04
Hi,

i am trying to enable v4l2 in vlc trunk in ubuntu. 
So i am trying to run 'configure' myself and it asks for 'v4l2-enabled kernel tree'

Can you please tell me what should I put for 'v4l2-enabled kernel tree' in ubuntu 7.10?

  --enable-v4l2           Video4Linux2 input support (default disabled)
    --with-v4l2=PATH       path to a v4l2-enabled kernel tree
    --with-dvb=PATH       path to a dvb- and v4l2-enabled kernel tree

---

### Post by geraldm on 2007-12-04
The path to the linux kernel source, where you have selected in the .config file these options:
CONFIG_VIDEO_V4L2=y
CONFIG_DVB=y
Perhaps the path to the top directory of the linux kernel source would do.

Gerald

---

