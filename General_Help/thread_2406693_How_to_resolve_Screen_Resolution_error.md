---
title: "How to resolve Screen Resolution error"
date: 2018-11-24
forum: General Help
---

### Post by Richard_York on 2018-11-24
I have a desktop machine newly running Ubuntu 18LTS, with dual boot to Windows 10 for rare occasions. I set it up using a spare Acer screen to allow continued use of our old machine until making the switch over.

Our preferred screen is an old Samsung Syncmaster 172v  which should have 1280 x 1024 resolution. Going to Settings/Devices showed "Unknown display", and the actual screen display didn't quite fit. 
While trying to improve this, a mix of sheer ignorance and mouse slip meant I clicked on something quite different. Now only the lower part of the Bionic Beaver arrives, the top of the display is somewhere way above the actual screen. 

So I can't find a way of getting my cursor up to that part of the Settings/Devices to change it, as this normally appears at the top of the display.

When I plug the Acer screen in, the machine recognises it straight away and adjusts accordingly, so while I could change settings, there's no point in doing so while using this screen, I take it.
When I plug the Samsung back in, the settings revert to the one I mistakenly saved; I'm in a sort of catch-22 here.

The Acer screen works, but is just too big for the space available, so we'd really like to swap back to the Samsung.

Thanks for any help.

---

### Post by CatKiller on 2018-11-25
You may be able to use Ctrl - Alt - F2 to get to a command line, and then use an appropriate xrandr command to change the resolution of your desktop. I'm typing from my phone, so I can't give you detailed instructions, but that might point you in the right direction.

---

### Post by NM5TF on 2018-11-26
@Richard_York....

have you tried xrandr yet ???

with the Samsung monitor plugged in, post the output of

```
xrandr
```

you will see something like this

```
[tommy@tommy ~]$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 4096 x 4096
VGA-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080     60.00*+
   1366x768      59.79  
   1280x800      59.81  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32  
   640x480       75.00    72.81    59.94  
   720x400       70.08  

```

this will show you what the system thinks the available resolutions are...

if your preferred resolution of 1280 x 1024 is not listed, try this

```
cvt 1280 1024
```

you will see something like this

```
tommy@tommy ~$ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

```

post the output here using code tags please...

tommy

---

### Post by Richard_York on 2018-11-27
Thanks.
With the Samsung screen in all looks normal until I log in, when it changes to the oversized version.

Ctrl-Alt-F2 gets no response, but pressing the Super key brought a Search box just enough in view, to type "Terminal"
I couldn't work out how to show what comes up without photographing the screen this time, so apologise it's not in code tags, but here's what I got:
[ATTACH=CONFIG]281776[/ATTACH]
The Line starting "DVI-D-O connected" has the correct 1280x1024 figure shown. I'm hoping the rest tells you enough to lead me back towards it displaying correctly.
Thanks again.

---

### Post by CatKiller on 2018-11-27
OK, so a couple of things.

That +1024 implies to me that your display is offset in some fashion - perhaps inside a larger virtual resolution?

If you're looking at a small part of a larger virtual display, you may be able to pan around by moving the cursor to the edges.

If you're able to see part of the window you're interested in, holding Alt and left-click-and-drag will move it. Hopefully to the point that you can set things more appropriately.

Some of the resolution-setting tools that use xrandr store their configuration in ~/.config/monitors.xml. If all else fails, you could try editing that file directly or nuking it.

---

### Post by NM5TF on 2018-11-27
> **Richard_York said:**
> Thanks.
With the Samsung screen in all looks normal until I log in, when it changes to the oversized version.

Ctrl-Alt-F2 gets no response, but pressing the Super key brought a Search box just enough in view, to type "Terminal"
I couldn't work out how to show what comes up without photographing the screen this time, so apologise it's not in code tags, but here's what I got:
[ATTACH=CONFIG]281776[/ATTACH]
The Line starting "DVI-D-O connected" has the correct 1280x1024 figure shown. I'm hoping the rest tells you enough to lead me back towards it displaying correctly.
Thanks again.

it shows that your preferred resolution of 1280 x 1024 IS being selected....something about the modeline doesn't seem correct....the "extra" 1024....almost looks
like an offset on the horizontal axis

specs on this monitor call for 75 Hz refresh rate...yours is set for 60 Hz....

try this ```
cvt 1280 1024
``` post the output here...

to use code tags....use the "advanced" reply button.....

copy the terminal output with your mouse...

use the # icon for code tags, and paste the output between the #s....much easier to see over a photo...

tommy

---

