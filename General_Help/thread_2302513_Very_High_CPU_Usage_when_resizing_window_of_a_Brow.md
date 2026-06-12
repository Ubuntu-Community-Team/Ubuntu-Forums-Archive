---
title: "Very High CPU Usage when resizing window of a Browser on Ubuntu 14.04"
date: 2015-11-11
forum: General Help
---

### Post by snarkyCoder on 2015-11-11
I switched from a Windows machine to Linux to do web development and so far it's been very nice.

Recently the downside has been that when reviewing some web designs I hear the fans going full throttle while I resize the browser window ...
It does this with Firefox and with Chrome as well...
I run **htop** and see the CPU going full... some times over 100% if I am reading right... the highest has been 720% :confused:

I don't have a graphics card yet but in my windows system this would not happen even though I was a laptop with an intel i3 CPU using the integrated graphics...

Has anyone had the same issue?
Do I have the correct driver for the 
intel graphics 4600??

**sudo lshw -c video**
  [INDENT]*-display               
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0[/INDENT]

**System**
[INDENT]Ubuntu 14.04
CPU: Intel i7-4790
GPU: Intel Graphics 4600
RAM: 16GB @ 1866Hz[/INDENT]

---

### Post by ajgreeny on 2015-11-11
Which process is showing as cpu hog in htop; is it the browser?

I normally use top and sort by cpu % with a press of upper case C, rather than htop with upper case P, which confuses me more, though I am sure you get the same info from both.

---

### Post by vasa1 on 2015-11-11
> **snarkyCoder said:**
> I switched from a Windows machine to Linux to do web development and so far it's been very nice.

Recently the downside has been that when reviewing some web designs I hear the fans going full throttle while I resize the browser window ...
It does this with Firefox and with Chrome as well...
...
Have you tried turning off hardware acceleration in your browser settings?

---

### Post by grahammechanical on 2015-11-11
Do integrated video systems have active or passive cooling? Be glad the motherboard is responding to rises in temperature caused by increased activity.

I have no experience of integrated graphics but there may be a settings utility like the one that comes with the Nvidia driver that I am using. I can see how the GPU scales up and down its performance level depending on what is happening on the user interface. It also gives a temperature reading.

What we have in a browser window will also affect the amount of work the GPU has to do when we move a browser window. Some web sites have lots of images and even videos playing. Tabs that are open but not in the main window still have to be re-drawn even though they are out of our sight.

I have installed a utility called Psensor. That monitors all the fan speeds and temperatures of the CPU, GPU, motherboard and hard disks. We can set alarm levels. and we do not have to rely on our sense of hearing alone.

Regards.

---

### Post by snarkyCoder on 2015-11-11
> **ajgreeny said:**
> Which process is showing as cpu hog in htop; is it the browser?

I normally use top and sort by cpu % with a press of upper case C, rather than htop with upper case P, which confuses me more, though I am sure you get the same info from both.

I don't know how to copy the entire line of the process in htop but this is what I got

