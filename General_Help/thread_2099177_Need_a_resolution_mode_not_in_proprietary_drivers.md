---
title: "Need a resolution mode not in proprietary drivers"
date: 2012-12-28
forum: General Help
---

### Post by CrusaderAD on 2012-12-28
Here's my issue. I need a 1280x800 resolution for my TV. The Open source drivers have it, and it looks perfect. When I install the proprietary fglrx drivers, the option is removed. I sort of have to use the fglrx drivers because I don't get sound out of the hdmi without them. So I either need to get the resolution on the proprietary drivers or get sound working on the open source drivers. Anyone have any tips or ideas?

---

### Post by cwsnyder on 2012-12-28
I don't know if you can, you tell me.  

First, install the package **x11-xserver-utils** with your favorite package manager.

Next, run the terminal command **xrandr**

If the first line of output from **xrandr** is an error about being unable to read the gamma of your display, you may not be able to change your display with **xrandr**.  If the first line of output starts with **Screen** then a number then goes on with numbers about present resolution and maximum resolution, the next line(s) will start with display names which can be used with **xrandr** as described in [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) with the name you wish to use being the one described as 'connected'.

---

### Post by cwsnyder on 2012-12-29
I have found a fix to the "unable to read gamma" error!

On the line which would read:
xrandr --output default --mode <newmodename>
change the line to:
xrandr --output default --gamma 1:1:1 --mode <newmodename>

You will still not set the output, and there will be a gamma error, but your new mode will be available in your Settings >> Display area for selection.  Now select the new mode from Settings >> Display.  It will not change your effective display, but still select the 'Keep this setting' from the dialogue box.  Now log out.

My login screen immediately went to the new setting, and remained when I logged in.  Also, when I tried the xrandr command by itself in a terminal, it showed me several new modes, some of them which would not work on my LCD display, but there was no longer an error about not being able to read the gamma.

This worked in two separate VirtualBox sessions and one Live session that did not work before, including Ubuntu 13.04.

---

