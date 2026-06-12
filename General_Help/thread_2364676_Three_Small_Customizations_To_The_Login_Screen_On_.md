---
title: "Three Small Customizations To The Login Screen On Ubuntu 16.04.2"
date: 2017-06-26
forum: General Help
---

### Post by SBTlauien on 2017-06-26
I'd did a search but couldn't find anything for customizing these exact things.  I have two programs installed that allow certain modifications but I don't believe either can do this.  The two programs are Compiz and Unity Tweak Tool.  

0. Remove my PC's name that is displayed at the top left corner
1. Remove all of the options in the top right corner except for being able to turn the PC off
2. Center the password box

Thanks in advance.

---

### Post by deadflowr on 2017-06-26
0 and 1 can be dealt with
2 is hard coded and would require changes to the greeter source code.

But to do 0 and 1 would require creating what is called an override file.
The greeter has dconf settings, which you can see with dconf-editor in the location com.canonical.unity-greeter.
But while you can try changing the settings here the changes normally cannot be changed as dconf runs as your user and the greeter runs before any user loads.

However to change this you can just make what in known as an override
open a terminal and run
```
sudo nano /usr/share/glib-2.0/schemas/10_unity_greeter.gschema.override
```
add these entries
```
[com.canonical.unity-greeter]
indicators=['com.canonical.indicator.session']
show-hostname=false
```
then save the file
and run
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```
If done right you should no longer see either the machine name in the panel or anything but the shutdown icon.
(this should not affect the ability to login if it goes belly up, at least)
If it does go sour, try removing the override file you created and re-run the glib-compile-schemas command again to revert it.

Hope it helps

Edit:
It should be show-hostname, I wrote just hostname, whcih will error.
fixed that.

---

### Post by CatKiller on 2017-06-26
lightdm-gtk-greeter-settings will do what you want easily.

---

### Post by SBTlauien on 2017-06-27
> **deadflowr said:**
> /usr/share/glib-2.0/schemas/10_unity_greeter.gschema.override.

  I don't seem to have this file.  These are the files from that location that start with a digit... 

10_compiz-gnome.gschema.override
10_gnome-settings-daemon-schemas.gschema.override
10_gnome-system-log.gschema.override
10_gsettings-desktop-schemas.gschema.override
10_ibus.gschema.override
10_libgtk-3-common.gschema.override
10_metacity-common.gschema.override
10_ubuntu-settings.gschema.override
10_unity-settings-daemon.gschema.override

---

### Post by deadflowr on 2017-06-27
That's because you make that file yourself.

Anyhoo,
lightdm-gtk-greeter works probably overall better.
And that method does not need to run a bunch of foo commands.
You just need to make a simple configuration file.

You would need to install lightdm-gtk-greeter
```
sudo apt install lightdm-gtk-greeter
```
You can read up on lightdm here:
[https://wiki.ubuntu.com/LightDM]("https://wiki.ubuntu.com/LightDM")
when you install lightdm-gtk-greeter it'll add a sample-like file in /etc/lightdm that lists available settings.
(Mine happens to be lightdm-gtk-greeter-conf-dpkg.new, fwiw)
One of the setting happens to be for indicators.
You can just set that the way you want in the config file you will create after following the linked guide on how to do that.

Also,
There a package called lightdm-gtk-greeter-settings that you can use to edit the configurations as well.
```
sudo apt install lightdm-gtk-greeter-settings
```
As you can see light-gtk-greeter is a tad more malleable than unity-greeter, which Ubuntu by default uses.
It can set what you want better than unity greeter can.
But you'll lose unity greeters slicker login box.
So there is that.

But at least you have options to look at.

---

### Post by SBTlauien on 2017-06-27
Awsome.  I went with the first suggestion since it was a bit simpler and didn't replace the slick Unity greeter login box.

Thanks, everyone.

---

