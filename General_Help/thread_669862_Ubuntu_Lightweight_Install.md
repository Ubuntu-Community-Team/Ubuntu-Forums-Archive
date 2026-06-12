---
title: "Ubuntu Lightweight Install"
date: 2008-01-16
forum: General Help
---

### Post by Phixion on 2008-01-16
Ubuntu is a great OS but my main issue is the amount of programs it installs by default, now I know some people appreciate this, but when you have a fast connection and have the option to pick and choose what you want on your computer - you'd rather go that route than have it bogged down with stuff you don't want.

I've tried installing ubuntu server and installing gnome manually, problem is that getting gnome tends to drag in all the default programs you get in a "normal" ubuntu install.

I've followed a few lightweight guides, none of which I've had much luck with.

So, does anyone know a good reliable guide to help me setup a lightweight install of Ubuntu, basically the base packages and GNOME, nothing more.

Cheers

---

### Post by aysiu on 2008-01-16
If you've already tried a few lightweight guides, your best bet is to just go through Synaptic and try uninstalling stuff you don't need.

There isn't that big a difference between base packages-Gnome and Ubuntu's default packages.

---

### Post by Phixion on 2008-01-17
Well, I'd prefer not to install any extra packages in the first place.

Are there any plans to release an "Ubuntu Lite" or something to that effect that will let people choose what they want installed?

It's very much needed, I enjoy the useability of Ubuntu so would rather stick with it than move to a lightweight distro.

---

### Post by aysiu on 2008-01-17
> **Phixion said:**
> Well, I'd prefer not to install any extra packages in the first place.

Are there any plans to release an "Ubuntu Lite" or something to that effect that will let people choose what they want installed?

It's very much needed, I enjoy the useability of Ubuntu so would rather stick with it than move to a lightweight distro.
It already exists in the form of a "server" install from the Alternate CD or a regular installation from the mini.iso. Various guides explain how to do this, but you said you already tried some, so I figured it wouldn't make sense to link you to those.

If you want a lightweight distro, I wouldn't even bother with Gnome. Gnome and KDE are the two heaviest environments. I would try Xubuntu or Fluxbuntu instead.

---

### Post by Phixion on 2008-01-17
By lightweight I mean installing less programs by default, therefore making it a light install.

I have a pretty decent system so using a lightweight DE/WM isn't really needed, I just don't want to install Ubuntu with stuff I don't need/use. I've already tried a server install but as soon as I install GNOME it tends to drag all the apps/games along with it, which really defeats the purpose of installing the server version, what package do I need to get to install just a clean GNOME desktop?

If you have any links to a comprehensive lightweight install I'd appreciate it, it's highly likely that I've missed some guides floating around.

Cheers

---

### Post by aysiu on 2008-01-17
I would do a server install and then install *gnome-core*: ```
sudo apt-get update
sudo apt-get install gnome-core gdm xorg
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by notwen on 2008-01-17
Try installing the following after a server install.  This would be the bare minimum for GNOME.  If this doesn't work, perhaps you should look into other distros that are more customizable.  Good luck. =]
```
sudo apt-get install gnome-core gdm xorg
```


---EDIT---

aysiu beat me and aysiu's commands are a bit more thorough. =]

---

### Post by jken146 on 2008-01-17
XFCE is much lighter than GNOME and has pretty much the same features and feel.  There are of course other, lighter WMs/DEs but XFCE is nice and complete in itself.

---

### Post by Phixion on 2008-01-17
> **jken146 said:**
> XFCE is much lighter than GNOME and has pretty much the same features and feel.  There are of course other, lighter WMs/DEs but XFCE is nice and complete in itself.

I'm not after a lightweight DE though :) GNOME runs fine, I just don't want / need 90% of the apps it installs by default.

I'll try the suggestions above, cheers!

---

