---
title: "after linux kernel update today resolution all wrong on screen..."
date: 2014-12-13
forum: General Help
---

### Post by shantiq on 2014-12-13
...   including webpages icons everything has gone too wide

how can i reset it all ?
I use nvidia and lxde

> shantiq@shantiq-00000000000000000000000:~$ xrandr --current
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0 


but my screen  is 1600x900    so what has happened?   it is not seen

[ATTACH=CONFIG]258560[/ATTACH]

---

### Post by Groot on 2014-12-13
I'm guessing you have to re-install the NVidia drivers.

---

### Post by shantiq on 2014-12-13
thank you very much Groot    i really did not think of doing that

worked fine!   plumped for the one at the bottom of the list and all back 


[B]i shall say it again this is why [COLOR=#800000]i love this community[/COLOR]    people helping people  ...    one day the whole world will be thus ...


[/B]> shantiq@shantiq-00000000000000000000000:~$ xrandr --verbose | grep *current  **1600x900** (0x24e)  108.0MHz +HSync +VSync *current +preferred


---

