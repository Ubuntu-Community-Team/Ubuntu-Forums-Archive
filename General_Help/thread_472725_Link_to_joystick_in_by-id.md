---
title: "Link to joystick in by-id"
date: 2007-06-13
forum: General Help
---

### Post by elusivespoon on 2007-06-13
I have a USB joystick which works fine, which occasionally shows up as /dev/input/js0 , but sometimes as /dev/input/js1 (usually after my laptop has entered and left suspend mode). This is frustrating, as it means I have to reconfigure any application to use a different joystick location when it changes. I noticed that in the directory /dev/input/by-id there are symlinks created automatically that have a fixed name, and point to the current device location. For instance usb-. . .-event-mouse points to /dev/input/event5 and usb-. . .-mouse points to /dev/input/mouse3.

it would be nice if there were such a symlink for the joystick so I could just point applications to that symlink, and not worry whether js0 or js1 is used. Unfortunately there is only an event symlink for my joystick (pointing to /dev/input/event9) but no link to /dev/input/js0 or j1.

Is there any way I can have a symlink automatically created in /dev/input/by-id for my joystick, that points  to js0 or js1 depending on which is used?

Thanks,
Rob

p.s. I'm using KDE on Feisty, if it matters.

---

### Post by elusivespoon on 2007-06-15
After a bit of hunting I was able to answer my own question. *udev* is responsible for managing the device symlinks I mentioned. As it turns out, the rules that specify the creation of the symlinks for the mouse and joystick, match only when the kernel name is either "mouse" or "event", but not "js", hence my problem. The following is what I did to create a rule so that udev will create the desired symlink for the mouse.

1. Open up the rule file for editing.
```
> sudo vim /etc/udev/rules.d/65-persistent-input.rules
```
2. Copy the "mouse" rule under that line "#by-id links" comment, and edit as follows (change mouse to js)
```
KERNEL=="js*", ENV{ID_BUS}=="?*", ENV{ID_CLASS}=="?*", SYMLINK+="input/by-id/$env{ID_BUS}-$env{ID_SERIAL}-$env{ID_CLASS}"
```
3. Save and quit.
4. Unplug, and replug your USB joystick.

Note this only fixes things for a usb joystick. If you look at the rules file I edited you will notice quite a few devices were overlooked along with the joystick. If you have *udev* installed on Ubuntu, there should be a documentation file installed here:
```
/usr/share/doc/udev/writing_udev_rules/index.html
```

To help write your udev rules, you can find the keys associated with your device with the following command:
```
> udevinfo -a -p $(udevinfo -q path -n /dev/input/js0)
```
replacing */dev/input/js0* with the device's name.

---

