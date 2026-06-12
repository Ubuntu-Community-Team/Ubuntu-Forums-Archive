---
title: "Need help installing XGL on Ubuntu 6.10 Edgy 64 bit OS"
date: 2007-03-03
forum: General Help
---

### Post by blackstealth007 on 2007-03-03
I was able to install Ubuntu 6.10 to my hard drive, and am currently trying to install XGL but I have been running into some error problems that I cant figure as to why. One of them said "gpg: no valid OpenPGP data found." I have a Nvida GeForce 6800gs video card that I have been succesfull in installing the driver and also the control panel for it. But could someone please help me find a step by step tuturial for installing XGL???? I am fairly new to Ubuntu and linux in general, and am trying to get away from Microshaft.  This is one of the websites i tried using [http://www.biodesign.com.ar/blog/?p=25#more-25](http://www.biodesign.com.ar/blog/?p=25#more-25) and ended up getting error message after first 2 terminal entries.

---

### Post by K.Mandla on 2007-03-04
This is for Beryl, but it might give you some ideas.

[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

---

### Post by blackstealth007 on 2007-03-04
ok, ty, but in your opinion, is XGL better? or is Beryl

---

### Post by K.Mandla on 2007-03-05
I think it depends on what you want. Beryl is the rage right now, and comes with a lot more customization than Compiz. On the other hand, [some folks]("http://www.phocean.net/index.php/post/2007/03/01/Switched-back-from-Beryl-to-Compiz") think Compiz is more stable, and that makes it preferable. It depends on what you want out of life. :biggrin:

---

### Post by jocko on 2007-03-05
> **blackstealth007 said:**
> ok, ty, but in your opinion, is XGL better? or is Beryl

Xgl and beryl are completely different things.
Xgl is an opengl accelerated X-server, while beryl is a compositing window manager that work in opengl accelerated X-servers.
Xorg (in Edgy) contains AIGLX, a built-in extension that provides opengl acceleration, but whether or not you can use that depends on your graphics hardware and which drivers you use.
Intel cards work well with AIGLX, as does nvidia cards if you use a new enough version of nvidias proprietary drivers.
ATI cards work with aiglx only if you use the open source drivers.
So you may need to install Xgl to be able to run beryl, it all depends on your graphic card and which drivers you use.

If you need instructions for installing beryl, why not have a look at the [beryl wiki]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu")?
Just remember it's experimental software, and it may break your xorg setup.

---