### Post by Richard_York on 2018-11-29
Thanks. The response to cvt 1280 1024 is
```
richard@LizardsDesktop:~$ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
richard@LizardsDesktop:~$ 


```
I also tried alt left-click and drag, and it doesn't appear to have any effect.
I hope this is typo free - I'm using that Samsung screen, distortion and all, and iit's really hard to read!

---

### Post by CatKiller on 2018-11-29
> **Richard_York said:**
> I also tried alt left-click and drag, and it doesn't appear to have any effect.

That's a shame. Normally it works like dragging on the titlebar, but holding Alt means that you can do it by clicking anywhere on the window. It would have made your life a lot easier for this.

I'm really struggling to think of what setting you might have selected to give the symptoms you're seeing, of the correct resolution being selected but not fitting on the screen. 

Did you have anything in your monitors.xml file?

---

### Post by Richard_York on 2018-11-29
Forgive my ignorance, but where do I find that? I tried searching in my "home" folder and nothing came up.

---

### Post by CatKiller on 2018-11-29
> **Richard_York said:**
> Forgive my ignorance, but where do I find that? I tried searching in my "home" folder and nothing came up.

Files whose name starts with a . are hidden by default. You can use Ctrl-H (I think) to show them. Otherwise, ```
cat ~/.config/monitors.xml
``` will show you the contents from the command line.

If the file exists and has something in it, it gives us options.

---

### Post by NM5TF on 2018-11-29
> **Richard_York said:**
> Thanks. The response to cvt 1280 1024 is
```
richard@LizardsDesktop:~$ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
richard@LizardsDesktop:~$ 


```
I also tried alt left-click and drag, and it doesn't appear to have any effect.
I hope this is typo free - I'm using that Samsung screen, distortion and all, and iit's really hard to read!

you might try this

```
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
```

and then do this

```
xrandr --addmode DVI-D-0  1280x1024_60
```

then finally

```
xrandr --output DVI-D-0 --mode 1280x1024_60
```

the screen might flicker as it changes resolution.....

let us know if this works

tommy

---

### Post by Richard_York on 2018-11-29
The result is long...```
richard@LizardsDesktop:~$ cat ~/.config/monitors.xml
<monitors version="2">
  <configuration>
    <logicalmonitor>
      <x>0</x>
      <y>0</y>
      <scale>1</scale>
      <primary>yes</primary>
      <monitor>
        <monitorspec>
          <connector>VGA-0</connector>
          <vendor>unknown</vendor>
          <product>unknown</product>
          <serial>unknown</serial>
        </monitorspec>
        <mode>
          <width>1024</width>
          <height>576</height>
          <rate>59.899215698242188</rate>
        </mode>
      </monitor>
    </logicalmonitor>
    <logicalmonitor>
      <x>1024</x>
      <y>0</y>
      <scale>1</scale>
      <monitor>
        <monitorspec>
          <connector>DVI-D-0</connector>
          <vendor>SAM</vendor>
          <product>SAMSUNG</product>
          <serial>HSDX336203</serial>
        </monitorspec>
        <mode>
          <width>1280</width>
          <height>1024</height>
          <rate>60.019741058349609</rate>
        </mode>
      </monitor>
    </logicalmonitor>
  </configuration>
  <configuration>
    <logicalmonitor>
      <x>0</x>
      <y>0</y>
      <scale>1</scale>
      <primary>yes</primary>
      <monitor>
        <monitorspec>
          <connector>VGA-0</connector>
          <vendor>unknown</vendor>
          <product>unknown</product>
          <serial>unknown</serial>
        </monitorspec>
        <mode>
          <width>1152</width>
          <height>864</height>
          <rate>59.997058868408203</rate>
        </mode>
      </monitor>
    </logicalmonitor>
    <disabled>
      <monitorspec>
        <connector>DVI-D-0</connector>
        <vendor>ACR</vendor>
        <product>Acer AL1913</product>
        <serial>ETL3609234   </serial>
      </monitorspec>
    </disabled>
  </configuration>
</monitors>
richard@LizardsDesktop:~$ 

  
```I hope this helps.
Forgive a pause, I'll soon be away from this machine until Sunday night, will respond again on my return.
Thanks.again!

---

### Post by CatKiller on 2018-11-29
> **Richard_York said:**
> The result is long...I hope this helps.
Forgive a pause, I'll soon be away from this machine until Sunday night, will respond again on my return.
Thanks.again!

Awesome. That seems to be the configuration for both monitors that you've used. Renaming that to something else and then logging back in may put you back to where you were before your slip.

---

