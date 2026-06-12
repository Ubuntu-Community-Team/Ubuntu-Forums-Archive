---
title: "xorg.conf - mouse problem"
date: 2007-09-10
forum: General Help
---

### Post by Batuhan on 2007-09-10
Hello,

I have an USB mouse which is working fine. And I'm attaching a graphics tablet now but I do NOT want to use it as a mouse. I use it as a HID device for inputting data to another application.

Here is the problem:
In&#305;tially, in my xorg.conf file, in inputdevice section there is this line:

```
Option		"Device"		"/dev/input/mice"
```

"/dev/input/mice" merges all the mouses to a single mouse in the system. I want to use my usb mouse ONLY and not the graphics tablet(as a pointing device).

so I go to console and write:

```
sudo cat /dev/input/mouse1
```
and move my mouse to see which device is actually my usb mouse. It is mouse2 right now. And lets say my tablet is in /dev/input/mouse3(I want to disable this one). To disable the tablet as a pointing device, I edit xorg.conf as this:

```
Option		"Device"		"/dev/input/mouse2"
```

save it, press ctrl+alt+del to restart X then all is fine. My usb mouse works as expected nd the graphiics tablet is disabled as a pointing device, but I can still read it's data with external tools without it controlling the cursor.

But there is a problem: If I reboot the computer, the /dev/input/ location of my usb mouse changes. So none of the devices work as a pointing device. I have to go to terminal(by keyboard) and find the new location of my mouse(by using cat), and edit xorg.conf again. And next time I reboot, it changes again.

What should I do to fix this? Everytime I reboot, I have all my pointing devices are disabled so I need to edit xorg.conf to make it work.

I hope my question is clear.

Thanks

---

### Post by fragos on 2007-09-10
I have a laser mouse, Wacom and a touchpad.  They play nicely together and I can move between the devices at will.  Having my tablet share mouse duties has no impact on tablet function.  You're solving a perceived but not real problem.   Unless of course you want to make sure you don't have a weak moment and acidentialy use the tablet like a mouse.

---

### Post by Batuhan on 2007-09-10
I'm using the tablet for making live music, I'm using it as a control source. I get its x-y and pressure data and use that data to control something.

If it acts like a mouse, it clicks and drags around the screen by its function but I don't want it to have that functionality. (there will be parts of screen that it should not click if you want the show to go on : )

So basically I am asking: Is there a way to make sure that my USB mouse always stays at /dev/input/mouse1 ?

Then I can tell X to use that as a mouse only(instead of /dev/input/mice which simply means "use all the available mouses"). But if it keeps changing places, I have o reconfigure in every reboot...

---

### Post by fragos on 2007-09-10
Your answer may be with the used of /etc/udev rules to control device assignment.

---

