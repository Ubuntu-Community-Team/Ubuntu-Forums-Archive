---
title: "Need help with 3D desktop Compiz/Beryl"
date: 2006-11-04
forum: General Help
---

### Post by shaft350x on 2006-11-04
I'm new to the whole Linux thing.  I have switched from Edgy to Dapper and back to Edgy.  Just trying to figure out how to get all this to work and not break my box (hence the first switch from Edgy to Dapper...I broke X).

Currently I am running:
2.6.17-10-generic
Edgy Eft
[Dual booting, still have XP on this box]

On:
CPU AMD|A64 3400+ 2.4G 754 512K
NVidia GeForce XFX 6800XT 256MB
MB BIOSTAR NF325-A7 NF3-250 754

(I just upgraded this system myself this summer to run Oblivion in XP)

After much frustration I was finally able to get Beryl on this system using this HOWTO [http://ubuntuforums.org/showthread.php?t=263851&highlight=edgy+nvidia+beryl](http://ubuntuforums.org/showthread.php?t=263851&highlight=edgy+nvidia+beryl)

Unfortunately I don't know how to make any changes with it.  I change stuff but have no way of effecting that change (rather I don't know how to make it change)

Ultimately I want to do the Cubed desktop (part of my draw to finally make the jump to linux)  I believe that I need Compiz to do this.  I tried using this HOWTO to get compiz
[http://ubuntuforums.org/showthread.php?t=263840](http://ubuntuforums.org/showthread.php?t=263840)

when I do that I get 
E: Couldn't find package gnome-compiz-manager

So any help would be appreciated.  Thanks in advance.
~J

---

### Post by Joe_CoT on 2006-11-04
Are you sure you're currently running Beryl? When running beryl, the beryl manager (an emerald in your system tray) includes an option for the setting manager; all the effects (animation, cube, etc) are plugins, and you can enable/disable and configure them separately.

---

### Post by shaft350x on 2006-11-04
Ok, so I wasn't actually running it...now when I've got it going if I make changes I get the "no buttons, no right click" problem.  I'm pretty sure there is a a howto on this, but I guess I'll have to look that up.  Any other tips/advice on how to get this up and running quickly and smoothly?

Thanks for that step too.  I used the terminal then did a sudo beryl-manager command to get it started.  I should probably figure out how to get it to start on boot though.

(How do I do the "code" box on the forum?)

---

### Post by PriceChild on 2006-11-04
Compiz/Beryl is NOT a beginners subject.

I have moved this thread.

---

### Post by Joe_CoT on 2006-11-04
[ code] this is the code [/ code] (without the space)

The "no buttons, no right click" problem? as in you can't click on the system tray icon? I had that after one update or another; it fixed itself, and i could still get to it from the system -> preferences menu

---

### Post by shaft350x on 2006-11-04
System pretty much locks up.  I can move the mouse but that is it.  Right cliking doesn't work, alt+click, ctrl+click, same with TAB.  I've had to use alt+ctrl+bkspc to restart it so I could get back to doing things.  Can't type either. (Thought I might try a kill command when I had the terminal up but it wouldn't accept typing.)

I managed to get it to do that after starting beryl and then using the "Reload Window-Manager" option.

Found someone else having the no buttons/borders problem