**Chrome**
/opt/google/chrome/chrome --type=gpu-process --channel=2643.0.2047039655 --supports-dual-gpus=false --gpu-driver-bug-workarounds=2,45,57 --disable-gl-extensions=GL_ARB_occlusion_query GL_ARB_occlusion_query2 -
/opt/google/chrome/chrome --type=renderer --lang=en-US --force-fieldtrials=AffiliationBasedMatching/Enabled/AppBannerTriggering/Aggressive/AudioProcessing48kHzSupport/Default/*AutofillClassifier/Enabled/Captiv


**Firefox**
/usr/lib/firefox/firefox

---

### Post by snarkyCoder on 2015-11-11
> **vasa1 said:**
> Have you tried turning off hardware acceleration in your browser settings?

Just did. 
Same thing. :-?

---

### Post by CantankRus on 2015-11-11
By default, compiz redraws the contents of the window as you resize.
Try setting compiz only to draw the outline as you resize.
Via terminal....
```
dconf write /org/compiz/profiles/unity/plugins/resize/mode 1
```

To set back to default...
```
dconf reset /org/compiz/profiles/unity/plugins/resize/mode
```

---

### Post by snarkyCoder on 2015-11-11
> **CantankRus said:**
> By default, compiz redraws the contents of the window as you resize.
Try setting compiz only to draw the outline as you resize.
Via terminal....
```
dconf write /org/compiz/profiles/unity/plugins/resize/mode 1
```

To set back to default...
```
dconf reset /org/compiz/profiles/unity/plugins/resize/mode
```

Thanks man! This alternative fixed it! :)
Is this a bug just in this version of Ubuntu? Do you think that buy using a dedicated GPU this could go away?:confused:
Because re-sizing window inside a browser still causes the same CPU load...

But so far I am happy with this fix...
It should be included in the unity settings...:rolleyes:

---

### Post by snarkyCoder on 2015-11-11
> **grahammechanical said:**
> Do integrated video systems have active or passive cooling? Be glad the motherboard is responding to rises in temperature caused by increased activity.

I have no experience of integrated graphics but there may be a settings utility like the one that comes with the Nvidia driver that I am using. I can see how the GPU scales up and down its performance level depending on what is happening on the user interface. It also gives a temperature reading.

What we have in a browser window will also affect the amount of work the GPU has to do when we move a browser window. Some web sites have lots of images and even videos playing. Tabs that are open but not in the main window still have to be re-drawn even though they are out of our sight.

I have installed a utility called Psensor. That monitors all the fan speeds and temperatures of the CPU, GPU, motherboard and hard disks. We can set alarm levels. and we do not have to rely on our sense of hearing alone.

Regards.

Well yeah, but this problem even happened with only this thread opened.
I have Psensor too  I got an alarm at 50C that I set before just to test on a different issue.
and yeah ... it would hit the alarm pretty fast going from 30C to 50C in a couple of seconds haha

---

### Post by CantankRus on 2015-11-11
> **snarkyCoder said:**
> Thanks man! This alternative fixed it! :)
Is this a bug just in this version of Ubuntu? Do you think that buy using a dedicated GPU this could go away?:confused:
Because re-sizing window inside a browser still causes the same CPU load...

Maybe...maybe not. I have an nvidia GeForce GTX 550 Ti using the proprietary drivers and see laggy performance when using the
default resize mode.

 
You can also try adjusting the texture filter setting for speed...
```
dconf write /org/compiz/profiles/unity/plugins/opengl/texture-filter 0
```

To set back to default...
```
dconf reset /org/compiz/profiles/unity/plugins/opengl/texture-filter
```

You could also try a different desktop environment that uses a window manager other than compiz.
You will of course lose the benefits of the unity interface as it requires compiz.
```
sudo apt-get install gnome-session-flashback
```
Logout and choose the "GNOME Flashback (Metacity)" session.

---

### Post by snarkyCoder on 2015-11-11
> **CantankRus said:**
> 

You could also try a different desktop environment that uses a window manager other than compiz.
You will of course lose the benefits of the unity interface as it requires compiz.
```
sudo apt-get install gnome-session-flashback
```
Logout and choose the "GNOME Flashback (Metacity)" session.

Thanks! Now I am now using the Metacity desk environment and works great so far!

---

### Post by snarkyCoder on 2015-11-19
> **CantankRus said:**
> By default, compiz redraws the contents of the window as you resize.
Try setting compiz only to draw the outline as you resize.
Via terminal....
```
dconf write /org/compiz/profiles/unity/plugins/resize/mode 1
```

To set back to default...
```
dconf reset /org/compiz/profiles/unity/plugins/resize/mode
```

Hey I'm back :P

I tried to go back to the default with
```
dconf reset /org/compiz/profiles/unity/plugins/resize/mode
```

But it didn't go back to the default do you thinkg something is missing?

---

### Post by CantankRus on 2015-11-19
> **snarkyCoder said:**
> Hey I'm back :P

I tried to go back to the default with
```
dconf reset /org/compiz/profiles/unity/plugins/resize/mode
```

But it didn't go back to the default do you thinkg something is missing?
Are you still in the "GNOME Flashback (Metacity)" session?
If so, compiz settings don't apply as the window manager is Metacity.

---

### Post by snarkyCoder on 2015-11-19
> **CantankRus said:**
> Are you still in the "GNOME Flashback (Metacity)" session?
If so, compiz settings don't apply as the window manager is Metacity.

Thanks for replying man and your help!

See...I installed an external GPU so I went to unity again.
I wanted to test if with the new GPU things would change.
Also in gimp when doing the simplest thing, like changing color balance on a picture the CPU load would go up significantly and GPU stays the same temp

I would hope this could be better. I built this computer so I wouldn't use an old windows laptop with no gpu and i3 cpu. But that old laptop wouldn't do stuff like this...
So I suppose something is wrong with my configurations or something...

---

### Post by CantankRus on 2015-11-19
Are you sure you are now using the added GPU card?
No experience with integrated graphics.
Do you have an option to disable integrated graphics in the Bios?

Inxi (system info script) may help determine what's in use.
```
sudo apt-get install inxi
```

To display basic system info, run in terminal...
```
inxi -b
```

---

