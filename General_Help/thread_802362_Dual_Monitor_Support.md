---
title: "Dual Monitor Support"
date: 2008-05-21
forum: General Help
---

### Post by ricanelite on 2008-05-21
Okay I have another LCD Monitor that I will like to setup with my Hvidia Graphics Card. Currently right now I'm using Ubuntu Linux Hardy and have nvidia-settings installed. Now I will like to both of my monitors setup so if I want to move a window to my other monitor I drag the window to the end of the screen and it will go on over to my other monitor. I also have Compiz with the Desktop Cube. The main reason I want to do this is because I will like to my virtualbox w/windows xp running on one monitor and have my Ubuntu/Gnome Desktop in another. Now I when i install nvidia-settings and got it up and running I got my second monitor one but it showed the desktop and I could not drap any windows to it. Now when I selected twin view it gave me a error message. Is there a howto anywhere on the web for nvidia cards on how to get this to work. I'm a new to this part of linux. I'm not 100 percent sure how to work around the xorg.conf. Is there a application out that could do it? Please let me know thanks!

---

### Post by compgeek83 on 2008-05-21
I had to do a little bit of playing to get my setup to work also.

nvidia-settings worked for me but the settings it applied would not stick after a reboot.

I ended up copying the xorg.conf that is shows when you click "save to x configuration" then click preview and pasting it into the real xorg.conf myself once I got the settings the way I wanted them.

sudo gedit /etc/X11/xorg.conf in a terminal gets you into your xorg.conf

---

### Post by tigrezno on 2008-05-21
yeah, it's easy, just use the Twin View feature, adjust the resolutions and make the changes to /etc/X11/xorg.conf.

restart and that's all.

---

### Post by pvthodson on 2008-05-30
Hello everyone I need a little help on my new system. I want to setup my ubuntu hardy haron system to big desktop with two monitors but I cant seem to find a how-to that works and I think it is because of the way I have it setup. I have a ati graphics card with a dvi and vga connection on the back in which I have two monitors connected but I cant seem to find out why it wont work. I have installed the ati catalyst control center that gives me the option to use big desktop but it always comes out with horrible graphics or none at all. I have tried multiple configuration in the xorg.conf file but none have worked any help would be appreciated and let me no if you need any particualar specifics on my system.

---

