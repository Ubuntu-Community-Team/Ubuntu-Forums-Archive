---
title: "Which is the real HowTO for Compiz/Beryl/XGl/Whateveritscalled?"
date: 2006-10-25
forum: General Help
---

### Post by bg1256 on 2006-10-25
I'm running Dapper, and I'd love to install the eye-candy, but the recent fork has left me confused.

If I want to install this, does anyone know which howto is going to work for me?

PS: nvidia Geforce 7600 card, which I just got up and running today.

---

### Post by mushroom on 2006-10-26
To make it really simple:

sudo apt-get install xserver-xgl compiz-core compiz-plugins compiz-gnome

Make sure you're using the official NVidia driver.

in KDE: just log out, select the "Xgl" session and log in.

in Gnome: drop this in /etc/gdm/gdm.conf-custom :
```

[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true

```

then log out and log back in.

then issue the command:
compiz --replace decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water &

add and remove plugins to your content, and you should be set. If you end up with no titlebars on the windows, issue the command gnome-window-decorator, and your metacity theme should appear. However, should you want something a bit more sophisticated (yet much more hack-y), check [this thread]("http://ubuntuforums.org/showthread.php?t=272104").

---

