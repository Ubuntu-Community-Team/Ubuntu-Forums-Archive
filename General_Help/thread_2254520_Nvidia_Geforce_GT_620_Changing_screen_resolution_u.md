---
title: "Nvidia Geforce GT 620: Changing screen resolution using the nouveau driver?"
date: 2014-11-27
forum: General Help
---

### Post by ineuw on 2014-11-27
I am using Xubuntu 14.04 with an Nvidia Geforce GT 620 video card, and after repeated and unending problems with Nvidia drivers I swiched to using the "nouveau" driver. It work fine but I would like to change the current resolution of 1280x720 to 1408x792 which is also a valid 16:9 resolution. I know that both the video card and the monitor (LG 22" LED HDMI monitor) accepts this resolution without problems. The current resolution was inherited from the previous Nvidia driver version 340.58, which was set to this resolution. 

I 've already gone through all available Nvidia drivers, but there is no difference in image quality and the resolution offered in each is the same as specified in the EDID.

Is it possible to modify the nouveau driver to this resolution and what are the steps to implement it?

---

### Post by ajgreeny on 2014-11-27
Does command **xrandr** in terminal show that resolution is available to you?

---

### Post by ineuw on 2014-11-27
> **ajgreeny said:**
> Does command **xrandr** in terminal show that resolution is available to you?

The short answer is no. However, when using the Nvidia driver, I created a custom EDID with the Phoenix EDID editor in Windows and this worked fine until Wine crashed my video and couldn't repair the installation. So, I had to re-install from scratch, and no longer using wine. I used several NVidia drivers with this custom EDID, but couldn't get it working. The driver I used, is no longer available in the Nvidia archives.

---

### Post by carlwsnyder on 2014-11-28
Look at the Ubuntu wiki at [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) with the mode line of ```
xrandr --newmode "1408x792_60.00"   90.75  1408 1480 1624 1840  792 795 800 823 -hsync +vsync
xrandr --addmode VGA-1 "1408x792_60.00"
xrandr --output VGA-1 --mode "1408x792_60.00"
```  The specific information is for 1408x792 at 60 Hz refresh rate.  For a different mode line, use the terminal command **cvt horiz vert ref** where horiz is your horizontal resolution, vert is the vertical resolution, and refresh is the refresh rate in Hz.  Replace VGA-1 with whatever is your active display from **xrandr**&#8203; on a line by itself in your terminal.

---

### Post by ineuw on 2014-11-28
> **carlwsnyder said:**
> Look at the Ubuntu wiki at [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) with the mode line of 
```

xrandr --newmode "1408x792_60.00"   90.75  1408 1480 1624 1840  792 795 800 823 -hsync +vsync
xrandr --addmode VGA-1 "1408x792_60.00"
xrandr --output VGA-1 --mode "1408x792_60.00"
```  The specific information is for 1408x792 at 60 Hz refresh rate.  For a different mode line, use the terminal command **cvt horiz vert ref** where horiz is your horizontal resolution, vert is the vertical resolution, and refresh is the refresh rate in Hz.  Replace VGA-1 with whatever is your active display from **xrandr**&#8203; on a line by itself in your terminal.

Thanks for the reply. Unfortunately, this was my very first attempt months ago. It failed with each of many attemps and I don't have the old error messages. But then, I was using an Nvidia driver. 

Here is today's message

ineuw:~$ xrandr --newmode "1408x792_60.00"   90.75  1408 1480 1624 1840  792 795 800 823 -hsync +vsync

ineuw:~$ xrandr --addmode HDMI-0 "1408x792_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  29
  Current serial number in output stream:  30

I also undertook to paste the Xorg.0.log contents here: [http://paste.ubuntu.com/9289098/](http://paste.ubuntu.com/9289098/) hoping it will provide a clue as to what I am doing wrong. As for the link to the resolution, I''ve read the page as well

---

### Post by carlwsnyder on 2014-11-29
According to your pastebin, you might be having problems from two different areas:  1) You seem to still have detected portions of the nVidia 343 driver still installed,  and 2) Your EDID reports a contradiction, the custom EDID wants a vertical refresh rate of 24 Hz for the 1920x1080 resolution, but the reported refresh rate limits are from 57-63 Hz, with corresponding Horizontal and Vertical frequencies contraindicated.  You need to get better information on your monitor to fix your custom EDID, possibly from the manufacturer's website or from a user manual for the display.

