---
title: "Screen resolution is not in native resolution"
date: 2013-05-12
forum: General Help
---

### Post by derbydash on 2013-05-12
[FONT=verdana][SIZE=2]Hi, my [FONT=arial]Dell Latitude D260[/FONT] has a native screen resolution of [FONT=arial]1280x800[/FONT], in which when I first got it, it was set as [FONT=arial]1024x768[/FONT]. 

After upgrading Ubuntu to 12.10 from 12.04, my screen froze.

I rebooted the laptop and the BIOS screen had blue and red vertical lines running through the screen. */Graphics card corrupted?/*
When the log-in screen came up, everything was zoomed in but contained everything the screen was supposed to have.
I logged in as usual and the display screen was zoomed in as well.
I checked my Monitor Settings and it was set to [FONT=arial]800x600[/FONT].
The resolution options are: [FONT=arial]800x600, 640x480, 640x400, and 320x400[/FONT].
I turned off the laptop and left it off for a few days.
It was at its normal screen resolution at [FONT=arial]1024x768[/FONT]. After a while of using it, the screen froze and I forced it to shut down. 
Turned it on again and the same problem happened again, [FONT=arial]800x600[/FONT].

**SYSTEM INFO:**
DISTRIBUTION: Ubuntu 12.10: quantal (i686)
PROCESSOR: Genuine Intel©CPU T2500 @ 2.00GHz x2
GRAPHICS CARD 0: NVIDIA Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (256MB)

**TERMINAL:**
[/SIZE][/FONT][FONT=verdana][SIZE=2]```
[/SIZE][/FONT][FONT=verdana][SIZE=2]**$** [FONT=courier new]xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 400, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600         0.0* 
   640x480        60.0  
   640x400         0.0  
   320x400         0.0  
  1440x900_59.90 (0x7f)  106.3MHz
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   55.8KHz
        v: height  900 start  901 end  904 total  932           clock   59.9Hz
  1280x800_60.00 (0xba)   83.5MHz
        h: width  1280 start 1352 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  803 end  809 total  831           clock   59.8Hz
  &#8220;1024x768_60.00&#8243; (0xbd)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz
  1280X800_60.00 (0xbf)   83.5MHz
        h: width  1280 start 1352 end 1480 total 1680 skew    0 clock   49.7KHz
        v: height  800 start  803 end  809 total  831[/FONT]   
[FONT=verdana][SIZE=2]**$ **[FONT=courier new]cvt 1280 800 60[/FONT][B]
#[/B][FONT=courier new] 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync[/FONT][/SIZE][/FONT]
**$ **[FONT=courier new]xrandr --newmode "1280X800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19[/FONT]
```

 How will I go about to changing my screen back to its native resolution or at least back to [FONT=arial]1024x768[/FONT]?
[/SIZE][/FONT]

---

### Post by derbydash on 2013-06-21
[SIZE=1][FONT=verdana][FONT=garamond]**UPDATE:  **[/FONT]Okay, so now I looked through some things on my laptop and changed a few things around. 
Now my *Graphics* driver is: [FONT=garamond][B]VESA: G72 Board - travis1
[/B][/FONT]
Now, when I ran:
user@user-Latitude-D620:~$ [FONT=garamond]**xrandr**[/FONT]
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0  

```

I got it to be in the normal screen resolution (1024x768), **but** now the games I try to play are very laggy.
For example, when I play Tetris on Facebook, during gameplay, it freezes for about 5 seconds and/or it is slow (when I move the tetris piece to the right/left, it doesn't move as smooth as it supposed to be)(sometimes when I press the spacebar to drop the tetris piece, it freezes for 2 seconds and resumes but didn't drop the tetris piece).
I usually play the games on [FONT=garamond][POG]("http://pog.com")[/FONT], and most of them are very laggy, some run very smoothly though. 
When I play the games on [FONT=garamond][Not Doppler]("http://notdoppler.com")[/FONT], they don't lag (except the ones that have a lot of animation like Amateur Surgeon which lags a whole lot but still playable-ish).
The games on [/FONT][/SIZE][SIZE=1][FONT=verdana][FONT=garamond][GAMES]("http://games.com")[/FONT] are actually fine, they don't lag.

[/FONT][/SIZE][SIZE=1][FONT=verdana]I didn't have this problem, before my screen resolution was screwed up and after being able to change it back to 1024x768.
[/FONT][/SIZE]

---

### Post by derbydash on 2013-12-14
[SIZE=1][FONT=verdana][SIZE=2][B]TERMINAL:
[/B][/SIZE][/FONT][/SIZE][SIZE=1][FONT=verdana][SIZE=2]```
[/SIZE][/FONT][/SIZE]
[SIZE=2][FONT=verdana]**$** [SIZE=1][FONT=verdana][SIZE=2][FONT=courier new]xrandr[/FONT][/SIZE][/FONT][/SIZE]
[/FONT][/SIZE][SIZE=1][FONT=verdana][SIZE=2][FONT=courier new] xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0  
  1024x768_60.00 (0x181)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz
[/FONT]
```
```
[FONT=courier new]**[FONT=courier new][SIZE=2][FONT=verdana]$ [/FONT][/SIZE][/FONT]**cvt 1024 768 60
**[FONT=verdana]#[/FONT]** 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
**[FONT=courier new][SIZE=2][FONT=verdana]$ [/FONT][/SIZE][/FONT]**xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync[/FONT]
```

 **TERMINAL; CHANGE FILE PERMISSIONS:**[/SIZE]
[/FONT][/SIZE][SIZE=2]```
[SIZE=1][FONT=verdana][SIZE=2][FONT=courier new]**[FONT=courier new][SIZE=2][FONT=verdana]$ [/FONT][/SIZE][/FONT]**[/FONT][/SIZE][/FONT][/SIZE] [FONT=courier new]sudo su
[SIZE=1][FONT=verdana][SIZE=2][FONT=courier new]**[FONT=courier new][SIZE=2][FONT=verdana]$  [/FONT][/SIZE][/FONT]**[/FONT][/SIZE][/FONT][/SIZE]cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
[SIZE=1][FONT=verdana][SIZE=2][FONT=courier new]**[FONT=courier new][SIZE=2][FONT=verdana]$  [/FONT][/SIZE][/FONT]**[/FONT][/SIZE][/FONT][/SIZE]chmod 777 /etc/X11/xorg.conf
[/FONT][FONT=verdana][FONT=courier new][SIZE=1][FONT=verdana][SIZE=2][FONT=courier new]**[FONT=courier new][SIZE=2][FONT=verdana]$  [/FONT][/SIZE][/FONT]**[/FONT][/SIZE][/FONT][/SIZE]chmod 777 /etc/X11/xorg.conf.backup[/FONT]
[/FONT]
```[FONT=verdana]
**OPEN *FILES* FOLDER:**
[/FONT][/SIZE]
[LIST]
[*][SIZE=2][FONT=verdana][**[FONT=courier new]Ctrl + L[/FONT]**] (For location bar: able to type; no buttons) Type [FONT=courier new]**/etc/X11/ **[/FONT]into location bar
[/FONT][/SIZE] 
[*][SIZE=2][FONT=verdana]Locate files **xorg.conf** and **xorg.conf.backup** and *delete* them
[/FONT][/SIZE] 
[/LIST]
[B][SIZE=2][FONT=verdana]
TERMINAL:[/FONT][/SIZE][/B]
[LIST]
[*][SIZE=2][FONT=verdana]Type[FONT=courier new] **reboot**[/FONT]
[/FONT][/SIZE] 
[/LIST]


[SIZE=1][FONT=verdana]>> If when you log into your account and the screen resolution hasn't changed,
[LIST]
[*]Go to **Applications **> **System Tools/Settings** > **Preferences** > **Monitor Settings** 
[*]Go to **Menu** > Search **Monitor** > **Monitor Settings** 
[*]Open **Dash** > Search  **Monitor Settings **>** Monitor Settings** 
[*]-------- OR if you cannot change the screen resolution in Monitor Settings, 
[*]Go to [SIZE=1][FONT=verdana] **Applications **> **System Tools/Settings** > **Preferences** > **Displays**[/FONT][/SIZE] 
[/LIST]
[/FONT][/SIZE]

---

