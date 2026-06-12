---
title: "Mouse and CPU load"
date: 2007-06-08
forum: General Help
---

### Post by spynode on 2007-06-08
I have this weir problem on my Feisty. Every time CPU load becomes little higher my mouse starts to turn off an then back on. Sometimes it doesn't even turn back on until I reboot. I am not sure if this is directly related to CPU load but most often this happens exacly when I am doing some CPU eating tasks. I have VT8237 chipset KT600-A motherboard with Athlon XP 2500+. My mouse is Logitech MX518. As I said I am using Ubuntu Feisty Fawn. In edgy I did not have this problem. I don't think it appeared right after upgrade to Feist either. It appeared a bit later (after some update I guess). I have 2.6.21.3 vanilla kernel. I don't think this problem is related to mouse becouse it turns back on on reboot. Please help me figure out what is wrong here. This problem really keeps me from being productive.

---

### Post by ikonia on 2007-06-08
1.) why are you using a non ubuntu built kernel ?
2.) how long is the system under %100 load
3.) how does the rest of your X session respond
4.) have you tried restarting X
5.) are there any errors or warning in the syslog or xorg log ?

---

### Post by spynode on 2007-06-08
1) I just like compiling kernels I guess. + NVIDIA drivers wont work with the Ubuntu one. I have never ben experiencing any problems with vanilla kernels and I am pretty confident that I configure them right.
2) well I didn't say it was under 100% load. And it doesn't always happen under high CPU loads. It just happens more often when I actually do something that needs more CPU.
3) X isn't affected at all. Keyboard works every thing works. I forgot to tell you thaht mouse turns off completely. I mean - red light off optical mouse goes off. 
4) I can't restart X cuz it says that core pointer can't not be found. (that's becouse mouse is turned off)
5) xorg.log says nothing. My syslog is full with something like this that I think is directly related to my problem 
```
Jun  8 14:52:26 spy-desktop NetworkManager: <debug info>^I[1181303546.290804] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c01e_noserial'). 
Jun  8 14:52:26 spy-desktop NetworkManager: <debug info>^I[1181303546.319596] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c01e_noserial_if0'). 
Jun  8 14:52:26 spy-desktop NetworkManager: <debug info>^I[1181303546.424010] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c01e_noserial_if0_logicaldev_input'). 
Jun  8 14:52:26 spy-desktop lomoco: 002.014: 046d:c01e MX518 Optical Mouse (M-BS81A) Caps: RES
Jun  8 14:52:26 spy-desktop NetworkManager: <debug info>^I[1181303546.573968] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c01e_noserial_usbraw'). 
Jun  8 14:53:02 spy-desktop NetworkManager: <debug info>^I[1181303582.505826] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c01e_noserial_if0_logicaldev_input'). 
Jun  8 14:53:02 spy-desktop NetworkManager: <debug info>^I[1181303582.517053] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c01e_noserial_if0'). 
Jun  8 14:53:02 spy-desktop NetworkManager: <debug info>^I[1181303582.523337] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c01e_noserial_usbraw'). 
Jun  8 14:53:02 spy-desktop NetworkManager: <debug info>^I[1181303582.527817] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c01e_noserial'). 
```

btw thanks for your fast response. I hope we can sort out this problem.

Edit: Also here is mouse section from xorg.conf : 

```
Section 	"InputDevice" 
	Identifier 	"MX518_2"
	Driver 	"evdev" 
	Option 	"Device" 				"/dev/input/event9"
        Option "Emulate3Buttons"	"false"
EndSection
```

---

### Post by spynode on 2007-06-08
Bump

---

### Post by ikonia on 2007-06-09
well, 

lets look at this objectivly.

1.) you've built your own kernel, and your a bit more on the bleeding edge, plus everything may not intergrate as well.

as a side issue building your own kernel because "you like to" seems a bit pointless due to the ammount of effect ubuntu put in to making sure things are compatible. The Nvidia drivers ubuntu package up with the kernels they provide are compatible, thats the benifit of using the ubuntu packaged/supported software. Did you have a reason to pugrade the nvidia drivers outside of the ubuntu ones or did you just want to ?

