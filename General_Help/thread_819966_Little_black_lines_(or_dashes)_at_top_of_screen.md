---
title: "Little black lines (or dashes) at top of screen"
date: 2008-06-05
forum: General Help
---

### Post by MrGrieves on 2008-06-05
Ever since I upgraded to Hardy Heron, I've had little stacks of little black lines on my monitor (see attached screenshot).

Any idea what this is?

The lines are usual at the complete top of the screen but if for some reason the resolution changes on my monitor, the lines move down (but not back up).

The lines appear in all applications including a game I like to play (Defcon).

My graphics card is an Nvidia FX 5200 which I configured using EnvyNG.

Thanks in advance

Mark

---

### Post by iaculallad on 2008-06-05
Are you currently using compiz?

---

### Post by MrGrieves on 2008-06-06
> **iaculallad said:**
> Are you currently using compiz?

I never installed it but it comes up when I grep for it on ps -ef.  Does it come on by default in Hardy?

---

### Post by MrGrieves on 2008-06-07
So should I remove all the compiz packages on my system:


```

dpkg -l |grep compiz
ii  compiz                                     1:0.7.4-0ubuntu6                                   OpenGL window and compositing manager
ii  compiz-core                                1:0.7.4-0ubuntu6                                   OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.7.4-0ubuntu1                                     Collection of extra plugins from OpenCompositing for Com
ii  compiz-fusion-plugins-main                 0.7.4-0ubuntu5                                     Collection of plugins from OpenCompositing for Compiz
ii  compiz-gnome                               1:0.7.4-0ubuntu6                                   OpenGL window and compositing manager - GNOME window dec
ii  compiz-plugins                             1:0.7.4-0ubuntu6                                   OpenGL window and compositing manager - plugins
ii  compizconfig-backend-gconf                 0.7.4-0ubuntu1                                     Settings library for plugins - OpenCompositing Project
ii  libcompizconfig0                           0.7.4-0ubuntu1                                     Settings library for plugins - OpenCompositing Project


ps -ef|grep compiz
home      6275  6122  0 May25 ?        00:00:00 /bin/sh /usr/bin/compiz --sm-client-id default0
home      6343  6275  2 May25 ?        06:40:14 /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding --sm-client-id default0 core ccp
home      6403  6343  0 May25 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decorator
home      6404  6403  0 May25 ?        00:00:00 /bin/sh /usr/bin/compiz-decorator

```

Thanks

---

### Post by WIGGMPk on 2008-11-07
I am experiencing the same issue, is there a possible fix to this??


I have noticed that restarting the x-server via CTRL+ALT+BACKSPACE will (most of the time) fix the issue, but this becomes a pain to do every time I turn on my comp.

BTW: I am using Compiz + Emerald, this was not an issue untill I had to reinstall Hardy (amd64) using the same/similar setup.

---

### Post by 987poiuytrewq on 2008-12-04
I am also having the same issue, the little black lines do disappear if I restart the X server (CTRL-ALT-BACKSPACE). But remain if I switch windows managers eg to metacity. Any help removing them would be appreciated.

Using gnome + compiz on intrepid.

---

### Post by thirdrev on 2009-02-18
I am having a similar issue; have any of you found something that works to get rid of these lines?

---

### Post by Orange Kingdom on 2009-05-01
Me too. Small black lines at top of screen (Ubuntu Jaunty)

I just tried to change the boot options framebuffer. Now the dashes are gone.

---

### Post by Tulsapoke on 2009-08-08
I have this same problem with a line of dashes across my screen. Usually it is across the taskbar but creeps down up to an inch.  I am going to try this frame buffer [disable trick]("https://wiki.ubuntu.com/FrameBuffer") since you have mentioned this as a fix.


Well the framebuffer trick had no effect on my system.  I guess I will live with the dashes till a fix is posted.

---

### Post by Cethin on 2009-10-20
Modifying the Framebuffer did not help me, however, I removed Compiz and the lines are now gone!

---

