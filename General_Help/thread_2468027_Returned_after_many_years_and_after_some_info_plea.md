---
title: "Returned after many years and after some info please"
date: 2021-10-16
forum: General Help
---

### Post by mirdragon on 2021-10-16
I've not used Ubuntu as a desktop for many years and have decided to get back into using it as my main system and only use windows if i need to.

 I've installed the current 20.04 desktop version and this is working with all my stuff (I did try mint but it didn't like my nvidia gtx1050ti)

One thing I want to get working is a decent photo application so can process my raw images without need of going back into windows to use lightroom or capture one.

I've seen the following progams listed as best alternatives, with there pros and cons, so looking at trying them all

DarkTable, digiKam and Corel Aftershot.

But when look at the Aftershot info it says **_The Unity desktop environment is not supported for version 16.10 or later_**,

So does this mean it won't work with 20.04 desktop? will I need to install a different flavour of Ubuntu (ie Mate), If I have to install Mate will I get the same compatibility with applications? Will I have to perform a clean install?

Thanks

---

### Post by osse7 on 2021-10-16
I have no skills about these progs; but 16.10 stands for october 2016, so everything newer is no more supported.
It's time to digg for linux alternatives (ppa/github ...) like :  [https://github.com/luong-komorebi/Awesome-Linux-Software](https://github.com/luong-komorebi/Awesome-Linux-Software)  or wider search: [https://duckduckgo.com/?t=ffab&q=ppa+ubuntu+aftershot&ia=web](https://duckduckgo.com/?t=ffab&q=ppa+ubuntu+aftershot&ia=web)

---

### Post by mirdragon on 2021-10-16
Thanks,

I've installed 20.04 not 16.10, i've already done searching for alternatives and so far the 3 products i've mentioned are the ones interested in

The Linux info for Aftershot says for Ubuntu 14.04 or later, but it's the bit about unity desktop not being supported, are both desktop and mate versions running unity?

---

### Post by grahammechanical on 2021-10-16
Back in the old days the desktop environment for Ubuntu was Gnome and the user interface was Gnome 2. Then the Gnome developers released the Gnome 3 desktop environment and that gave the Ubuntu developers the opportunity to bring out their own user interface which they called Unity. It was installed on Ubuntu by default instead of the Gnome 3 shell user interface.

Unity was developed up to version 7 with the intention of a modified Unity (version 8) becoming a user interface for smartphones and tablets. When it was realized that the Ubuntu based smartphones and tablets were not going to be a commercial success the whole idea of Unity was dropped. For some years now Ubuntu has been using not only the Gnome 3 desktop environment but also the Gnome 3 user interface.

The Mate desktop environment is a fork of Gnome 2. There is an official flavour called Ubuntu Mate for those who like that style of user interface.

The text that you have highlighted in bold is most probably referring to Ubuntu 16.10 not using the Unity user interface. I suggest that the question you should be asking is this: Does this program I want to install depend on having the Unity user interface installed or will it work with Gnome 3 shell? In fact, is this program still under development?

Regards

---

### Post by grahammechanical on 2021-10-16
Actually I am surprised that the Corel organisation is still in business. Its owner made some disastrous business decisions. He switched the product to Linux well before there were sufficient Linux users around that might want to purchase the product.

If you are thinking of using Aftershot Pro 3, then this is the specification for Linux.

> Fedora®19 or Ubuntu® 14.04 or later (64-bit distributions)

[LIST]
[*]64-bit Intel or AMD processor (multi-core processor recommended)
[*]2 GB of RAM
[*]250 MB of available hard disk space required
[*]1024 x 768 resolution with 16-bit color
[*]Internet connection required for online help and program updates
[*]Dependencies: Glib 2.4, KDE or GNOME recommended (full list of dependencies in RPM & DEB packages)
[*]Enable desktop compositing and freedesktop.org-compliant window manager (KDE, Gnome, and others) recommended
[*]64-bit distributions require 32-bit compatibility libraries (ia32-libs)
[/LIST]

It seems to me that the company has been neglecting its Linux offering. Fedora is at version 35 and Ubuntu has had 14 more releases since then.

It is getting the 32 bit compatibility libraries that you should worry about. Will they be installed when you install Aftershock Pro 3 or do you have to install them yourself. There are not installed by default in Ubuntu 20.04.

Regards

---

### Post by dragonfly41 on 2021-10-16
[I]Much depends on what you plan to do with your images.
[/I]
I am not a photographer but recently installed Wolfram free developer licence on Ubuntu 20.04.
I have not purchased a full Mathematica licence (the developer licence is free) but the image processing capabilities of Wolfram are fascinating. Example below:

[https://reference.wolfram.com/language/ref/Sharpen.html](https://reference.wolfram.com/language/ref/Sharpen.html)

I can walk through the installation of wolframscript (cli) and WolframEngine on Ubuntu 20.04 desktop
if this branch of image processing is of interest.

---

### Post by dragonfly41 on 2021-10-16
Other tools to explore ...

[https://boxy-svg.com/tutorials/j8v4SzypzWw/compositing](https://boxy-svg.com/tutorials/j8v4SzypzWw/compositing)

You can install Boxy SVG as a desktop app or use web site.

And ImageMagick and Gimp in Ubuntu desktop.

---

### Post by Frogs Hair on 2021-10-16
> So does this mean it won't work with 20.04 desktop? 20.04 uses Gnome so there shouldn't be a problem if there is a compatible Aftershot .deb package available.

---

