---
title: "Screen strech on widescreen monitor"
date: 2007-02-16
forum: General Help
---

### Post by higgylm on 2007-02-16
Hi there,

I Apolagise in advance because its probably somthing little but...

Just installed Linux on my laptop,

it has a wide screen moitor and the sreen is streched to fit the wide screen,

I have tryed to adjust the sreen res in Linux but the only option in the drop down box is 1028 x 768.

I need something like 1280 x 800,

does anyone have any suggestions,

Thanks, higgylm

---

### Post by ghandi69_ on 2007-02-16
I'm not sure.... but when I install a window manager from the server edition.. xorg asks me to pick what resolutions I want to choose from... I'm not sure what command to type to start up that menu process again.. xorg config or something I'm not sure.... someone should be able to tell you.

---

### Post by FluffyElmo on 2007-02-16
Type *sudo dpkg-reconfigure xserver-xorg* from the terminal to reconfigure your XServer and choose available resolutions. 

Note that If you have an integrated Intel video chipset (i915?) you may want to search around the forums as I think you may have to apply a patch for it to handle wide-screen aspect ratios...

---

### Post by aidanr on 2007-02-16
/etc/X11/xorg.conf is the file you want to add the resolution to, but be sure to backup the file first and know how to restore the backup if something goes wrong, also i think you need a program called 915resolution if it's intel graphics

[http://ubuntuforums.org/showthread.php?t=269052](http://ubuntuforums.org/showthread.php?t=269052)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

edit:// or FluffyElmo's suggestion:wink:

---

