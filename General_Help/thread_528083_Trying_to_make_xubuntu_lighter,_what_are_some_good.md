---
title: "Trying to make xubuntu lighter, what are some good alternative to default apps?"
date: 2007-08-17
forum: General Help
---

### Post by smartboyathome on 2007-08-17
I am trying to make xubuntu relatively lighter so that it can run on a friend's machine (which currently runs win98) until they can get a new computer. The reason for this is their daughter has an ipod and needs to get it to work. So I decided to take Xubuntu and remaster it for their needs.

So, my question is, what are some lighter alternatives to the default apps in Xubuntu? I already have Seamonkey and am planning to install claws mail on it, but what else can I replace stuff with? Here are some things I am looking to replace:
- gxine (I am probably going to get rid of this and replace it with a media player that can access ipods. Anything that is relitively lightweight?)
- GIMP (I don't know if this is light, but from the looks of it, it isn't. Anything that I can replace it with?)
- Anything else you can think of (not XFCE or Thunar ;))

I would like to keep this as user friendly as possible (though speed is priority #1). I will (possibly if I have time before school starts) compile a list of changes when I am done. Thanks to anyone who helps!

P.S. I am going on a trip for a few days, and will be back monday. Please still respond, as I will reply when I come back!

---

### Post by bonzodog on 2007-08-17
I wouldn't use xubuntu at all on that box, but maybe an ubuntu server install + X + Fluxbox + custom apps to fit as needed. I would ask what apps they actually *need*. Do they really need an image editor, or just a simple paint program? 

Fluxbox or Openbox make for nice desktops, and you could then install, say, pcmanfm for a file manager, xmms for audio, seamonkey for web browsing, pidgin for IM, I would stick with GXine for video app, abiword for word processing, Leafpad for text editor.

---

### Post by smartboyathome on 2007-08-17
The only problem with Fluxbox or Openbox: you have to right click on the desktop to access the menu. I am trying to make a good impression on them (they have only used Windows), so XFCE would probably be my best bet (unless there is another DE that is easy for new people to configure without editing a text file?). I will try the others you mention if I have time before I go on the trip. Also, I would not like to totally build it from the ground up when there is something out there that already has most of my needs with less tweaking (ie: I don't want to use a cli for this, as I don't like using that very much ;))

---

### Post by ugm6hr on 2007-08-17
IceWM is pretty Win98-like, and is very light.  In fact, there are numerous XP / Vista themes for IceWM (have a look in [http://www.box-look.org/index.php?xsortmode=high&page=0&xcontentmode=7311](http://www.box-look.org/index.php?xsortmode=high&page=0&xcontentmode=7311)).  Maybe give that a try?  It's in the Universe repo (I believe).

Instructions below edited from: [http://psychocats.net/ubuntu/minimal#barebones](http://psychocats.net/ubuntu/minimal#barebones)

```
sudo apt-get update
sudo apt-get install icewm menu
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

As for lighter apps:
Opera for web browser worth trying (available direct from [http://www.opera.com/](http://www.opera.com/))
I think there is an mpaint or tpaint or something like that in the repo for image editing (never tried it).
Ipod compatible media player?  You'll be struggling to get one that will run on such old hardware - Exaile *may* work.

Good luck.

---

### Post by kerry_s on 2007-08-17
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
[http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)


Try a truely light distro see what you like. 
If you know enough linux then go custom, nothing beats building the system to the needs.

---

### Post by maybeway36 on 2007-08-17
Don't do a server install unless you want a LAMP server.
I think if it runs win98 then you might be good with regular Xubuntu -try the Live CD first.

---

### Post by kerry_s on 2007-08-17
> **maybeway36 said:**
> Don't do a server install unless you want a LAMP server.
I think if it runs win98 then you might be good with regular Xubuntu -try the Live CD first.

Wrong kind of server install. "server" meaning just the base. he has xubuntu already installed.

---

### Post by kadath on 2007-08-18
gxine should be replaced with VLC for videos and Audacious for audio. gtkpod can be used to put music on iPods.

GIMP isn't really "light," but it's the most featureful image editor for Linux. Although not really in the same league as Photoshop, GIMP is lighter than, say, Photoshop 7.

GQView is nice for image viewing, but Mirage is a little lighter.

---

### Post by Slychilde on 2007-08-18
I second VLC for a video player. 

For a browser - go Epiphany or Firefox.  Epiphany seems to work really well with XFCE.

I'm curious as to what you're going to use for a cd-burning app, if any? :)

---

### Post by smartboyathome on 2007-08-20
Thanks for all the suggestions. I will try all of them. I will post back here when I am done.

---

