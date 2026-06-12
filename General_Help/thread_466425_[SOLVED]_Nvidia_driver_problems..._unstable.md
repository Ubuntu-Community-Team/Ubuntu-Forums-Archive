---
title: "[SOLVED] Nvidia driver problems... unstable?"
date: 2007-06-06
forum: General Help
---

### Post by viciouslime on 2007-06-06
If I run 3d games sometimes everything will completely lock for about 30-40 seconds before suddenly carrying on as normal. If I run glxgears I get the following output:

dan@lime:~$ glxgears
66595 frames in 5.0 seconds = 13318.896 FPS
66940 frames in 5.0 seconds = 13387.930 FPS
66060 frames in 5.0 seconds = 13211.960 FPS
67059 frames in 5.0 seconds = 13411.625 FPS
67048 frames in 5.0 seconds = 13409.468 FPS
67012 frames in 5.0 seconds = 13402.234 FPS
67074 frames in 5.0 seconds = 13414.682 FPS
67084 frames in 5.0 seconds = 13416.787 FPS
67043 frames in 5.0 seconds = 13408.487 FPS
67065 frames in 5.0 seconds = 13412.973 FPS
67006 frames in 5.0 seconds = 13401.133 FPS
66974 frames in 5.0 seconds = 13394.629 FPS
67055 frames in 5.0 seconds = 13410.925 FPS
67088 frames in 5.0 seconds = 13417.412 FPS
67060 frames in 5.0 seconds = 13411.955 FPS
28921 frames in 34.6 seconds = 835.239 FPS
1 frames in 28.0 seconds =  0.036 FPS
58303 frames in 5.0 seconds = 11660.516 FPS
58329 frames in 5.0 seconds = 11665.648 FPS
58316 frames in 5.0 seconds = 11663.098 FPS
58311 frames in 5.0 seconds = 11662.109 FPS


Everything runs fine for quite some time, then there is the lockup, then everything carries on but about 2000fps slower...

I have a 7800GT with the binary nvidia driver installed from the repos. I have had this problem on breezy, dapper, edgy, feisty and I've even tried it on gutsy and get the same...

Any ideas what is wrong here?

---

### Post by Crafty Kisses on 2007-06-06
> **viciouslime said:**
> If I run 3d games sometimes everything will completely lock for about 30-40 seconds before suddenly carrying on as normal. If I run glxgears I get the following output:

dan@lime:~$ glxgears
66595 frames in 5.0 seconds = 13318.896 FPS
66940 frames in 5.0 seconds = 13387.930 FPS
66060 frames in 5.0 seconds = 13211.960 FPS
67059 frames in 5.0 seconds = 13411.625 FPS
67048 frames in 5.0 seconds = 13409.468 FPS
67012 frames in 5.0 seconds = 13402.234 FPS
67074 frames in 5.0 seconds = 13414.682 FPS
67084 frames in 5.0 seconds = 13416.787 FPS
67043 frames in 5.0 seconds = 13408.487 FPS
67065 frames in 5.0 seconds = 13412.973 FPS
67006 frames in 5.0 seconds = 13401.133 FPS
66974 frames in 5.0 seconds = 13394.629 FPS
67055 frames in 5.0 seconds = 13410.925 FPS
67088 frames in 5.0 seconds = 13417.412 FPS
67060 frames in 5.0 seconds = 13411.955 FPS
28921 frames in 34.6 seconds = 835.239 FPS
1 frames in 28.0 seconds =  0.036 FPS
58303 frames in 5.0 seconds = 11660.516 FPS
58329 frames in 5.0 seconds = 11665.648 FPS
58316 frames in 5.0 seconds = 11663.098 FPS
58311 frames in 5.0 seconds = 11662.109 FPS


Everything runs fine for quite some time, then there is the lockup, then everything carries on but about 2000fps slower...

I have a 7800GS with the binary nvidia driver installed from the repos. I have had this problem on breezy, dapper, edgy, feisty and I've even tried it on gutsy and get the same...

Any ideas what is wrong here?
I can't even install my Drivers, it messes up everything, but anyways, what's all your system specs?

---

### Post by viciouslime on 2007-06-10
FIXED IT! This problem has plagued me for over a year, for the solution see here: [http://viciouslime.co.uk/index.php?view=article&catid=3%3Ahowtos&id=2%3Ahowto-fix-pixelview-nvidia-7800gt-instability-under-linux&option=com_content&Itemid=3]("http://viciouslime.co.uk/index.php?view=article&catid=3%3Ahowtos&id=2%3Ahowto-fix-pixelview-nvidia-7800gt-instability-under-linux&option=com_content&Itemid=3")

Too long to post here, sorry.

---

