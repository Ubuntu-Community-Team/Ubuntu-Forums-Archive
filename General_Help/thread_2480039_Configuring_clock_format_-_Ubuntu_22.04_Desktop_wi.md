---
title: "Configuring clock format - Ubuntu 22.04 Desktop with Gnome 42"
date: 2022-10-17
forum: General Help
---

### Post by martinu2 on 2022-10-17
I'd like to configure the format of the real-time clock which displays in the top centre of the top toolbar. I've done this in the past with a Gnome Shell Extension on Ubuntu 20.04, but it seems that the change in the version of Gnome is preventing the tool working with Ubuntu 22.04.

I've tried Extension Manger / Clock Override (clock-override@gnomeshell.kryogenix.org). This displays the Clock Override page but the cogwheel Settings button gives an error

TypeError: Gtk.EventBox is not a constructor

I wonder if this is because the utility doesn't work with the new Gnome.

Is there a tool which does work with this Gnome, which instructions on how to install it and any dependencies that it needs?

I want to change the default format "17 Oct 11:17:52" (probably the default for my en_GB locale) to "Mon 17 Oct 11:17:52" (ie add the day of the week). I'm familiar with the format of a time string using %H, %M etc because I've already tweaked my locale so the "date" command puts the year in the proper place ("Mon 17 Oct 2022 11:21:01 BST", instead of the UNIX default "Mon 17 Oct 11:21:01 BST 2022" with the year bizarrely after the timezone instead of after the month).

---

### Post by tea for one on 2022-10-17
Have you installed gnome-tweaks?

gnome-tweaks > Top Bar > Clock > Weekday

---

### Post by Dennis N on 2022-10-17
> Is there a tool which does work with this Gnome?
What you want is the "Date Menu Formatter" gnome-shell extension.

---

### Post by mIk3_08 on 2022-10-18
> **martinu2 said:**
> 
I want to change the default format "17 Oct 11:17:52" (probably the default for my en_GB locale) to "Mon 17 Oct 11:17:52" (ie add the day of the week). I'm familiar with the format of a time string using %H, %M etc because I've already tweaked my locale so the "date" command puts the year in the proper place ("Mon 17 Oct 2022 11:21:01 BST", instead of the UNIX default "Mon 17 Oct 11:21:01 BST 2022" with the year bizarrely after the timezone instead of after the month).
In my case I just use Time Format below. 
```
%x | %H:%M:%S
``` 
and the Output for this is just like: Monday, 17 October, 2022 | 11:17:52 Its just that, the year appears. Regards and cheers.

---

### Post by mIk3_08 on 2022-10-18
> **martinu2 said:**
> 
I want to change the default format "17 Oct 11:17:52" (probably the  default for my en_GB locale) to "Mon 17 Oct 11:17:52" (ie add the day of  the week). I'm familiar with the format of a time string using %H, %M  etc because I've already tweaked my locale so the "date" command puts  the year in the proper place ("Mon 17 Oct 2022 11:21:01 BST", instead of  the UNIX default "Mon 17 Oct 11:21:01 BST 2022" with the year bizarrely  after the timezone instead of after the month).
In my case I just use Time Format below. 
```
%x | %H:%M:%S
``` 
and the Output for this is just like: 
```
Monday, 17 October, 2022 | 11:17:52
```
 Its just that, the year appears. Regards and cheers.

---