I am unable to determine if the new errors which you are reporting are from a mismatch with the custom EDID you made or a mismatch with the actual operating display.

---

### Post by ineuw on 2014-11-29
> **carlwsnyder said:**
> According to your pastebin, you might be having problems from two different areas:  1) You seem to still have detected portions of the nVidia 343 driver still installed,  and 2) Your EDID reports a contradiction, the custom EDID wants a vertical refresh rate of 24 Hz for the 1920x1080 resolution, but the reported refresh rate limits are from 57-63 Hz, with corresponding Horizontal and Vertical frequencies contraindicated.  You need to get better information on your monitor to fix your custom EDID, possibly from the manufacturer's website or from a user manual for the display.

I am unable to determine if the new errors which you are reporting are from a mismatch with the custom EDID you made or a mismatch with the actual operating display.

The contradicton exists in the original EDID, and I will re-edit an original copy to try to eliminate the issue. I became aware of the two different drivers, after I posted the Xorg.0.log and then I studied it line by line. (Please keep in mind that I am completely new at this and learning as I go along.) I tried to get rid of the Nvidia 343.22 driver through the terminal, and was surprised that it still exists. I am also aware that there is an additional 343.58 installed and dormant, stored somewhere, wherever that is. I will post the results again.

---

### Post by ineuw on 2014-11-30
carlwsnyder, many thanks for your help. Unfortunately, I made such a mess of the Nvidia installations (three NVidia drivers were recognized) and I could not remove any of them. In the process of trying I crashed Xubuntu. No matter, I made a fresh install as no data was lost, only time (the data is stored on another drive). With the fresh install, I carefully upgraded "nouveau" to its current version and your solution works like a charm. I can change to any 16:9 resolution I prefer.

My question is, how do I make the change permanent after I end the session. I guess that a script is the solution but where to place it so that it installs at the right time of the boot.  Thanks again.

---

### Post by coldcritter64 on 2014-11-30
> My question is, how do I make the change permanent after I end the session.You could add the xrandr commands to a script in your user "bin" folder in your home directory "/home/<user>/bin" and point a startup entry to it each time you boot into xfce.

You may need to create the folder "/home/<user>/bin"; if you do need to, do a log out and log back into your desktop environment to activate its use with the system path. Call the script "xrandr-mode" or some such name and put in the contents below, _*alter the*__* "--addmode VGA-1" and  "--output VGA-1" code to suit your install.*_

eg.> ```
#!/bin/bash

xrandr --newmode "1408x792_60.00"   90.75  1408 1480 1624 1840  792 795 800 823 -hsync +vsync;
xrandr --addmode VGA-1 "1408x792_60.00";
xrandr --output VGA-1 --mode "1408x792_60.00";

exit 0
```Set the file executable, right click the file > Properties > Permissions Tab > Tick the Execute/Program box.

By pointing a startup entry at the script in xfce menu > Settings > Session and Startup > Application Autostart Tab > Add ... Set the command as the script in your ~/bin folder, I named "xrandr-mode" above, name and give a description, click OK. Now everytime you boot into xfce that resolution will be set up by the start up entry.

I use this "startup" method to set up dual monitors with a xrandr command in xfce on each startup; when the xfce interface itself doesn't allow for such a set up easily. It may work for you, cheers. :) coldcritter64

---

### Post by ineuw on 2014-11-30
coldcritter64, my gratitude. It works perfectly well on login. I always knew that Aussies are special.

---

