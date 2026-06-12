---
title: "[kubuntu]Xrandr gives “Failed to get size of gamma for output default”"
date: 2015-02-27
forum: General Help
---

### Post by joo7 on 2015-02-27
I recently installed Kubuntu 14.04 64-bits on a Desktop but the graphics were too slow (windows opening, minimizing, etc) and someone suggested my that the graphic card accelarator shouldn't be activated.

My graphic card is a MSI Global RX9250-TD128 ([http://www.msi.com/product/vga/RX9250TD128.html#hero-overview](http://www.msi.com/product/vga/RX9250TD128.html#hero-overview)) so I decided to try and install some new drivers for the ATI in order to manage Video Hardware Accelaration. Surprisingly the graphics are faster but now I have one problem, I have only one resolution possible.

When I run `xrandr` in the terminal the output is:

`xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1280 x 1024, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      77.0* 
`

I tried solving this "Failed to get size of gamma for output default" problem like this ([http://ubuntuforums.org/showthread.php?t=1594308&page=6](http://ubuntuforums.org/showthread.php?t=1594308&page=6)) but I couldn't manage to do it. Help please

Edit: Also, my /etc/X11/xorg.conf is empty (well, now it's actually deleted). Isn't that a problem?

---

