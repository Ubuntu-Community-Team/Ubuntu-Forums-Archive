---
title: "USB Audio - Only 1 Volume Setting"
date: 2007-12-27
forum: General Help
---

### Post by webplus on 2007-12-27
I have Ubuntu 7.10 installed and have USB Audio speakers connected.  If I set USB Audio in Sound Preferences for Sound Playback, I only get 1 volume setting - very loud. The volume bar increases and decreases on the screen when I use the + and - volume buttons on the speakers, but the volume is always at the loudest, even when the volume is set to off.

Sound volume settings and the volume slide bar in the top panel on the Desktop (next to the time) work absolutely fine for sound going through the monitor's built-in speakers, but through the USB speakers there's no volume control, except very loud.

Any ideas?  These are just a cheap basic pair or folding portable speakers, and no known brand so I can't get any drivers or help from the speaker manufacturers (the box they came in has this for 'Drivers' : 34mm Micro Driver).  Maybe I should buy different speakers? Although they work fine with XP and Vista.

Thanks for any help.

---

### Post by NilsE on 2007-12-27
This may not work but worth a try. Go into the volume control preferences (right click on icon and select preferences) and change what the volume control manages and see if that helps.

---

### Post by webplus on 2007-12-27
Thanks, I tried that but the volume control it stuck at maximum volume and won't move at all.

---

### Post by NilsE on 2007-12-27
Double click on the volume icon and let me know what shows up on the Playback tab.  You should see Master plus maybe one or two other sets of sliders.

Then go into Edit > Preferences and select all devices that show up there.  

Then with the volume control still open like in step one above try changing each of the sliders and see which one if any makes a difference.  If one of them works right click on the volume icon and select preferences there and highlight one or more of the options there to determine which the single click of the icon controls.

I hope that makes sense because all I am getting at is make sure all possible sliders are turned on, determine which if any makes a difference and select which one is controlled by the single click slider.

---

### Post by webplus on 2007-12-27
I tried this as well, and still get the same maximum volume setting that won't move. No worries, I've ordered some non USB speakers instead. Thanks for the help.

---

### Post by tgalati4 on 2007-12-27
It sounds like Linux is loading the wrong driver.  Some USB speakers use a *line-level* signal which is very loud.  It's used to drive amplifiers that have a built-in volume control.

Sounds like your speakers don't have a volume control, so you need to send a* headphone-level* signal that varies with the volume control.

In a terminal, post the output of:

>lsusb

In windows, did you have to load a driver to activate the speakers?

---

### Post by webplus on 2007-12-28
This is the result of lsusb: 

Bus 005 Device 007: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 005 Device 006: ID 04a9:1094 Canon, Inc. PIXMA iP3000x Printer
Bus 005 Device 005: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 19a8:2036  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

The speakers have volume + and - buttons which causes a volume control to appear on screen and the volume increase and decrease bar moves as the volume is changed but has no affect on the actual volume.

In Windows the drivers were automatically installed.

I have somehow managed to adjust the USB speaker sound to a lower setting, but it's still not adjusting via the normal volume control.  If I double-click the audio icon (next to the time in the top panel) Volume Control appears showing Playback - PCM sliders for left and right, but they are always stuck on maximum volume.  If I adjust, the slider always jumps back to the highest setting, but it does lower or turn off the USB sound.

Using this I have been able to get several volume settings, so will see how it goes.

Thanks for your help.

---

### Post by tgalati4 on 2007-12-29
You can change the channel that the panel volume slider controls in its preferences.  Try Right-Click Properies and change it to a channel that does control volume properly.  This will allow your dedicated volume buttons to work properly.

---