[http://ubuntuforums.org/showthread.php?t=292120&highlight=beryl+no+buttons](http://ubuntuforums.org/showthread.php?t=292120&highlight=beryl+no+buttons)

doesn't look like they've fixed it.  I tried
```
 sudo apt-get update
sudo apt-get upgrade 
```
and nothing seems to need upgrades.

---

### Post by Joe_CoT on 2006-11-04
What the means is that beryl isn't actually working correctly; if you start metacity, you'll see it works just fine. Your lack of buttons/toolbars/etc means that beryl didn't actually start, and that it's in window manager limbo. try running beryl from a console to see what errors it gives.

---

### Post by shaft350x on 2006-11-04
I'm guessing by running from a console you mean a command line like Terminal?

I used Terminal and typed in "beryl"  it read something like
```
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
```

I'm pretty sure that is where it stopped.

Thanks again for taking the time to help me with this, I really appreciate it!

---

### Post by Joe_CoT on 2006-11-04
Do the following:
```
glxinfo | grep direct
```

Is direct rendering on? If not, you'll want to look at /var/log/Xorg.0.log to see where DRI dies

---

### Post by shaft350x on 2006-11-05
Direct rendering is on.

---

### Post by shaft350x on 2006-11-05
Any thing else I can try to get this working?

---

### Post by Joe_CoT on 2006-11-06
I'm not entirely sure why it would check for XGL twice ...
Can you do this from a console:

```
gdb /usr/bin/beryl
```

Then at the gdb command line, type
```

run

```
and post the output?

---

### Post by igknighted on 2006-11-06
Start beryl the way you usually do then try running the command

```
emerald --replace
```

I set a launcher button to launch beryl-manager and issue the emerald --replace command at the same time and it works fine for me every time.

---

### Post by shaft350x on 2006-11-08
the gdb simply gave me the same output as before.  Looks like it goes into a loop.  Perhaps this is why the system is locking up?  Infinite loop looking for XGL?

---

### Post by shaft350x on 2006-11-08
I tried the --replace trick, and while my system didn't lock up, none of the changes took place.  The command line kept saying "Reloading..." with nothing really happening.

---

### Post by shaft350x on 2006-12-02
Any other advice?

---

### Post by jsteve54302 on 2006-12-04
You may want to make sure that that Compositing and ARGB Visuals are turned on.  In the terminal program of your choice, open the xorg.conf file file for editing as root (and detach the editor from yout terminal) by typing:

```
gksudo gedit /etc/X11/xorg.conf &
```enter your root password, then add the line

```
Option "AddARGBGLXVisuals" "True"
```in the "Screen" section of xorg.conf, and create this section (if it doesn't exist) at the end of the file:

```
Section "Extensions"
    Option "Composite" "1"
EndSection
```The last *shouldn't* be needed in Edgy, but it won't hurt.  If this section already exists, just edit the value following "Composite" from 0/False/Disable to 1/True/Enable (the values within each group do the same thing), keeping the double quotes.

Save the file, log out, and press <ctl>-<alt>-<bkspc> to restart.

If this doesn't work, you may need to reinstall your video drivers, and how you do that depends on your video card.  Post your video card info, and someone should be able to point you towards a good how-to.

---

### Post by shaft350x on 2006-12-06
Umm that just bricked my Ubuntu.  I added the Composite thing to my Xorg.conf file, and now I get a big blue greeting screen telling me I messed things up, and I cannot boot into Ubuntu until I fix it.  So how do I fix it?

I backed it up, but I don't know how to overwrite the file, or open it up and edit it outside of Ubuntu.

Help would be appreciated...

---

### Post by shaft350x on 2006-12-06
Managed to get help on using my backup file to overwrite the one that broke my X.

The extensions thing did it.  I already have the ```
Option "AddARGBGLXVisuals" "True"
``` in there.

---

### Post by kakalaky on 2006-12-06
I had to add Option "AddARGBGLXVisuals" "True" to the Device section instead of Screen to get it to work with my 6800GT.

---

### Post by shaft350x on 2006-12-06
On the plus side I was able to make the changes suggested to the xorg.conf file and not have it crash on me.

The downside is that beryl-manager still doesn't work.  I had the terminal open this time that I just tried and it said it was looking for XGL and couldn't find it.

---

### Post by DarkN00b on 2006-12-06
If the above fixes don't work, try this. Beryl is a fork of Compiz so some of the configs from your Compiz installation could be interfering. At the command line type

```
beryl-settings
```

This should open the Beryl settings manager without loading Beryl. Then go through every option and click every "Revert" button you can find. I'm not on my Ubuntu machine right now, but this may not be necessary because I think there is a button on the bottom left of the settings manager window to reset all options.

---

### Post by jsteve54302 on 2006-12-06
> **shaft350x said:**
> Umm that just bricked my Ubuntu.  I added the Composite thing to my Xorg.conf file, and now I get a big blue greeting screen telling me I messed things up, and I cannot boot into Ubuntu until I fix it.  So how do I fix it?

I backed it up, but I don't know how to overwrite the file, or open it up and edit it outside of Ubuntu.

Help would be appreciated...

Oops...  My bad... :oops:  I think I made a stupid assumption...  Before I make any more potentially system-breaking advice, what version of the nVidia video driver are you using?  I didn't notice earlier in the thread.  Beryl only works without XGL on the latest nVidia version, not Ubuntu repository version. It seems that beryl-manager is getting stuck when it can't find XGL or nVidia.  You may need to install/reinstall XGL, and make sure that gdm is using the xgl x server instead of xorg (i think - flame me if I'm wrong, but I've never used XGL, so I'm not sure how to fix it if it's broken).  You may also try the latest drivers from nVidia, but probably not both methodsat the same time.  Using method 2 at [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy) worked for me, with no XGL, but I have a 7950 GT KO, not a 6800 series, and it seems video driver installation sometimes depends on the phase of the moon :) .  However, before following my advice again, you may wish to search these forums for howtos/advice...  Esp, try searching for "xgl howto" and "nvidia driver howto" (without the quotes).  Oh, yes, I also realised that on my system, I also had to add 
```
Option  "AllowGLXWithComposite" "True"
```to the "Extensions" section.  The log claims  it's ignoring an unknown extension, but Xorg crashed when I took it out, so it must be doing something :).

My humble apologies,

---

