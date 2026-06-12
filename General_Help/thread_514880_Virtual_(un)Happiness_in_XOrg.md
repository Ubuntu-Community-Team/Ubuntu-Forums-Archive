---
title: "Virtual (un)Happiness in XOrg"
date: 2007-08-01
forum: General Help
---

### Post by Wraith Daquell on 2007-08-01
Hello. I have been researching this problem for awhile and decided to ask the Open Source Expert's Exchange.

I had a working Feisty installation on a physical machine. I needed to re-image the machine, so I ghosted the disk with partimage for a backup.

I need some data on the ghost image. I've converted the ghost image to a Virtual PC file, used a live cd to reinstall Grub, and it will boot fine.

However, after the Ubuntu init screen, the whole screen turns white with only the mouse in the middle. I think it attempts to show my taskbar, but that fails. If I restart X with CTRL-ALT-Backspace, the desktop wallpaper shows for a split-second.

I have tried:

[LIST]
[*]dpkg-reconfigure xserver-xorg
[*]Removing compiz and beryl
[*]I have set the bit depth to 16
[/LIST]

On a side note, the Live CD desktop shows up just fine, so I know it's not a driver issue (I think).

I'd really appreciate any help. Thank you!

---

### Post by roaldz on 2007-08-01
What video driver are you using? Changin it to "vesa" in xorg.conf can help.

---

### Post by Wraith Daquell on 2007-08-01
Thank you. I had tried the Vesa driver to no avail.

However, the problem appears to be fixed. Apparently, simply removing compiz is not enough to disable the effects.

So I opened xorg.conf in recovery mode:

```
sudo nano /etc/X11/xorg.conf
```
And changed the line:

```
Load “glx”
```
to

```
#Load “glx”
```
Worked like a charm! Thank you all.

---

