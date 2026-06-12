---
title: "Setting new display setting"
date: 2015-06-11
forum: General Help
---

### Post by adrian61 on 2015-06-11
I'm currently working on a Raspberry Pi 2 with Ubuntu 14.10. When I'm using it on a regular full hd 24" with HDMI cable computer screen it works fine in 1920x1080, but when i take my rPi2 and plug it in 42" HD LED TV it sets it self to 1024x768 and i can't seem to change it in display setting or with some commands, might just be me who are using the wrong codes :/

Is there any one who can help me with this little obstacle?

*EDIT*

Still haven't figured out how to fix it, but I manage to pull out some info from xrandr if it helps with you quest :)

```

[FONT=Verdana]root@raspberry:/home/linaro# xrandr
[/FONT][FONT=Verdana]xrandr: Failed to get size of gamma for output default[/FONT]
[FONT=Verdana]Screen 0: minimum 1280 x 720, current 1280 x 720, maximum 1280 x 720[/FONT]
[FONT=Verdana]default connected 1280x720+0+0 0mm x 0mm[/FONT]
[FONT=Verdana]   1280x720        0.0*[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]root@raspberry:/home/linaro# cvt 1920 1080 60[/FONT]
[FONT=Verdana]# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz[/FONT]
[FONT=Verdana]Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]root@raspberry:/home/linaro# sudo xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync[/FONT]
[FONT=Verdana]xrandr: Failed to get size of gamma for output default[/FONT]
[FONT=Verdana]X Error of failed request:  BadName (named color or font does not exist)[/FONT]
[FONT=Verdana]  Major opcode of failed request:  140 (RANDR)[/FONT]
[FONT=Verdana]  Minor opcode of failed request:  16 (RRCreateMode)[/FONT]
[FONT=Verdana]  Serial number of failed request:  19[/FONT]
[FONT=Verdana]  Current serial number in output stream:  19[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]root@raspberry:/home/linaro# xrandr[/FONT]
[FONT=Verdana]xrandr: Failed to get size of gamma for output default[/FONT]
[FONT=Verdana]Screen 0: minimum 1280 x 720, current 1280 x 720, maximum 1280 x 720[/FONT]
[FONT=Verdana]default connected 1280x720+0+0 0mm x 0mm[/FONT]
[FONT=Verdana]   1280x720        0.0* [/FONT]
[FONT=Verdana]  1920x1080 (0x13b)  173.0MHz[/FONT]
[FONT=Verdana]        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz[/FONT]
[FONT=Verdana]        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz[/FONT]
[FONT=Verdana]  1920x1080_60.00 (0x13c)  173.0MHz[/FONT]
[FONT=Verdana]        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz[/FONT]
[FONT=Verdana]        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz
[/FONT]
``` 

But now I'm stuck, I can chose 1920x1080 from "Monitor Settings", but they wont save/lode. But I definitely feel like I've made some progress :D

---

### Post by adrian61 on 2015-06-11
*UPDATE*

this is where I'm at now, and I have no idea where to go from here
```

root@raspberry:/home/linaro# xrandr --addmode default 1920x1080xrandr: Failed to get size of gamma for output default

root@raspberry:/home/linaro# xrandr --output default --mode 1920x1080
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed

```

hope these codes helps with something :)

---

### Post by Bucky Ball on 2015-06-11
I might have mentioned this in one of your other threads.

Have you tried switching everything off, plugging the RPi in to the 42" via HDMI, switch on 42" until 'no signal' then switch on the Pi?

If you yank the HDMI from one monitor and plug it into another of a different size without switching off the Pi I can imagine it might be problematic.

---

### Post by adrian61 on 2015-06-11
"Have you tried turnig it off and on again" - Roy Trenneman, IT Crowd. No to be honest I haven't actually tried that, that Will be the first thing i'll try when I'm back to work.  

Thanks for replaying, really appreciate it, Bucky Ball :)

---

### Post by Frogs Hair on 2015-06-11
In the Pi configuration with Rasbpian OS I toggle the overscan setting or the resolution is locked and there is black boarder. I don't know the Ubuntu equivalent to that setting to that setting though.

---

### Post by Bucky Ball on 2015-06-12
> **adrian61 said:**
> "Have you tried turnig it off and on again" - Roy Trenneman, IT Crowd. No to be honest I haven't actually tried that, that Will be the first thing i'll try when I'm back to work.  

Thanks for replaying, really appreciate it, Bucky Ball :)

Ha. Love that show. Anyhow, that's what worked with my RPi. I could never get it working if I switched it on first and then the TV monitor. So, have you tried turning it off and on again, but with it plugged into a monitor that is on? :)

---

### Post by adrian61 on 2015-06-17
> **Bucky Ball said:**
> Ha. Love that show. Anyhow, that's what worked with my RPi. I could never get it working if I switched it on first and then the TV monitor. So, have you tried turning it off and on again, but with it plugged into a monitor that is on? :)


I just got back to work, tried what you said. But it still sets it self back to 720p 60 Hz. and this starts to really annoy me! Because it it runs 1080p on my computer screen, and when i plug it in to my TV monitor it just sets it self back to 720p. 

Is it possible that the RPi cant run 1080 on a 42" screen? 

how can i force comand the RPi running Ubuntu 14.10 to run from 720p to 1080p

---

### Post by Bucky Ball on 2015-06-17
Well, 14.10 is no longer supported by Canonical and you won't get a lot of help here as the repos are closed. Didn't realise you were using that. Try 14.04 LTS. 

You can also try install xrandr and tweaking with that (it has a GUI) but doubt you'll be able to install as the repos would be no longer available. Grab a current image for the Pi and reinstall.

* Update: Oops, you've already tried xrandr. :)

---

### Post by adrian61 on 2015-06-17
Right on! I'll get right to it! :D 

Thanks, Bucky Ball!  :D :D

---

### Post by howefield on 2015-06-17
> **Bucky Ball said:**
> Well, 14.10 is no longer supported by Canonical and you won't get a lot of help here as the repos are closed. Didn't realise you were using that. Try 14.04 LTS. 

Almost, but not for a month yet.

---

### Post by Bucky Ball on 2015-06-17
My mistake. As howefield mentions ... trying to do three things at once again. :)

---

