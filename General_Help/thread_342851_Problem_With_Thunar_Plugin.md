---
title: "Problem With Thunar Plugin"
date: 2007-01-20
forum: General Help
---

### Post by Wight_Rhino on 2007-01-20
Can anyone help? I'm trying to compile the Volume manager plugin for Thunar; [volman,]("http://www.gnomefiles.org/app.php/thunar-volman") but when I ./configure, I get > checking for exo-hal-0.3 >= 0.3.1.13... not found
*** The required package exo-hal-0.3 was not found on your system.
*** Please install exo-hal-0.3 (atleast version 0.3.1.13) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.


Now, just to make things clear, I have checked the PKG_CONFIG_PATH and adjusted it twice and got the same result. (Once for pkg-config and again for pkgconfig) I have the libexo libraries installed and Hal's dev package. it's still looking for this "exo-hal"

What am I doing wrong?

---

### Post by chebe on 2007-02-01
Same problem here ...
if I do a "aptitude install libexo-0.3-dev"
I get this as a reply ...

```
The following NEW packages will be installed:
  libatk1.0-dev libcairo2-dev libexo-0.3-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev libgtk2.0-dev libice-dev libpango1.0-dev libpng12-dev libsm-dev libstartup-notification0-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev libxext-dev libxfce4util-dev libxfcegui4-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-dev libxpm-dev libxrandr-dev libxrender-dev libxt-dev x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev 
```

It seems a wee bit too much ... I'm going to try this on another computer !!

---

### Post by chebe on 2007-02-01
Well ... installing all this didn't solve the dependancy problem :(

But  :  sudo aptitude install libthunar-vfs-1-dev
is the one you want !!

---

### Post by Wight_Rhino on 2007-02-01
Thanks for your reply, Chebe. I ended up emailing Benedict Muerer (sp?) an Xfce/Thunar dev, and he informed me (Almost immediately!) about the impending 4.4 release (which I installed successfully; an absolutely awesome piece of Work!) and a possible inclusion into Feisty.

Bottom Line, I'm running Xfce 4.4 from the installer, and everything "Just Works"!:D

---

