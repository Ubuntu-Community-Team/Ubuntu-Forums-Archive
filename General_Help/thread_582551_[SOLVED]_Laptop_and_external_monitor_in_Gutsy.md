---
title: "[SOLVED] Laptop and external monitor in Gutsy"
date: 2007-10-20
forum: General Help
---

### Post by Nicolas Pham-Dinh on 2007-10-20
I have an Aspire 3680 laptop (internal display 1280 x 800) and external display Acer AL2216W (1680 x 1050). Since I upgraded to Gutsy, whenever I work on the external display, the windows keep re-sizing while I work and this is driving me nuts. It is behaving as if there were two super-imposed resolution and keeps maximizing to the top right region coinciding to the resolution of the internal display. Any help would be greatly appreciated. Thanks in advance.

---

### Post by daengbo on 2007-10-20
Since this is an upgrade, I'm going to assume you customized your xorg.conf file before. Is this right? If so, have you tried using the graphical utility provided by Gutsy?

Back up your current xorg.conf:
$ mkdir Backups
$ cp /etc/X11/xorg.conf backups

Start the graphical utitlity in
System -> Administration -> Screens and Graphics

Make sure your driver is correct, choose the correct monitors, and choose resolutions for both the LCD and external monitor.

Restart X with CTRL-ALT-BKSP

See if that solves your problem.

Good luck

Daeng Bo
[http://ibeentoubuntu.blogspot.com](http://ibeentoubuntu.blogspot.com)

---

### Post by Nicolas Pham-Dinh on 2007-10-20
No luck with this. Thank you for trying.

---

### Post by zacinaction on 2007-10-22
I'm having the same problem with my laptop and external display - Internal Display is 1280x768 and external is 1440x900.  When I'm using the external display and I maximize a window, it maximizes to the size it would have on the 1280x768 monitor in the upper left corner of the screen.  This is on a clean install of Gutsy.  I've also played with the xorg.conf file a little bit by hand to no avail.

---

### Post by kbracer on 2007-10-22
I am experiencing the same behavior with a clean install of Gutsy. Maximized windows on the external 1680x1050 monitor resize themselves to the 1024x768 resolution of the laptop. No amount of fiddling with "Screens and Graphics" has produced a solution. In fact, I've had little success in getting any kind of predictable behavior out of "Screens and Graphics" in regards to running the laptop with an external monitor.

Intel 855, 1024x768 laptop LCD, 1680x1050 external Samsung 226BW

---

### Post by Laen on 2007-10-22
Experiencing the same problem. Looks like external monitor issues will never end with Linux. I don't expect a fix for this one. :(

---

### Post by Nicolas Pham-Dinh on 2007-10-22
I have no clue what happened but this morning I was experimenting with editing xorg.conf and got into trouble again so I reset it once more for probably the 15th time in four days (sudo dpkg-reconfigure -phigh xserver-xorg) and rebooted. Surprise! The problem is gone after four days of struggling. Would it be that a fix has been made to the xserver? Hopefully, but I don't know much about how this works. The only thing I know is that I am a happy camper now. Long live Unbuntu!

---

### Post by buntunub on 2007-10-22
:popcorn:

Umpteenth post now about this ever persistent issue with the borked xorg's in Gutsy! Congratz! Fix now please! Right now, unless your on Nvidia and use the nvidia-settings utility, forget about dual screens. Even then, its VERY VERY buggy, and ...........still............. issues with random frequent lockups on the xserver whenever running Compiz. This is an ever persistent issue carried over from Feisty that also never got fixed!

---

### Post by Nicolas Pham-Dinh on 2007-10-22
Here's another thing: I found that turning off the visual effects in the appearance menu solves the problem. But you don't get visual effects...

---

### Post by kkinder on 2007-10-23
Same problem here. Along with the fact that I can't type this very message in firefox, because as of "upgrading" to gutsy, it crashes at random. Ubuntu hasn't been usable since Breezy.

---

### Post by NawaMan on 2007-10-23
I have the same problem and I think someone has posted that before. Unfortunately there seems to be no solution or work around.

From what I recalled (some reading those posts), it seems that the problem is Compiz-Fusion no X. I, too, found that the problem disappear if you disable Compiz. But since can't live with Compiz (actually I like Beryl much better). I seems that Compiz has pick up a wrong resolution.

If this is useful for the debugger, here is experience of the problem:
I use external monitor with my laptop. The laptop resolution is 1280x800 and the external monitor is 1680x1050. They work in the cloning mode. The problem occur when I maximize a windows. If the close button is within 1280x800, the windows will expand to 1280x800. If the close button is within 1680x1050, the windows will expand to 1680x1050 but when I click on it, it change to fit 1280x800. When I toggle to full screen (totem), it only fit 1280x800. If I zoom while in 1280x800, I will only zoom the inside 1280x800 but if I zoom outside this, it will just zoom only outside. When I do something that need my password or when I want to exit (restart or shutdown), the 1280x800 part of the screen become dark the rest is still the same brightness but weirdly the password/restart box is right in the center of 1680x1050 screen :S. All of these problems disappear when I switch back to Metacity instead of Compiz. But I can't live without it now. :'( I am using Intel Expression 945GM card on SonyVAIO DuoCore 1GB RAM

NawaMan

---

### Post by Bakey on 2007-10-26
I can also confirm these same problems on a fresh Gutsy install on a Dell Latitude D820 with the intel graphics.  Internal display resolution 1280x800, external display resolution 1280x1024.  Turning off the effects also fixed the problem for me, but I don't get any pretty eye-candy now! :(  Has anyone submitted a bug report about this?

*EDIT*

Thanks Tuba...is this your bug report?
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/154453/](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/154453/)

---

### Post by TubaTodd on 2007-10-26
I submitted a bug report last week about this. I'm not sure that it is actually an Ubuntu specific problem. I experienced the same thing running Fedora 8 Test 3.

---

### Post by Bakey on 2007-10-26
Here's TubaTodd's bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/154453](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/154453)

