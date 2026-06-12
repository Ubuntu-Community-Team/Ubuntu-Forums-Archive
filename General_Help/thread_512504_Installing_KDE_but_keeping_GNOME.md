---
title: "Installing KDE but keeping GNOME"
date: 2007-07-29
forum: General Help
---

### Post by b0ng0 on 2007-07-29
Basically I have GNOME set up as I want it, but fancy having the option to use KDE but keep KDE programs in KDE and not have them appear in my GNOME menus. I fancy just installing the KDE apps I need (there are a lot of ones I won't use that come with Kubuntu).
I have tried looking on Synaptic for KDE but there are so many different things I could download (e.g. kde, kdecore, kubuntu-desktop) that I have no clue which one to choose. Which one should I download and install for what I want? Bearing in mind, I just want the option to switch between desktop environments, not install the whole of kubuntu.

Thanks

---

### Post by FluffyElmo on 2007-07-29
From the Kubuntu docs it sounds like you can install* kubuntu-desktop* choose gdm as your login manager and switch back and forth between the two desktops.
[https://help.ubuntu.com/6.10/kubuntu/about-kubuntu/C/wonderful-linux.html#sect-switching-desktops]("https://help.ubuntu.com/6.10/kubuntu/about-kubuntu/C/wonderful-linux.html#sect-switching-desktops")

Assuming this is more or less what you want to do installing the whole of Kubuntu shouldn't affect performance while under Gnome, it just uses disk space.

---

### Post by aysiu on 2007-07-29
If you don't want the whole Kubuntu, install *kde-core*

---

### Post by b0ng0 on 2007-07-30
I tried installing just "kde" but this installed a whole load of apps (sooo many) and they just took over my GNOME menus so I uninstalled it. Does kde-core just install the environment and not all the gazillions of apps that I don't need? :)

Thanks

---

### Post by aysiu on 2007-07-30
> **b0ng0 said:**
> I tried installing just "kde" but this installed a whole load of apps (sooo many) and they just took over my GNOME menus so I uninstalled it. Does kde-core just install the environment and not all the gazillions of apps that I don't need? :)

Thanks
Yes. In order from small to large:

kdebase
kde-core
kubuntu-desktop
kde

---

### Post by b0ng0 on 2007-07-30
Oh, guess I couldn't have chosen a worse option then :-s

What is the main difference between kdebase and kde-core?

---

### Post by aysiu on 2007-07-30
kdebase is barely functional. It just has a KDE session... and that's it.

kde-core has the basics for functionality with very few frills. In fact, in addition to kde-core, you may also want to install kde-guidance so you can graphical configure screen resolutions.

---

### Post by b0ng0 on 2007-07-31
Ok cool i'll try installing kde-core. One last thing, ;) is there anyway to keep the programs in kde and gnome seperate so that they only appear depending on what session you choose (i.e. kde programs only appear in kde, likewise for gnome)? Thanks again.

---

### Post by aysiu on 2007-07-31
> **b0ng0 said:**
> Ok cool i'll try installing kde-core. One last thing, ;) is there anyway to keep the programs in kde and gnome seperate so that they only appear depending on what session you choose (i.e. kde programs only appear in kde, likewise for gnome)? Thanks again.
[This](http://ubuntuforums.org/showthread.php?t=123969) may help a little, but you'll still have to do some manual menu editing.

---

