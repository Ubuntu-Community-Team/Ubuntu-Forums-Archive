---
title: "Black screen after login - Working with external monitor"
date: 2016-03-06
forum: General Help
---

### Post by hermes5 on 2016-03-06
Hello,

I've run into some sort of bug where my laptop screen display fails after login. Funnily enough, the system boots just fine when I have my HDMI monitor running through my thunderbolt adapter. This is a pretty big problem for me, as I need to use the laptop in at university. I tried doing some google-ing for similar problems but it is an awkward problem to search. I'm running kubuntu 15.10 with a 4.2 kernel.

Something I've noticed is sometimes after rebooting in using my external display, very briefly, the aspect ratio on the external display is that of my laptop screen before it fixes itself. I think there has been some sort of miscommunication between my laptop display and the external display and it has somehow 'hardwired' this into it's settings. I've tried removing the thunderbolt adapter and restarting, shutting down and then removing the adapter before boot but neither of these seem to work. 

I'm sorry, I'm not very technically literate and I'm still learning. I really need some help with this.

---

### Post by Bucky Ball on 2016-03-07
*Thread moved to **General Help**.*

Boot to the HDMI input, go to 'Display' settings, make sure your laptop monitor is there and on. If it is there but not 'Active', make it so. You should have both screens visible. 

There is also a box to tick in the configuration 'Configure displays automatically'. Is that ticked? If not and you have set up for the HDMI screen only, that is what you'll get in perpetuity, until you manually change it back.

---

### Post by hermes5 on 2016-03-07
I have these settings in the display configuration module. I can't seem to find the automatic settings but I will have a closer look.

edit - To clarify, I think the desktop is booting thinking it has a second display to the side of it, when infact it doesn't. This leads to a perpetual black screen on my laptop screen. I can access command line from tty1 just fine. I hate to sound desperate but I really am, I need this laptop to bring in to university.

edit 2 - For what its worth, I unplugged my thunderbolt adapter(thunderbolt to HMDI adapter) while the screens were in use, and working. After I unplugged it some of the applications were still on the other screen. I then tried to go into the display settings, and the screen blacked out, and in a similar fashion to boot up, the system seemed to labour under a task(presumably trying to fix itself). I'm really lost I don't know what to do =/

---

### Post by montag dp on 2016-03-07
Does this command work?

```
xrandr --output HDMI1 --off
```

You might need to change "HDMI1" to something else if that's not what it is actually called.  Use xrandr -q with both monitors plugged in to find out the actual name.

You might also try setting the laptop screen as primary, like this:

```
xrandr --output <name of laptop screen> --primary
```

I think this option should be in the GUI display configuration options.  Maybe it's under advanced?  There are also other things you can do with xrandr that might be helpful, like --pos, which should allow you to make the laptop display actually appear on the screen if it is offset.  See the man pages for xrandr.

All this stuff should really work from the GUI, but Plasma 5 is still pretty new and it seems like it has some issues with HDMI displays.

---

### Post by hermes5 on 2016-03-07
Thanks for the reply montag!

I queried xrandr -q and got the following output

> james@vulcan:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 8192 x 8192
LVDS-1 connected primary 1440x900+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1440x900      59.90*+
   1152x864      59.96  
   1024x768      59.92  
   800x600       59.86  
   640x480       59.38  
   720x400       59.55  
   640x400       59.95  
   640x350       59.77  
DP-1 connected (normal left inverted right x axis y axis)
   1920x1080     60.00 +  50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1400x1050     59.95  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.08    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
VGA1 disconnected
VIRTUAL1 disconnected

I  proceeded to turn off DP-1 which turned off the external monitor. It  looked to have work as the laptop screen spun up, but then it died a  black screen death =/. I have to go to university now, I'll have a look  at the man pages while I'm there. Hopefully I can get it working for  tomorrow.

edit - Rebooted and it is working. 2nd monitor is still off but I'll look at the man pages to get that setup properly. Thanks montag :)

---

### Post by montag dp on 2016-03-07
I'm glad it worked!  I had a similar issue awhile ago when I unplugged the HDMI display and it just messed everything up.  Since then I've had a few updates to Plasma that problem hasn't happened again.  But now I normally just use a script to toggle the HDMI display on/off.  It uses the following commands:

On:
```
xrandr --output HDMI1 --auto --right-of LVDS1
```

and off:
```
xrandr --output HDMI1 --off
```

I also have some commands in the script to automatically set the audio profile so that it plays through HDMI when it's plugged in.  It has been much more convenient to me than going through the system settings every time I connect/disconnect the display.

---

### Post by antvyanka on 2016-11-12
I think you should mark this as [SOLVED]
I've been having this problem for about a week now and just couldn't find a solution, and was bout ready to reformat. Turning off, in my case, VGA1 via xrandr resolved the problem successfully.

Thank you!

---

