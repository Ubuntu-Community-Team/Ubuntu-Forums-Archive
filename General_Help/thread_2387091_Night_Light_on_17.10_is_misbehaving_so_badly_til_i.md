---
title: "Night Light on 17.10 is misbehaving so badly til it's unuseable"
date: 2018-03-14
forum: General Help
---

### Post by BikeRich on 2018-03-14
Night Light on my newly-installed 17.10 is switching from manual to sunset-sunrise by itself. If I turn it off, it may turn itself back on again during the same session. When I try it on manual, it will soon change the times for on and for off.  

Its not there in Synaptic for me to un-install, so is there another way for me to un-install it ?

Have searched this forum using Night Light , NightLight , and  Night-Light,  found nothing.  Help would be appreciated ,  Thanks

---

### Post by #&amp;thj^% on 2018-03-14
> **BikeRich said:**
> Night Light on my newly-installed 17.10 is switching from manual to sunset-sunrise by itself. If I turn it off, it may turn itself back on again during the same session. When I try it on manual, it will soon change the times for on and for off.  

Its not there in Synaptic for me to un-install, so is there another way for me to un-install it ?

Have searched this forum using Night Light , NightLight , and  Night-Light,  found nothing.  Help would be appreciated ,  Thanks

It's part of the System Settings > Display > **so not wise to uninstall** if you don't want problems or side effects. (**In other words it is in gnome-control-center**)
If you have "**dconf-editor**" installed you may find adjusting a few settings more to your liking via:

Open dconf-editor (install it if you don&#8217;t have it)
Navigate to org/gnome/settings-daemon/plugins/color/night-light-temperature.
Enter a custom value:
Here are some temperatures values to use as a guide:

```
>>> *1000 &#8212; Lowest value (super warm/red)
>>> *4000 &#8212; Default night light on temperature
>>> *5500 &#8212; Balanced night light temperature
>>> *6500 &#8212; **Default night light off temperature**
>>> *10000 &#8212; Highest value (super cool/blue)

```
You can readily undo any changes you make at any time by sliding the &#8216;use default value&#8216; switch to on.
EDIT You can also enable and disable Night Light with:
```
gsettings set org.gnome.settings-daemon.plugins.color night-light-enabled false
```
Will Disable ^^^^^^^^^
```
gsettings set org.gnome.settings-daemon.plugins.color night-light-enabled true
```
Will Enable ^^^^^^^^^

---

### Post by BikeRich on 2018-03-14
1Fallen :

     Will try your suggestions tomorrow;  thank you for the info !

                             Bikerich

---

### Post by BikeRich on 2018-03-18
Yes, 1Fallen , that shuts it off o.k..    I'll try twilight or some such. thank you.   Why Night Light behaves so badly, who knows ?

---