Now lets look at the actual problems.

First things first - lets go back to using an ubuntu built kernel to remove the basics. Boot with an ubuntu installed kernel - stable and supported and run X for a period of time and lets see what happens. 

the reason I am suggesthing this is two fold. 1.) the ubuntu kernel is a known quantity and you're having a problem that is device related, so lets drop back to a known quantity. 2.) The errors reported in your syslog suggest that hal is dropping your device, this could be due to any reason but as hal/udev get device info and events from the kernel this seems a likley place to start.

---

### Post by spynode on 2007-06-09
well the thing is that I have MX440 video card and it is supported by a bit older NVIDIA binary drivers. That's why I always compile my own kernel and install driver for it. I probably will try older kernel or Ubuntus kernel then. Thanks for advice.

---

### Post by ikonia on 2007-06-09
for this moment in time - you could even forget X or use the vesa driver (don't forget there is the nvidia-legacy package in nvidia for older cards too).

Don't roll your own - use the ubuntu stock kernel and let your machine run for a while. See if hal starts complaining with the stock kernel, as again, building your own kernel still removes away from the ubunu packages/compatability efforts. An older kernel may be just as much of a problem. Lets find out where the problem is before trying to fix it.

---

### Post by spynode on 2007-06-09
So I installled 2.6.20-16-generic Ubuntu stock kernel. After some time my mouse unfortunatly turned off completely again. When I reboot my computer it turns back ON in moment my computer bios lists all IDE devices.  
syslog :
```
Jun  9 16:41:14 spy-desktop NetworkManager: <debug info>^I[1181396474.980220] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c01e_noserial_if0_logicaldev_input'). 
Jun  9 16:41:15 spy-desktop NetworkManager: <debug info>^I[1181396474.980568] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c01e_noserial_if0'). 
Jun  9 16:41:15 spy-desktop NetworkManager: <debug info>^I[1181396474.987801] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c01e_noserial'). 
Jun  9 16:41:15 spy-desktop NetworkManager: <debug info>^I[1181396474.993232] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c01e_noserial_usbraw'). 
Jun  9 16:41:15 spy-desktop NetworkManager: <debug info>^I[1181396475.400456] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c01e_noserial'). 
Jun  9 16:41:15 spy-desktop NetworkManager: <debug info>^I[1181396475.466517] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c01e_noserial_if0'). 
Jun  9 16:41:15 spy-desktop NetworkManager: <debug info>^I[1181396475.597932] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c01e_noserial_if0_logicaldev_input'). 
Jun  9 16:41:15 spy-desktop lomoco: 002.003: 046d:c01e MX518 Optical Mouse (M-BS81A) Caps: RES
Jun  9 16:41:15 spy-desktop NetworkManager: <debug info>^I[1181396475.725011] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c01e_noserial_usbraw'). 
```
And it keeps happening all the time. Mouse just keeps turning on and off. And sometimes it doesn't even turn back on so I have to reboot. This can't be a mouse problem becouse reboot would not turn it back on. What could this be ?

Also right after mouse turned off I got these messages in my console :
```
USB 2-2: device descriptor read/64 error -110
USB 2-2: device not accepting address 16 - error -110
USB 2-2: device not accepting address 17 - error -110

```

My xorg.conf also came up with this : ```
(EE) Read error: No such device (19, -1 != 16)
(II) MX518_2-usb-0000:00:10.1-2/input0: Off
(II) evdev brain: Rescanning devices (3).
(II) evdev brain: Rescanning devices (4).
(II) MX518_2-usb-0000:00:10.1-2/input0: On
```

goddamnit it keeps happening all the time... mostly on cpu load as I said. please help me.

EDIT: Ok so I tried my other mouse Microsoft Habu and it works fine. I also tried my MX518 mouse on my brother's XP system and it works perfectly there. So there is something between my system and MX518 that keeps turning it off. I am confused guys. What is happening ? It worked fine before and I am on Ubuntu back from Edgy and it only started to behave this way couple of weeks ago.

EDIT: BIG FREAKING BUMP

---

