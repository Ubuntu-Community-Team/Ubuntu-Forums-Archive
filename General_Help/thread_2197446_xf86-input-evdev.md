---
title: "xf86-input-evdev"
date: 2014-01-03
forum: General Help
---

### Post by musicboy on 2014-01-03
This is the only last way I am trying to remap a Microsoft 7000 ergonomic multi media keyboard extra keys as xev does not read anything above 255 every other way does not work what so ever in UBUNTU any more at all!!

xf86-input-evdev - [http://www.thenautilus.net/cgit/xf86-input-evdev/](http://www.thenautilus.net/cgit/xf86-input-evdev/)

[http://www.thenautilus.net/SW/xf86-input-evdev/](http://www.thenautilus.net/SW/xf86-input-evdev/)

[http://www.thenautilus.net/SW/my-layout/](http://www.thenautilus.net/SW/my-layout/)

[http://www.mythtv.org/wiki/Remapping_remote_control_key_codes_greater_than_255_#Key_mapping_using_event_key_remap](http://www.mythtv.org/wiki/Remapping_remote_control_key_codes_greater_than_255_#Key_mapping_using_event_key_remap)

Adding the code line:


ModulePath "/usr/local/lib/xorg/modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"


To: etc/x11/xorg.config

Section "Files"
        ModulePath "/usr/local/lib/xorg/modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
EndSection


Now restart X (eg reboot the machine or restart gdm etc) and check that the new module is being used:


grep evdev_drv /var/log/Xorg.0.log


The output should be something like:


(II) Loading /usr/local/lib/xorg/modules/input/evdev_drv.so

When I restart x with real console loging in first: sudo service lightdm restart[COLOR=#000088][FONT=Consolas]
[/FONT][/COLOR] 
Does not allow me to log back into UBUNTU or GNOME desktops at all, creates a log in loop where its going to a blank screen then looping back around to the login screen again over and over no matter how many times I try.

When I restart x with real console loging in first: sudo lightdm restart *none of the real consoles work and then run grep evdev_drv /var/log/Xorg.0.log : this returns the standard path and then loging out or rebooting creates the login loop


ONLY works with "UBUNTU Studio" desktop log in, not UBUNTU or GNOME using UBUNTU STUDIO 13.10 as the install core and then with GNOME and UNITY desktops added on top.


If when In UBUNTU studio desktop I run:


grep evdev_drv /var/log/Xorg.0.log


this confirmed returns:


(II) Loading /usr/local/lib/xorg/modules/input/evdev_drv.so


When I take the code line out again and log out of UBUNTU studio I can then log back into UBUNTU using UNITY desk top or GNOME if I wish etc etc.


Can anyone tell me why that is and can anyone help me to configure this right to work with UBUNTU Unity desk top and GNOME as I am taking it that that the cause of this problem is effecting UNITY and GNOME.


Thanks.

Hope someone can help!!

---

