---
title: "Stupid problems with gnome-settings-daemon, themes, etc..."
date: 2007-04-25
forum: General Help
---

### Post by 3ntity on 2007-04-25
Hello,
```
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
```
When trying to run something like 'sudo gnome-mouse-properties' i get the above error, yet it'll display the properties. When i try to change something i get the following, and obviously it doesn't save the changed value::
```
(gnome-mouse-properties:6057): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(gnome-mouse-properties:6057): capplet-common-WARNING **: Unable to find a default value for key for /desktop/gnome/peripherals/mouse/motion_threshold.
I'll assume it is an integer, but that may break things.
Please be sure that the associated schema is installed

(gnome-mouse-properties:6057): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

```
I tried the suggestions on [this]("http://ubuntuforums.org/showthread.php?t=316647") page, namely moving ~/.gconf, .gconfd, .gnome and .gnome2, which didn't help.

I'm not sure if this is related to the above, since i had Beryl for like 2 days only: I had Beryl(+AIGLX) installed, and although it wasn't in my Sessions->Startup Programs beryl-manager still started every time i logged on. This got on my nerves, so i decided to remove beryl. Is there any way i can access a non-graphical, and hopefully complete, list of programs that are started upon loging in?

When i try changing theme i get the following:
```
The default theme schemas could not be found on your system.  This means that you probably don't have metacity installed, or that your gconf is configured incorrectly.
```
I tried reinstalling Metacity through Synaptic; this hasn't helped.

Oh yea, all icons have disappeared from my applications/places/system menus. I did do an update before which had something to do with gnome panels, maybe that's relevant?

Any ideas as to what might have gone wrong and how i can solve these problems?
Thanks a lot in advance :)

---

### Post by 3ntity on 2007-04-27
I reinstalled in the end.
If you have any ideas as to what might have gone wrong, please share :) 
Others may have this problem too, or it could just happen again...

---

### Post by jasonwert on 2007-06-27
I had this same problem a while back. I found this [link]("http://ubuntuforums.org/showpost.php?p=1164346&postcount=11") which showed how to fix it. 

> **Human Prototype said:**
> 
Solution:
1. ```
cd /usr/share/gconf/schemas
```2. ```
sudo gconf-schemas --register *.schemas
```That should register all the schemas again and for me it got the mouse working and the themes working and synaptic works ok. My menus seem fine but I don't know if they were broken as I fixed it pretty quick.

---