If you're having similar behavior, please add a commend here and subscribe to the bug so that we can get this fixed.

---

### Post by Vaan on 2007-10-26
Ugh this is driving me nuts. I upgrade today from Feisty and I literally had to spend all day trying to figure out this problem.

My internal resolution is 1280x800 and my external is 1600x1200. I've reconfigured xserver-xorg many times, messed around with the new Screens and Graphics config and still get this "superimposed" issue.

On Feisty my external monitor was the main display and my internal notebook monitor was just turned off. Now they're both turned on and not displaying properly. Sorta driving me nuts here. I can't seem to disable my internal notebook display and get just my external Dell monitor to run like I had it in Feisty.

Oh and I forgot to mention, disabling Desktop Effects does not solve this issue.

=(

**Update**

Check this thread out: [http://ubuntuforums.org/showthread.php?t=593097](http://ubuntuforums.org/showthread.php?t=593097)

---

### Post by ariel on 2007-10-29
Same problem here... on a dell latitude D820 / Intel, with and external monitor of 1440x900... hopefully we will find some sort of workaround before the next ubuntu release...

---

### Post by Nicolas Pham-Dinh on 2007-11-04
Problem finally solved. Here's how to: 

- Install Compiz Advanced Desktop Setting;
- Open it and go to "General Options", then "Display Settings"; 
- Uncheck "Detect Outputs";
- In "Ouputs", edit the resolution (mine was set at 800x600x0x0) to your external display's resolution (mine is now 1050x1680). 

This should solve the problem.

---

### Post by Nicolas Pham-Dinh on 2007-11-04
h

---

### Post by abh83 on 2007-11-04
Sorry i didn't read the whole thread. But for those with nvidia cards: I had a similar issue with my acer 5630 (1280x800) and my 1680x1050 LG monitor. However, i installed nvida settings from the synaptic package manager.

Then to launch it type the following into the terminal:

~$ ```
sudo nvidia-settings
```

hope this helps!

---

### Post by Nicolas Pham-Dinh on 2007-11-04
Problem solved. Here's how to:

- Install Compiz Advanced Desktop Setting;
- Open it and go to "General Options", then "Display Settings";
- Uncheck "Detect Outputs";
- In "Ouputs", edit the resolution (mine was set at 800x600x0x0) to your external display's resolution (mine is now 1050x1680).

This should solve the problem.

---

### Post by Cringeworthy on 2007-11-07
Same problem here with both Ubuntu and Kubuntu gutsy.  As described above, maximised windows on the external monitor occupy only part of the screen at the top left.  The part they occupy corresponds to the (lower) resolution of the laptop.  Maddening.  Kubuntu does not come with Compiz so turning it off is not an option.

It worked fine under Feisty, but no amount of tweaking will make it work under Gutsy.  This is so frustrating.  After 40 hours of troubleshooting, I went back to Feisty.

 Laptop is Compaq n600c, resolution 1024 x 758.  External monitor is HP w2007v, resolution 1680x1050.

---

### Post by fguillen on 2008-02-03
Same problem internal monitor 1280x800 external 1680x1050.

---

### Post by fguillen on 2008-02-03
I have the problem on mi external monitor 1680x1050: the image is not centered.

I have not actived any graphic effects.

---

### Post by kenosando on 2008-02-24
i also have an external display (1440x900). I am able to get fullscreen on all windows, but the process is somewhat weird. I first minimize the window(s) (or show the desktop if you prefer) and restore the windows NOTE: I am running 7.10 - Gutsy Gibbon with a Gateway on Intel chipset. The windows will be fullscreen for me after that. However, after I would click on the window, it would revert back to the semi-fullscreen as before. I then went into System-->Prefs-->Advanced Desktop-->General-->Focus and Raise and unchecked "Raise to Click" and checked "Auto-raise" --- obviously not the fix to the bug, but for presentations on a external display such as projector, this is a way around for those that can get this to work for you.

---

