---
title: "At the boot"
date: 2007-04-09
forum: General Help
---

### Post by Kizilbas on 2007-04-09
When I start up my computer I get a message "Video Mode Not Supported"
So I press ALT+F4 quickly a number of times and then I'm able to bring up the login menu. (I don't know how I figured out bringing up the default login menu by using ALT+F4 lol, must be just my curiosity).

How would I prevent that silly message 'V M N S' from appearing?

---

### Post by taurus on 2007-04-09
Edit /etc/X11/xorg.conf and remove the unsupported video mode(s).

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Kizilbas on 2007-04-09
Thanks for your support taurus, that was very quick :)

Would that remove the unsupported video modes straight with that command?

ty

---

### Post by taurus on 2007-04-09
That command would let you edit /etc/X11/xorg.conf.  So, you need to use the arrows to move around and remove the unsupported resolution(s) from it.  Save it and restart X again with <Ctrl><Alt>Backspace or reboot.

---

### Post by Kizilbas on 2007-04-09
taurus it says: 
[B]
sudo: gedit: command not found[/B]

---

### Post by taurus on 2007-04-09
Are you running Gnome, KDE, or XFce4?

For KDE:
```
kdesu kate /etc/X11/xorg.conf
```

For XFce4:
```
gksudo mousepad /etc/X11/xorg.conf
```

---

### Post by Kizilbas on 2007-04-09
I'm running XFce4 & yes that command worked = For XFce4 but the strange thing is, when I start up my computer it says video mode not supported and when I do ALT+f4 and login to my account, then in the resolution settings I am able to change it to any of resolutions listed in the xorg.conf.

That's really strange.. :s

---

### Post by Kizilbas on 2007-04-09
The 'video mode not supported' message only comes up at the startup of my home pc
that should be the major confinement

---

### Post by dreadlord_chris on 2007-04-09
> **Kizilbas said:**
> The 'video mode not supported' message only comes up at the startup of my home pc
that should be the major confinement

There are 2 different points where your video resolution is set. The first point is when GRUB loads: this basically sets up your text mode display(s) - they are what you see when pressing <CONTROL><ALT>F1-F6, F7 being your Xserver screen. After you pass the GRUB menu is probably where you are seeing this ***Out of Range*** error. The setting for this is in **/boot/grub/menu.lst**. The second point that your video resolution is set, and possibly changed, is when your Display Manager (gdm/kdm/XFce4/etc) loads. The setting for this is in **/etc/X11/xorg.conf**. So, since you are getting this error before your Display Manager loads you need to edit your **/boot/grub/menu.lst** and add the video resolution you want to be default for booting.

```

Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?      770       ?        ?        ?         ?
 8 bits |   768     769     771      773      353      775       796 
15 bits |    ?      784     787      790      354      793       797 
16 bits |    ?      758     788      791      355      794       798 
24 bits |    ?      786     789      792       ?       795       799 
32 bits |    ?       ?       ?        ?       356       ?

```

That chart will tell you what to enter. i.e. 1024x768 24 bit = 792

So, open a terminal:
```

sudo nano /boot/grub/menu.lst

```

this will open menu.lst for editing. Scroll down until you see the line that starts:
```

# defoptions=

```
It may have something after the **=**, probably **splash**. What you want to do is add **vga=###** where **###** is taken from the chart above.

So, if the line started off like this:
```

# defoptions=splash

```
and you wanted to set 1024x768 24bit color, you would change it to:
```

# defoptions=vga=792 splash

```
Then type **<CONTROL>X**, then **Y** to save.

Then type:
```

sudo update-grub

```

And you should be good to go...

---

### Post by Kizilbas on 2007-04-12
ah that doesn't work either dreadlordchris :(

thanks though..

---

### Post by tgm4883 on 2007-04-13
dreadlord_chris:

Wouldn't you have to remove the # in front of defoptions=vga=792 splash?  Otherwise wouldn't it be commented out?

---

### Post by Kizilbas on 2007-04-13
aigh guys I solved this problem, thank you for joining in and trying to help me on it :)

See you all, good day

---

### Post by tgm4883 on 2007-04-13
For future people who search the forums with this problem, could you post how you fixed this problem and mark the thread as resolved

---

### Post by Kizilbas on 2007-04-13
> **dreadlord_chris said:**
> There are 2 different points where your video resolution is set. The first point is when GRUB loads: this basically sets up your text mode display(s) - they are what you see when pressing <CONTROL><ALT>F1-F6, F7 being your Xserver screen. After you pass the GRUB menu is probably where you are seeing this ***Out of Range*** error. The setting for this is in **/boot/grub/menu.lst**. The second point that your video resolution is set, and possibly changed, is when your Display Manager (gdm/kdm/XFce4/etc) loads. The setting for this is in **/etc/X11/xorg.conf**. So, since you are getting this error before your Display Manager loads you need to edit your **/boot/grub/menu.lst** and add the video resolution you want to be default for booting.

```

Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
 4 bits |    ?       ?      770       ?        ?        ?         ?
 8 bits |   768     769     771      773      353      775       796 
15 bits |    ?      784     787      790      354      793       797 
16 bits |    ?      758     788      791      355      794       798 
24 bits |    ?      786     789      792       ?       795       799 
32 bits |    ?       ?       ?        ?       356       ?

```

That chart will tell you what to enter. i.e. 1024x768 24 bit = 792

So, open a terminal:
```

sudo nano /boot/grub/menu.lst

```

this will open menu.lst for editing. Scroll down until you see the line that starts:
```

# defoptions=

```
It may have something after the **=**, probably **splash**. What you want to do is add **vga=###** where **###** is taken from the chart above.

So, if the line started off like this:
```

# defoptions=splash

```
and you wanted to set 1024x768 24bit color, you would change it to:
```

# defoptions=vga=792 splash

```
Then type **<CONTROL>X**, then **Y** to save.

Then type:
```

sudo update-grub

```

And you should be good to go...



Here's how I did it, good luck :)

---

### Post by tgm4883 on 2007-04-13
You followed that exactly?  I ask because you posted this.

> **Kizilbas said:**
> ah that doesn't work either dreadlordchris :(

thanks though..

---

### Post by Kizilbas on 2007-04-13
Well my computer is dodgy so I managed to do it after numerous trys, that's what I ment tgm4883 anyway

bye

---

### Post by linckraker on 2007-04-13
when i lspci i get something like 00:0a:0 VGA Compatible controller: nVidia Corp... blah blah blah.   what i was hoping to get some info on is what would that **00:0a:0** convert to in the xorg.conf file?

---

### Post by tgm4883 on 2007-04-13
> **linckraker said:**
> when i lspci i get something like 00:0a:0 VGA Compatible controller: nVidia Corp... blah blah blah.   what i was hoping to get some info on is what would that **00:0a:0** convert to in the xorg.conf file?

First start another thread, then post the complete output of lspci

---

