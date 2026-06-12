---
title: "Screensaver as your wallpaper"
date: 2008-05-30
forum: General Help
---

### Post by Bigtime_Scrub on 2008-05-30
I wanted to see how this would look but Im afraid to do it because I havent been able to find a way to turn it off. 



The first way I know how to do this is by removing nautilus and using xscreensaver as a replacement. 
```
gconftool-2 &#8212;type bool &#8212;set /apps/nautilus/preferences/show_desktop false /usr/lib/xscreensaver/glmatrix -root
```

I also understand there is a second way which lets you loop movies, video, and screensavers in the same way but its more complex.

I would have to compile so I would need these tools.

```
sudo apt-get install build-essential libx11-dev x11proto-xext-dev libxrender-dev libxext-dev cvs
```

Then I have to install xwinwrap:
```
cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps co xwinwrap
cd xwinwrap
make
sudo cp xwinwrap /usr/bin
```

After this I could set a video as my desktop wallpaper. I would run the video using mplayer.

```
xwinwrap -ni -fs -s -st -sp -b -nf -- mplayer -wid WID -nosound "Steal This Film II.Xvid.avi" -loop 0
```

This code would also allow me to use a screensaver as wallpaper.

```
nice -n 15 ./xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- /usr/lib/xscreensaver/glmatrix -root -window-id WID
```



My questions are:

1. How do you turn off this feature if you decide you dont like it.
2. Are they compatible with Gnome or will I have to switch to KDE, or even something else?
3. Can I adjust sound with the video and if so how?
4. Has anyone attempted this before? I'd like some advice and tips before I try it because I finally got everything just perfect on my Ubuntu and I dont wanna screw it up.

---

### Post by Bigtime_Scrub on 2008-05-31
I guess I'll give it a little bump. I think it would be really cool to get working.

---

### Post by jpeddicord on 2008-06-01
To set the screensaver as a background, run the following to first disable Nautilus on the desktop:
```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
```

Then, to start the screensaver as your background, run this:
```
/usr/lib/xscreensaver/glmatrix -root
```
You may want to add it as a startup entry in System > Preferences > Session to make sure it stays enabled.

To disable and restore Nautilus's display, first remove the startup entry, and then:
```
killall glmatrix
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop true
```

Sign out and back in again, and Nautilus should be drawing the desktop as normal.

---

### Post by Bigtime_Scrub on 2008-06-03
It worked. 

Not as cool as I thought it would be though. The actual screen saver as a background was too small, it would stay over all my other windows which means I cant do anything while I use it, and it didn't play nice with compiz. If you bring up the cube and try to rotate it your system slows down and the screensaver will jump around. I'm going to play around a little more with it. Maybe there are some setting it has that will let me configure it better.

It also feels really weird not having nautilus.

---

### Post by Morton's Red Stapler on 2008-06-13
I remember on gutsy, the background was transparent, like the flying toasters, the black was replaced by whatever you had as your wallpaper, but the toasters were full opacity, is there a way to get that to work in hardy?

---

### Post by schmidtbag on 2008-06-16
this is cool but how do i get the icons while the screensaver is running?  both what scrub and jacob said do the exact same thing but neither show the icons.  i'd really like to do this instead of a plain wallpaper

---

