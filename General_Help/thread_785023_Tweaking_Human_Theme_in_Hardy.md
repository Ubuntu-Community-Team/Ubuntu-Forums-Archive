---
title: "Tweaking Human Theme in Hardy"
date: 2008-05-07
forum: General Help
---

### Post by undfined on 2008-05-07
All -

Thanks for the great forum.  I just got a new Dell 1420n and installed a fresh version on Hardy on it.  Life is good.  Wireless works, even after hibernation, graphics with the nVidia driver are sweet (I have yet to figure out compiz), and I'm loving the speed.

Got a few things I want to figure out though.

First is, while I'm happy with the Human theme, I want to customize it a little.  The title bar for starters.  A few icons after that.  I figure it's baked into the system as I've tried to tweak the gtkrc file with no luck.

Any ideas?

Thanks ahead.

---

### Post by hencke on 2008-05-07
> **undfined said:**
> All -

Thanks for the great forum.  I just got a new Dell 1420n and installed a fresh version on Hardy on it.  Life is good.  Wireless works, even after hibernation, graphics with the nVidia driver are sweet (I have yet to figure out compiz), and I'm loving the speed.

Got a few things I want to figure out though.

First is, while I'm happy with the Human theme, I want to customize it a little.  The title bar for starters.  A few icons after that.  I figure it's baked into the system as I've tried to tweak the gtkrc file with no luck.

Any ideas?

Thanks ahead.

Have you tried System>Preferences>Appearance? Click "Customize" in the "Theme" tab to change icon theme and window borders etc. or click "Install" to add more themes. You can look for new themes at

[http://www.gnome-look.org/](http://www.gnome-look.org/)

Some of the themes have installation instructions, but normally you just have to unpack them and then choose the right file after clicking "Install".

To change individual icons (select System>Preferences>Main Menu (or right click on the main menu) and then choose the application you want to edit) right-click on the applications icon and choose properties. Click on the icon that you want to change, you will be presented with a "Browse icons" window. If you can't see an icon that suites you click on "Browse..." and navigate to your downloaded icon. It might be a good idea to copy all your icons to the /usr/share/pixmaps/ folder, but you will need root privileges to do this. One option is to

```
gksudo nautilus
```

Please be careful with root-privileged-nautilus.

To enable compiz fusion, try the "Visual Effects" tab in System>Preferences>Appearance. If you want more options with compiz, you can try compizconfig-settings-manager from Synaptic or

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by undfined on 2008-05-07
> **hencke said:**
> Have you tried System>Preferences>Appearance? Click "Customize" in the "Theme" tab to change icon theme and window borders etc. or click "Install" to add more themes. 

Yea.  Doesn't look like the title bar colors can be changed in Hardy.

---

### Post by hencke on 2008-05-08
> **undfined said:**
> Yea.  Doesn't look like the title bar colors can be changed in Hardy.

I Just tried changing them myself and it seems as though it's no longer possible to change the title bar colors in the "Colors" tab (I'm quite sure I customized my settings from there in Gutsy). It's probably the gnome guys taking away "useless" option?

Anyway, I did some googling and found these:

[LIST]
[*][http://linuxtidbits.wordpress.com/2008/02/14/gnome-panel-font-color-part-deux/](http://linuxtidbits.wordpress.com/2008/02/14/gnome-panel-font-color-part-deux/)
[*][https://launchpad.net/gnome-color-chooser](https://launchpad.net/gnome-color-chooser)
[/LIST]

I searched synaptic for "gnome color" and indeed there is a package called "gnome-color-chooser". I presume this gives you the ability to change title bar colors, amongst others. Hope this helps.

---

### Post by undfined on 2008-05-12
I ended up editing the gtkrc file in /usr/share/themes/Human/gtk-2.0.  I changed the metacity_frame_color to a hex number that looked good to me and restarted.

The original is #CC863E, in case anyone needs it.

Cheers. :)

---

### Post by hencke on 2008-05-12
> **undfined said:**
> I ended up editing the gtkrc file in /usr/share/themes/Human/gtk-2.0.  I changed the metacity_frame_color to a hex number that looked good to me and restarted.

The original is #CC863E, in case anyone needs it.

Cheers. :)

I thought you might be looking for something "cleaner" than my solution, but I hope my responses will help someone else looking for a graphical user interface... =)

Good to know that you got your problem solved anyway. =)

---

### Post by undfined on 2008-05-13
> **hencke said:**
> I thought you might be looking for something "cleaner" than my solution, but I hope my responses will help someone else looking for a graphical user interface... =)

Good to know that you got your problem solved anyway. =)

Yep.  The text edit did the job.  I'm not so hot on the blue I have going, for obvious reasons, but it's doing the job for now.

Thanks for your help.  I got into the gnome color chooser but wanted a more out of the box solution.  While I can appreciate what the Ubuntu team was going for with the orange color, I wasn't feeling it when I had Gimp open and was working with various photos.  Now that I have a better understanding of how it works I'll make my own theme eventually.  Your links got me off to a good start in figuring it all out. :D

---

### Post by hencke on 2008-05-13
> **undfined said:**
> Yep.  The text edit did the job.  I'm not so hot on the blue I have going, for obvious reasons, but it's doing the job for now.

Thanks for your help.  I got into the gnome color chooser but wanted a more out of the box solution.  While I can appreciate what the Ubuntu team was going for with the orange color, I wasn't feeling it when I had Gimp open and was working with various photos.  Now that I have a better understanding of how it works I'll make my own theme eventually.  Your links got me off to a good start in figuring it all out. :D

Nice to hear that the links were helpful. Here's one more:

If you're interested in a blue theme for ubuntu, you might want to try blubuntu (search for blubuntu in synaptic).

[https://wiki.ubuntu.com/Artwork/Incoming/Blubuntu](https://wiki.ubuntu.com/Artwork/Incoming/Blubuntu)

---

