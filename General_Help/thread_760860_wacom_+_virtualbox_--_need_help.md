---
title: "wacom + virtualbox -- need help"
date: 2008-04-20
forum: General Help
---

### Post by bemused0 on 2008-04-20
This posting is a log of everything I'm attempting to get pressure sensitivity working in Virtualbox
(Or wine, if that happens somewhere along the way, but that's not the primary concern)
I DO have pressure sensitivity in Gimp, 
everything works fine in and out of virtualbox as far as the cursor movement, UNLESS I uncomment the line in fstab (group permission for usbfs )  then giving the device to vbox of course causes it to quit working in X.

-Running Hardy 2.6.24-16 
-compiled 0.7.9-11 LinuxWacom
-Trying with a Bamboo and Intuos3 (same on both)
-xorg.conf is properly configured
-virtualbox - non-free,  USB is enabled, but working incorrectly/incompletely
-drivers are installed on the virtualbox guest, however bringing up tablet preferences displays an error 'no supported tablets detected' etc.
-changed write permission on /proc/bus/usb/002 (usb for the wacom)
(pulled this from a tutorial, adding write permission had no effect on the situation in or out of virutalbox)

(my vboxusers gid is 125)
-edit to /etc/fstab
```

none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

```

-Edit to /etc/init.d/mountdevsubfs.sh
```

mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

```


-edit to /etc/udev/rules.d/40-permissions.rules 
```

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device", MODE="0666"

```

As mentioned here:
[http://ubuntuos.com/index.php?option=com_content&task=view&id=15&Itemid=1](http://ubuntuos.com/index.php?option=com_content&task=view&id=15&Itemid=1)

modified /etc/init.d/mountkernfs.sh

-Tried a startup script :
That also doesnt help the situation, (Useful in x11 of course, not so much in virtualbox)
```

xsetwacom set eraser ClickForce "5" &
xsetwacom set eraser PressCurve "0 0 100 100" &
xsetwacom set stylus TPCButton "off" &
xsetwacom set stylus mode "Absolute" &
xsetwacom set stylus Button3 "Button 3" &
xsetwacom set stylus Button2 "Button 2" &
#xsetwacom set stylus Button2 "core key ctrl" &
xsetwacom set stylus Button1 "Button 1" &
xsetwacom set cursor mode "Relative" &
xsetwacom set cursor Button5 "Button 5" &
xsetwacom set cursor Button4 "Button 4" &
xsetwacom set cursor Button3 "Button 3" &
xsetwacom set cursor Button2 "Button 2" &
xsetwacom set cursor Button1 "Button 1" &
xsetwacom set cursor Accel "1" &
xsetwacom set cursor SpeedLevel "6" &
xsetwacom set pad AbsWUp "4" &
xsetwacom set pad AbsWDn "5" &

```


Any ideas?  Thanks in advance!

Man this is a lonely thread, no replies but mine....

output of   'xsetpointer -l' 
```

0: "Virtual core keyboard"	[XKeyboard]
1: "Virtual core pointer"	[XPointer]
2: "Generic Keyboard"	[XExtensionKeyboard]
3: "<default pointer>"	[XExtensionPointer]
4: "pad"	[XExtensionKeyboard]
5: "eraser"	[XExtensionKeyboard]
6: "cursor"	[XExtensionKeyboard]
7: "stylus"	[XExtensionKeyboard]

```

output of 'xidump -l'
```

Virtual core keyboard          keyboard
Virtual core pointer           disabled
Generic Keyboard               unknown
<default pointer>              unknown
pad                            unknown
eraser                         unknown
cursor                         unknown
stylus                         unknown

```

---

### Post by bemused0 on 2008-04-20
bump + more info

After following the tutorial linked above (the new change was the addition to /etc/init.d/mountkernfs.sh and uncommented the permission line in /etc/fstab
I can enable a USB harddrive, doesn't actually show up in disk manager or explorer though (although the disconnect device icon shows up in the systray)

Any clues/help would be greatly appreciated at this point (still digging for more info on the forums)


-b

---

### Post by bemused0 on 2008-04-22
bump

---

### Post by bemused0 on 2008-04-23
bumpidy bump bump

Seriously, Anyone?   Someone who's gotten this working reply?
Is general help, somehow, not the place for this?


-thanks,
b

](*,)

---

### Post by bemused0 on 2008-04-27
Awesome, 100+ views and not a single reply.
Love it!


This works now on VMWare 6.03 with pressure sensitivity.
I was hoping to use virtualbox because of the integration, but this will do just fine.
v 6.03 + Patched to work on the Hardy kernel.
(?!?).
   

-bemused0

---

### Post by ERICwithanH on 2008-06-01
Hey, I'm having the same problem...  I'm searching for a solution.

Sorry, I'm no help, but I thought I'd reply anyways.

---

