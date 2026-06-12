---
title: "Font Rendering Issues"
date: 2007-07-06
forum: General Help
---

### Post by Puzzettone on 2007-07-06
Hi, I'm a former Windows XP user recently converted to Ubuntu 7.04. I'm a typography geek so I expect fonts look beautiful and sharp on my display. Of course Ubuntu default setup is not good enough for me :)
Here is what I've done on my old ThinkPad T30:


sudo apt-get install msttcorefonts


sudo gedit /etc/apt/sources.list
    deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
    deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
gpg --keyserver pgp.mit.edu --recv-key D0AFFF5E937215FF
gpg -a --export D0AFFF5E937215FF | sudo apt-key add -
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install libfreetype6 libcairo2 libxft2
sudo dpkg-reconfigure fontconfig-config (Native; Always; No)
sudo dpkg-reconfigure fontconfig


sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo gedit /etc/X11/xorg.conf
    DisplaySize    270    203    # 1024x768 96dpi


System->Preferences->Font
Font: Bitstream Vera Sans 8...
Font Rendering: -
Resolution: 96 dpi
Smoothing: Subpixel (LCDs)
Hinting: Slight
Subpixel order: RGB


After this extra work fonts in my Ubuntu look great, especially in Firefox, which I use all day. But, coming from Windows, a little precisation is necessary. Windows/ClearType users should read this great article comparing font rendering on Mac with Windows:
[http://www.joelonsoftware.com/items/2007/06/12.html](http://www.joelonsoftware.com/items/2007/06/12.html)
In fact Ubuntu rendering (with the options I've choose) is very similar to the MAC one. In my experience Ubuntu attempt to emulate Windows rendering (set "Font Rendering: Subpixel Smoothing LCDs" in "System->Preferences->Font") make fonts look very ugly. In this case the best results are obtained with "sudo dpkg-reconfigure fontconfig-config (Autohinter; Always; No)". However I'm learning to love the MAC/Ubuntu rendering since fonts are more true to their original design...

Here are my only complains with Ubuntu:
bold letters (especially i, j, f, a) are very blurry;
fonts are too bold (also normal weight).

As an example enter Gmail (or the UbuntuForums) and see how bad is rendered bold text (i and l are very hard to tell).

Do you know a trick to graduate the boldness of fonts?

---

### Post by Puzzettone on 2007-07-06
Up!

---

