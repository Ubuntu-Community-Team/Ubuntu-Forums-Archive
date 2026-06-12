---
title: "How to mirror a display to a projector that has a different aspect ratio?"
date: 2021-03-29
forum: General Help
---

### Post by wrybread on 2021-03-29
I'm using xrandr to mirror my main display to a projector. My main display has a resolution of 1680x1050 (16:10 aspect ratio), the projector has a native resolution of 1024x768 (4:3 aspect ratio). Interestingly if I send a 1680x1050 signal to my projector it works fine, but the projector scales it to 4:3 aspect ratio, so it distorts the image (a circle becomes an oval). 

Is there some way to work around this, maybe with some letterboxing on the projector?

Here's my xrandr script:

```

# set resolution of main display
xrandr -s  1680x1050_60.00

# set the projector to 1680x1050
xrandr --addmode VGA-1 1680x1050_60.00
xrandr --output VGA-1 --mode 1680x1050_60.00 --pos 1680x0 --rotate normal

# now clone it
xrandr --output VGA-1 --same-as DVI-I-1

```

Using an old Nvidia card with Nouveau drivers, if that's a factor.

Any ideas?

---

### Post by CelticWarrior on 2021-03-29
You should only use the device's native resolution to avoid that. Instead you're forcing a resolution - for no good reason - that the projector must then downscale and what you complain of is the result and at least you have one to complain about! Most devices can't even do that.

---

### Post by wrybread on 2021-03-30
I'd love to use the native resolutions, but the native resolution of each display has a different aspect ratio. 

Using the --scale-from parameter I can scale the 1680x1050 down to 1024x768 for my projector's native resolution, but that still doesn't solve the aspect ratio issue.

Untested but something like: xrandr --output VGA-1 --scale-from 1680x1050 --same-as DVI-I-1

---

### Post by wrybread on 2021-03-30
Here's a one liner that does the following:

- sets my primary monitor to 1680x1050 resolution (it's native resolution)
- sets my projector to 1024x768 (it's native resolution)
- mirrors the primary monitor to the projector, scaling the resolution down to 1024x768

```

xrandr --output DVI-I-1 --mode 1680x1050_60.00 --output VGA-1 --mode 1024x768 --scale-from 1680x1050 --pos 1680x0 --rotate normal --same-as DVI-I-1

```

It works, but the aspect ratio is wrong on the projector. Here's a pic:

[IMG]http://sinkingsensation.com/stuff/projector_aspect_ratio_issue.jpg[/IMG]

It's a little hard to tell from my loosely hanging projection screen (soon to be fixed!), but the circle is being compressed.

---

### Post by Holger_Gehrke on 2021-03-30
You could define a 4:3 frame buffer with a width of 1680 (--fb 1680x1260) then set the laptop display to show from an offset (--pos 0x105) at its normal resolution and have the projector show the whole thing scaled down to 1024x768.
Something like (untested since I don't have displays on which I could test this ...)
```

xrandr --fb 1680x1260 --output DVI-I-1 --pos 0x105 --mode 1680x1050_60 --output  VGA-1 --mode 1024x768 --pos 0x0 --scale-from 1680x1260

```

Holger

---

### Post by TheFu on 2021-03-30
My playback software controls the aspect ratio.  I send the native resolution to the projector.

---

### Post by wrybread on 2021-03-31
@Holger_Gehrke: Thanks for that. To get that command to run without error I had to modify the resolution in --mode slightly, adding ".00":

```
xrandr --fb 1680x1260 --output DVI-I-1 --pos 0x105 --mode 1680x1050_60.00 --output  VGA-1 --mode 1024x768 --pos 0x0 --scale-from 1680x1260
```

With that change I can run the command without an error, but it doesn't actually set VGA-1 to 1024x768 (I think it's 1680x1260). Strange. The output of "xrandr" after running the command is:

```

wrybread@wrycade:~$ xrandr
Screen 0: minimum 320 x 200, current 1680 x 1260, maximum 8192 x 8192
DVI-I-1 connected primary 1680x1050+0+105 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200     59.95 +
   1600x1200     60.00
   1280x1024     75.02    60.02
   1280x960      60.00
   1152x864      75.00
   1024x768      75.03    70.07    60.00
   832x624       74.55
   800x600       72.19    75.00    60.32    56.25
   640x480       75.00    72.81    66.67    59.94
   720x400       70.08
   1680x1050_60.00  59.95*
   1920x1080_60.00  59.96
VGA-1 connected 1680x1260+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00*+  85.00    75.03    70.07
   1400x1050     59.98
   1280x1024     75.02    60.02
   1152x864      75.00
   832x624       74.55
   800x600       85.06    72.19    75.00    60.32    56.25
   640x480       85.01    75.00    72.81    59.94
   720x400       70.08
   1680x1050_60.00  59.95
HDMI-1 disconnected (normal left inverted right x axis y axis)
VGA-1-2 disconnected (normal left inverted right x axis y axis)
HDMI-1-2 disconnected (normal left inverted right x axis y axis)

```

I'll do some more tests.



And thank you @TheFu. 

> My playback software controls the aspect ratio. I send the native resolution to the projector.

Me too of course, but what would you do if you were mirroring to two different displays that have different aspect ratios? In other words sending a single output to two different monitors that have different aspect ratios? 

By the way thanks for your excellent advice on my previous question, where I was trying to play two HD videos simultaneously:

[https://ubuntuforums.org/showthread.php?t=2459267](https://ubuntuforums.org/showthread.php?t=2459267)

This is actually an evolution of the same problem. When I posted the above my way of playing the same video to two different monitors that have different aspect ratios was to play two instances of the video, one on each monitor, using mplayer's slave mode to keep them syncronized. So the master plays on monitor 1 (main monitor), and the slave plays on monitor 2 (projector), and things get letterboxed by mplayer as needed. That works well, except with very high resolution videos. I haven't figured out why exactly 1080p and higher videos won't play (the slave instance simply doesn't appear), but it's possible it's not simply the obvious issue with GPU capacity, it might be a scaling issue. Mplayer seems to have a lot of bugs with it's slave mode, like playlists going out of sync. 

The obvious and commonly recommended fix for that is to switch to MPV, but I haven't been able to get joystick input working with MPV. Mplayer works really well with joysticks (after compiling it with joystick support enabled), which is important for me since the main monitor in this case is an old arcade cabinet:

[IMG]http://sinkingsensation.com/stuff/cabinet1.jpg[/IMG]

The joysticks navigate a list of video categories, then pressing a button selects the video. I know I could convert the joystick signals to keystrokes, which would work with MPV, but this cabinet also works as a MAME cabinet for old video games so I'd rather not add complexity to the joystick signal. Another option is catching the joystick signals in Python/Pygame and sending commands to MPV.

[IMG]http://sinkingsensation.com/stuff/cabinet2.jpg[/IMG]

[IMG]http://sinkingsensation.com/stuff/cabinet3.jpg[/IMG]

The important thing is to play the video well on the projector, so I could conceivably make a "now playing" movie marquee style graphic to display on the arcade machine monitor describing what's playing on the projector, but it would be nice to get it to play well on both monitors.

---

