---
title: "It's been awhile, can't boot into Xubuntu because no external display"
date: 2017-10-03
forum: General Help
---

### Post by alanmoore78 on 2017-10-03
When I installed Xubuntu on this laptop on my second hard drive (yes, laptop has two hard drives) I was using an external display I no longer have access to.  The laptop display and keyboard were each having issues so I ran it closed with a separate keyboard and mouse and display like a desktop.  I've since replaced my screen and keyboard and would like to log in and do updates and get back into running Xubuntu primarily unless I want to play GTA IV in Windows.  But unless I can find a display and VGA or HDMI cable and connect, I won't be able to log in.

The splash screen shows normally and then a cursor blinks and then it goes black.  Pressing the power button shuts the laptop down.  But I have no idea how to switch from the external display to the laptop's main display if I can't see anything.

Is there maybe a key combination I can use on the login screen that will change the display output, toggle it back to the internal display?

---

### Post by dragonfly41 on 2017-10-03
I'm using a secondary monitor after my primary laptop display failed.

Try hitting Windows icon key plus P key.   
I'm not sure if this will help you but I have to use this to toggle between my failed primary monitor and my secondary monitor.

---

### Post by efflandt on 2017-10-03
Laptops typically have a function key that switches additional displays or between displays using ACPI. In many laptops the ACPI function is primary and if you actually want to use numbered function keys (F1-F12), you need to press Fn or fn key like a shift key along with the function key. Although, the Win10 laptop I have automatically switches to its own display if HDMI is disconnected. It can dual boot Ubuntu 16.04, but I have not paid attention to whether it automatically switches to its own display in Linux because I don't normally use an external display for that.

---

### Post by gordintoronto on 2017-10-04
What brand and model of laptop? Do you have a manual for it?

As the above posters have suggested, there is usually a key or key sequence to control the display.

---

### Post by Yellow Pasque on 2017-10-04
If all else fails, boot a LiveUSB, mount your root partition (or /home partition if you have a separate one), and remove this file:
```
~/.config/xfce/xfconf/xfce-perchannel-xml/displays.xml
```
Then you should be able to boot your install as normal and a fresh displays.xml file will be generated.

---

