---
title: "Feisty Compiz/Beryl Issues"
date: 2007-04-17
forum: General Help
---

### Post by emid on 2007-04-17
I just did a clean Feisty install on my laptop and would love to be able to get either compiz or beryl running again.  My graphics card isn't so great, but I was previously able to get beryl running on edgy using XGL.  I have an ATI Radeon R250 [Mobility FireGL 9000].  Is it possible to get this running with AIGLX or do I have to go back to the XGL method I had previously on Edgy.  Interestingly enough Compiz kinda works.  I can get it to start but the right 30% of the screen is totally messed up when I enable it.  When I try to run beryl from the terminal I get the following:
```

Checking maximum texture size                   : failed

Root window size (1400/1050) is bigger then maximum texture size (1024x1024)

X Error of failed request:  GLXBadContext
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  4 (X_GLXDestroyContext)
  Serial number of failed request:  39
  Current serial number in output stream:  41
```

If anyone has any input I'd appreciate it.

---

### Post by xanikseo on 2007-04-17
Maybe install some drivers that might optimise your performance?

---

### Post by emid on 2007-04-17
> **xanikseo said:**
> Maybe install some drivers that might optimise your performance?

My xorg.conf shows that I am using the "ati" driver.  Is there another one which should be better?  fglrx perhaps?

---

### Post by eggdeng on 2007-04-17
In /etc/X11/xorg.conf, section Screen, Display subsections, have you got the following? 
```

		Modes    "1024x768" "800x600" "640x480"

```
I think AIGLX with the ati Driver is the recommended way to go with your configuration, even more so if it worked for you before.

---

### Post by emid on 2007-04-17
> **eggdeng said:**
> In /etc/X11/xorg.conf, section Screen, Display subsections, have you got the following? 
```

		Modes    "1024x768" "800x600" "640x480"

```
I think AIGLX with the ati Driver is the recommended way to go with your configuration, even more so if it worked for you before.

This is what I have in the Screen section of my xorg.conf:
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
        EndSubSection
EndSection

```
On Edgy I had to use XGL to get it working. I was hoping that I wouldn't have to on Feisty.

---

### Post by eggdeng on 2007-04-17
OK. What I think the error message means is that AIGLX is finding a bigger size of display or higher resolution (1400/1050) than it can handle (1024x1024) which is why it can only cover 70% of the screen. So you need to reduce the resolution in xorg.conf.

First, back up your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Open the file
```
sudo gedit /etc/X11/xorg,conf
```
Substitute all occurences of the line
```
Modes           "1400x1050"
```
with
```
Modes    "1024x768" "800x600" "640x480"
```
You could do it using Find & Replace. Save, close the file and restart gnome with Ctrl-Alt+Backspace. (You might need to do startx.) If gnome won't start, undo the previous steps.
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
``` & you're at least no worse off than before.

---

### Post by emid on 2007-04-17
Does that mean that I'm going to have to run in 1024x768 resolution mode?

---

### Post by emid on 2007-04-17
I'm confused as to why I didn't have this issue in Edgy.  It seems that if it was able to support 1400x1050 before, it should be able to on Feisty as well.  Since it is a laptop it looks pretty bad if I have to run it at a non-native resolution.  Any other suggestions?

---

### Post by emid on 2007-04-19
No suggestions? Anyone? :(

---

### Post by eggdeng on 2007-04-19
Try it and see. My laptop, which has that line in xorg.conf, actually runs at 1280 x 800.

---

### Post by db9s on 2007-04-19
beryl svn guys should be on it. Its nothing new, just run beryl as a "copy" . Advanced beryl options -> rendering path-> copy. This should be a temporary solution for now.

---

### Post by lognok on 2007-04-21
Hi emid, I got compiz working in aiglx by doing nr 2 in this guide:
[http://ubuntuforums.org/showthread.php?t=293002&highlight=%2Fetc%2Fdrirc](http://ubuntuforums.org/showthread.php?t=293002&highlight=%2Fetc%2Fdrirc)

Then I got wobbly windows and rotating cube working without the loss of screen resolution on the right side of the screen.

I have a ATI mobility 9000 on my laptop runnning at 1400x1050.

Funny thing is that I can't get the cube effect to work again after the first attempt. I had to install gnome-compz-manager to manage that, and then only when I get the windows refreshed am I able to select rotating cube and select how many workspaces should be available. Next I need to enable 'GL Desktop' to start-up, cause every time I restart xserver I loose rotating cube.

Also check this link:
[http://forum.beryl-project.org/viewtopic.php?f=36&t=2789](http://forum.beryl-project.org/viewtopic.php?f=36&t=2789)
the last post describes something about why you run out off memory and can't go beyond 1024x1024 resolution.

AND the final thing: Simply Mepis 6.5 runs 3D on my ATI M9000 without any problems in live mode. Why can Mepis do it, when Ubuntu can't? (is it something to do with Mepis running Beryl on AIGLX vs Ubuntu running Compiz on AIGLX?)

---

