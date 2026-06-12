---
title: "Accidental Delete of libesd.so.0"
date: 2007-02-07
forum: General Help
---

### Post by ghandi69_ on 2007-02-07
Hey all, I was trying to remove a link, and accidently delete libesd.so.0...

I was trying to get sound to work in my edgy 64 quake 3 install.. the game works fine otherwise..

1st... any idea how to undo my '''' sudo rm /usr/lib/libesd.so.0''' command?

2nd.. any ideas how to get sound working in quake 3?

---

### Post by ghandi69_ on 2007-02-07
As it turns out... this problem is more serious than I originally thought..

apparently libesd.so.0 is required to boot into the window manager!!!

I am now posting from a live cd.... 

ahh.. the beautys of linux... looking forward to learning how to get out of this one!

Any help would be much appreciated!!

::further info;:

I was following the guide in the getting started guide about getting sound to work in gnome...

I make a link from libesd.so.0 to libesd.so.1 ......... cuz the guide said... so I went through that and it didn't help at all, so I tried to undo my steps.. and when removing the link.. I removed so.0 instead of 1!!

I tried now linking 1 back to zero or copying 1 to zero.. but I don't understand whats really in there so I don't know why that is a silly idea and why it doesn't work...

---

### Post by ghandi69_ on 2007-02-07
** found a fix **

It turns out.. I can just do a sudo apt-get install libesd0 and restore that information...

If anyone reads this and sees a reason why something else might be affected.. feel free to comment

---

### Post by bettlebrox on 2007-02-07
Have a look at the Linux Gamers FAQ:

[http://icculus.org/lgfaq/#q3alsa](http://icculus.org/lgfaq/#q3alsa)

---

