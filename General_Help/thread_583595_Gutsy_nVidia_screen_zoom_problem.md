---
title: "Gutsy nVidia screen zoom problem"
date: 2007-10-20
forum: General Help
---

### Post by Surkow on 2007-10-20
Like a lot of people who installed Gutsy, I also had a resolution problem after installing Gutsy. After messing with it and using the restricted drivers module to activate the nVidia graphics driver I didn't get what I expected. Both of my screens from my dual setup were recognized properly. There was just one problem...it was if I was using the zoom plugin from Compiz the whole time on both screens. Even after disabling anything 3D related the desktop still didn't show within my screen borders. In the end I just put back my old xorg.conf back from Feisty. But this solution won't solve the problem that not all programs are screen borders aware (for example games which go fullscreen over two screens instead of one).

---

### Post by repawn on 2007-10-20
I am not sure if this will help - I used the gksu nvidia-settings to setup the the dual monitor on my system - the screens and graphics menu item did not work for me at all. I had to play with the nvidia settings abit and then save them to the xorg file.

---

### Post by Surkow on 2007-10-21
> **repawn said:**
> I am not sure if this will help - I used the gksu nvidia-settings to setup the the dual monitor on my system - the screens and graphics menu item did not work for me at all. I had to play with the nvidia settings abit and then save them to the xorg file.

That's exactly what I did. After reading about it some more people claim that you need to remove a line about a virtual desktop from your first monitor. But currently I can't test it because I used envy instead of the restricted drivers.

---

### Post by Cyberbian on 2007-10-21
Here is a link for the soluton to the small video issue.
[http://psubuntu.com/forum/viewtopic.php?t=13](http://psubuntu.com/forum/viewtopic.php?t=13)

---

