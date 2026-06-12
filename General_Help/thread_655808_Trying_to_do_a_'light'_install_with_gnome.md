---
title: "Trying to do a 'light' install with gnome"
date: 2008-01-01
forum: General Help
---

### Post by MangasColoradas on 2008-01-01
I tried it with the 6.0.6.1 alternate CD, it has an 'install server' option.

I followed this guide [http://tuxoblog.blogspot.com/2007/06/ubuntu-light.html](http://tuxoblog.blogspot.com/2007/06/ubuntu-light.html)

One thing was, there was no 'gnome-core' to be found....it suggested 'gnome-data-manager' or something instead. I enabled universe and multiverse repos.

I want a gnome desktop without installing 'gnome-desktop' as that has a lot of extra stuff. The guide doesn't mention Nautilus either, should I install it? Or maybe Thunar?

If I use the 7.10 server CD will I get 'gnome-core'?

EDIT
I guess I could just install XFCE4?

---

### Post by empthollow on 2008-01-01
well, i don't see a gnome-core or similar package in my repositories either.  i would guess that this is because he was using a different flavor of ubuntu because package names change btw versions.   i would install gnome-session because that is the command that tells xorg to start gnome.  i would put gnome-session in the .xinitrc and run "startx"  if there are any errors or you don't get nautilus, that's when i would start installing other packages.  i would wager that alot of the packages you need will be dependancies of gnome-session.

---

### Post by MangasColoradas on 2008-01-01
Thanks mate, I just looked at it in Synaptic and it looks promising.

If I install XFCE I can use Synaptic to try and get whats needed for gnome as it lists dependencies, recommendations and suggestions. It should make it easier than trying to just use apt-get.

---

### Post by empthollow on 2008-01-01
yep, synaptic rocks.  
fyi:
if you use 7.10 apt-get has an "autoremove" option you can use to automatically get rid of unused libraries and other packages wasting space.  i believe there is a program called gtk-orphan in the repos for 6.06 that will work similarly.

---

### Post by g2g591 on 2008-01-01
you sure you don't want the latest and greatest, 7.10 6.10 is pretty darn out of date (albiet still supported for servers and people who refuse to upgrade)

---

### Post by jken146 on 2008-01-01
XFCE is pretty similar to Gnome IMO and a good deal lighter.

---

### Post by MangasColoradas on 2008-01-02
I am gonna use the 7.10 mini CD this time g2 and do the install without selecting anything, then I will install Xfce and play around with it. 

Does the 7.10 sever edition have the option not to install LAMP? If so that might be quicker as everything has to be downloaded with the mini CD.

---

### Post by MangasColoradas on 2008-01-02
Used the mini-CD and then did this from the command line


```
sudo aptitude install gdm xorg xfce4 firefox synaptic
```

Good guide here [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

So far I have just removed the display drivers that were installed by xorg, it installed all of them, so I just left ATI and VESA installed.

It has also installed some openoffice stuff but I will remove that too.

I might give up on the lightweight gnome desktop idea and just stick with xfce4, it seems fine.

---

### Post by empthollow on 2008-01-02
if you like xfce you might try xubuntu, it is a lightweight flavor of ubuntu featuring xfce as the desktop.

---

### Post by LowSky on 2008-01-02
may I suggest Debian Etch, its what ubuntu is based, and is more customizable.

---

### Post by MangasColoradas on 2008-01-02
By doing this I have a lighter version of Xubuntu, empthollow. I am just playing around really, I still have Ubuntu as my main OS.

LowSky, I tried Debian and had a bug immediately, it wouldn't mount any volumes. However, I am still very new to Linux and I am sure I will be trying Debian again in the future.

For now, I wanted to install a very lightweight system to compare speed and learn a little.
:)

---

### Post by MangasColoradas on 2008-01-02
I have just installed gnome-core from synaptic so it installed the dependencies too, these include nautilus and metacity.

Metacity didnt start by itself so I added it to the session start ups, since then I have only been able to use 'failsafe gnome'. Oh well.

I removed it from start up and I still get a brown screen. It's not important as I am just experimenting anyway.

---

