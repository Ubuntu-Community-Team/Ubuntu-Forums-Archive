---
title: "Kernel panic after Usplash update"
date: 2007-11-28
forum: General Help
---

### Post by PlantHead on 2007-11-28
Ok.
Changed  /etc/usplash.conf
to

xres=800
yres=600

and then updated the theme by running
sudo update-usplash-theme usplash-theme-ubuntu

now when I boot up I get a Kernel panic message.

I've logged in using the live CD and changed usplash.conf back to 
xres=1024
yres=768 

but how can I now update the theme?
how can I run sudo update-usplash-theme usplash-theme-ubuntu
from within the livecd environment.


Any help would be brilliant

---

### Post by jken146 on 2007-11-28
I had quite a similar problem very recently.  Take a look at these threads:
[http://ubuntuforums.org/showthread.php?t=620860](http://ubuntuforums.org/showthread.php?t=620860)
[http://ubuntuforums.org/showthread.php?t=622002](http://ubuntuforums.org/showthread.php?t=622002)

---