### Post by Richard_York on 2018-11-29
Thanks.
 While I'll have to wait before trying the next step now, I'm sorry, I don't currently have enough knowledge to understand how to work "Renaming that to something else" - which bits to rename what, and how to go about it.

---

### Post by CatKiller on 2018-11-29
> **Richard_York said:**
> Thanks.
 While I'll have to wait before trying the next step now, I'm sorry, I don't currently have enough knowledge to understand how to work "Renaming that to something else" - which bits to rename what, and how to go about it.

It's just ```
mv ~/.config/monitors.xml ~/.config/monitors.xml.backup
``` or renaming it in the file manager.

It's a safer first step than deleting things, since it's simple to rename it back if everything goes pear shaped, even from a live USB.

---

### Post by Richard_York on 2018-12-04
Please excuse the pause. 
I just  tried suggestions from the last few posts. Here's the result of all.
This screen is so stretched it's very hard to see what I'm typing, so I just copied and pasted everything on the terminal screen.
```
richard@LizardsDesktop:~$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
richard@LizardsDesktop:~$ xrandr --addmode DVI-D-0  1280x1024_60
xrandr: cannot find mode "1280x1024_60"
richard@LizardsDesktop:~$ xrandr --output DVI-D-0 --mode 1280x1024_60
xrandr: cannot find mode 1280x1024_60
richard@LizardsDesktop:~$ richard@LizardsDesktop:~$ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
richard@LizardsDesktop:~$: command not found
richard@LizardsDesktop:~$ richard@LizardsDesktop:~$ xrandr --addmode DVI-D-0  1280x1024_60
richard@LizardsDesktop:~$: command not found
richard@LizardsDesktop:~$ xrandr: cannot find mode "1280x1024_60"

Command 'xrandr:' not found, did you mean:

  command 'xrandr' from deb x11-xserver-utils

Try: sudo apt install <deb name>

richard@LizardsDesktop:~$ richard@LizardsDesktop:~$ xrandr --output DVI-D-0 --mode 1280x1024_60
richard@LizardsDesktop:~$: command not found
richard@LizardsDesktop:~$ xrandr: cannot find mode 1280x1024_60

Command 'xrandr:' not found, did you mean:

  command 'xrandr' from deb x11-xserver-utils

Try: sudo apt install <deb name>

richard@LizardsDesktop:~$ richard@LizardsDesktop:~$ 
richard@LizardsDesktop:~$: command not found
richard@LizardsDesktop:~$ 

```

---

### Post by CatKiller on 2018-12-04
Your monitors.xml is showing a phantom 1024×576 display. I really think you should nuke that file to get to how you were before your "slip."

---

### Post by Richard_York on 2018-12-04
Thanks. 
For some reason there was a phantom display problem with the new NVIDIA graphics card while the machine was still running on Windows 10 alone, then again after I installed Ubuntu, when MuseScore (but nothing else so far) also decided it was only going to display on a phantom screen. I don't know if any of this is related or relevant.
 But neither do I yet know how to "nuke that file", I'm sorry. What steps do I need to take?

---

### Post by CatKiller on 2018-12-04
> **Richard_York said:**
> But neither do I yet know how to "nuke that file", I'm sorry. What steps do I need to take?

```
mv ~/.config/monitors.xml ~/.config/monitors.xml.backup
```

then logging out and logging in should do it.

---

### Post by Richard_York on 2018-12-06
Thank you again, I finally got to try this and it worked. Great stuff.
The cursor still doesn't stop at the Right side of the screen, it happily vanishes off the edge, though it stops on the other three. This doesn't seem to be creating a big problem.

If there's a way of persuading it the screen really does stop at the Right edge that would be good too, but we can live with it as it is.

I appreciate the patient help.

---

### Post by CatKiller on 2018-12-06
That is very good news. It seems like it now simply thinks that the screen is wider than it is (maybe it's put the phantom screen to the right?) but at least it's usable now, so you can see what you're doing.

---

### Post by Richard_York on 2018-12-07
All down to help received here - as I said, I'm very grateful for the work you and others put in to help those with little understanding, like me! I'll mark this as solved now.

---

### Post by him610 on 2018-12-07
> it happily vanishes off the edge
FWIW, don't know if this will help or not, but I have a monitor where the display continually was misaligned and the mouse pointer would disappear off the edge of the screen. The display was always too far over to the right. It has been several years now, but I think I used the postioning tools on the monitor itself to both adjust the width of the display and center it so the display would align with the physical edges of the monitor. I still use that particular monitor with no obvious misalignment.

---

