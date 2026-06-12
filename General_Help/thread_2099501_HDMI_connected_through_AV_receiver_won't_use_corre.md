---
title: "HDMI connected through A/V receiver won't use correct resolution"
date: 2012-12-29
forum: General Help
---

### Post by chagrin5 on 2012-12-29
Hello all:  A long time listener, infrequent poster here

Short version:  HDMI goes from the ATI card to A/V receiver to TV and doesn't detect the right display or resolution on boot if the TV is off.  Also, can't add a xrandr --newmode because it **always** says "can't open display xxxx" for the working display.

Longer version:    I've scoured the forum for an answer to this problem and there are several but none seem to work for me.  Hopefully by asking directly someone might be able to figure out what makes this situation different.  When my media server turns on and the TV isn't on, it cannot pick 1920x1080 as a valid resolution.  Here is the behavior:

I have a box I just upgraded to 12.04 from 10.04 where the same behavior happened.  My Radeon 3450 is connected via HDMI through an A/V receiver (Onkyo) to the Television.  The computer is on a shutdown and wake schedule so it turns on in the morning without the TV on.  (This is important apparently)

When it turns on, if I ssh in and use xrandr, I can see that it is running from CRT1
As you can see from the first line, I have already added a virtual screen size into my xorg.conf so it reads the maximum as 1920x1920.  However, CRT1 is not the TV output, DFP2 is.  CRT1 doesn't have the right resolutions.

```
Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 1920 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0*+
   1400x1050      60.0
   1280x1024      60.0     47.0     43.0
   1440x900       59.9
   1280x960       60.0
   1280x800       60.0
   1152x864       60.0     47.0     43.0
   1280x768       59.9     56.0
   1280x720       60.0     50.0
   1024x768       60.0     43.5
   800x600        60.3     56.2     47.0
   720x480        60.0
   640x480        60.0
CRT2 disconnected (normal left inverted right x axis y axis)

```If I run ```
xrandr --newline <Modeline from cvt> 
```it will add that modeline to CRT2

```
Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 1920 x 1920
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1200      60.0*+
   1400x1050      60.0
   1280x1024      60.0     47.0     43.0
   1440x900       59.9
   1280x960       60.0
   1280x800       60.0
   1152x864       60.0     47.0     43.0
   1280x768       59.9     56.0
   1280x720       60.0     50.0
   1024x768       60.0     43.5
   800x600        60.3     56.2     47.0
   720x480        60.0
   640x480        60.0
CRT2 disconnected (normal left inverted right x axis y axis)
  1920x1080_60.00 (0xce)  173.0MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz
        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz

```Attempts to use the xrandr -d CRT1 or xrandr -d DFP2 is met with *Cannot open display DFP2*.  (DFP2 is the output that connects when the TV is turned on)

The only workaround so far is to turn on the TV, exit my media center (XBMC) run xrandr -s 1920x1080 with the TV on, then re-open XBMC.

Is there a way for me to do this without having to manually intervene every time?

Happy New Year!

---

### Post by wyliecoyoteuk on 2012-12-29
I have a similar problem.
The AV receiver is probably the cause.
I don't use a TV, but a monitor.
The video card depends on feedback from the monitor to wake up.
If I switch everything on, I still need to switch the monitor on/off, then select HDMI before the video card wakes up.
If I connect it direct instead of through the AVR, it works fine.

---

### Post by chagrin5 on 2013-01-05
I posted this right around the New Year so I'm giving it a bump.  Has anyone been able to solve this problem?

---

