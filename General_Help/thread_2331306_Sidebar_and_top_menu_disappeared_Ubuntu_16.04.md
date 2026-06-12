---
title: "Sidebar and top menu disappeared Ubuntu 16.04"
date: 2016-07-20
forum: General Help
---

### Post by FZR_Rider on 2016-07-20
I booted Ubuntu this morning and saw that the sidebar and top menu are missing.  I did some research and found haven't found a fix for Ubuntu 16.04. 

I've tried the following:
sudo service lightdm restart

and 
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity


Does anyone here have any suggestions on what to do next?  Thank you!

---

### Post by grahammechanical on 2016-07-20
If we right click the desktop background wallpaper we get an option to Change Desktop Wallpaper. That option will open System Settings at the Appearance utility but from there we can get to the main System Settings window and then Software & Updates>Additional Drivers tab. And try with another video driver.

Other useful commands. To reset Compiz

```
dconf reset -f /org/compiz/
```

to restart Unity

```
setsid unity
```

regards

---

### Post by FZR_Rider on 2016-07-20
I tried changing the drivers and I still couldn't get it to work.  I did notice that the top bar on the open windows isn't displaying.  There is no way to minimize or reduce an open window. 

I tried running [COLOR=#000000][FONT=&quot]dconf reset -f /org/compiz/ and I got the error message Cannot autolaunch D-Bus without X11 $DISPLAY.

Also, when I run setsid unity it just hangs, nothing happens.  

What else could this be?  Thank you for the suggestions :)

[/FONT][/COLOR]

---

### Post by jinglada on 2016-09-19
A member of [https://lists.ubuntu.com/archives/ubuntu-cat](https://lists.ubuntu.com/archives/ubuntu-cat) told me to rename the hidden home subdirectory .cache to xx.cache and then reboot. 

It worked to me but I have lost the history of Unity sidebar and browsers except firefox.

If it doesn't work then try with following other subdirectories:  .config, .gnome, .gnome2, .gnome_private2, .gconf, .gvfs, .local

Other member from the same ubuntu list proposes rename .compiz in the same way.

Finally, re-rename the subdirectories except that which caused the problem.

---

