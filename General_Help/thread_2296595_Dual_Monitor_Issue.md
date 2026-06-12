---
title: "Dual Monitor Issue"
date: 2015-09-27
forum: General Help
---

### Post by Dylan_Morshead on 2015-09-27
With Lubuntu, I've been having a problem with my second monitor.

I've tried activating it with xrandr.. It seems to change my settings, but my second monitor doesn't turn on.

Second monitor works default with ubuntu.

It only happens in XUBUNTU, LUBUNTU, LINUX MINT, KUBUNTU

but not ubuntu, fedora.

Been searching forever working out this issue.

---

### Post by Bucky Ball on 2015-09-27
I find arandr easier and have had better results than trying to tweak setting with xrandr. Install from Synaptics and launch. You should see your connected monitors. Right click on one and adjust.

You may need to untweak whatever you've tweaked in any files first, though.

---

### Post by Dylan_Morshead on 2015-09-27
I can't seem get get either to work... odd.

both monitors are connected, and it seems to "extend" but only one monitor is actually on, the other is still on sleep. for some reason. turn it off and on doesn't do anything.

---

### Post by Bucky Ball on 2015-09-27
Once you have arandr installed from Synaptic, open a terminal and type:

```
arandr
```

What happens? Report any errors in the terminal or anything else, even if it's nothing.

---

### Post by Dylan_Morshead on 2015-09-27
Sure.

dylan@dylan-pc:~$ sudo arandr
[sudo] password for dylan: 
/usr/share/themes/Lubuntu-default/gtk-2.0/apps/thunar.rc:55: error: invalid string constant "thunar-statusbar", expected valid string constant

Seems to apply, but the second screen won't turn on at all.

Screen 0: minimum 8 x 8, current 1280 x 1024, maximum 32767 x 32767
DVI1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   76.0     75.0     72.0     70.0  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 380mm x 300mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        75.0     72.8     60.0  
   720x400        70.1  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

---

### Post by Bucky Ball on 2015-09-27
No sudo. Just 'arandr'. You do not want to run this as root. Not advisable. And if you are running a GUI as root you use 'gksudo', not 'sudo'. 

Again, please. No sudo.

---

### Post by Dylan_Morshead on 2015-09-28
If i don't use sudo, there isn't any errors or anything.

---

### Post by Bucky Ball on 2015-09-28
> **Dylan_Morshead said:**
> If i don't use sudo, there isn't any errors or anything.

As it should be. You issue 'arandr' and arandr appears ok? No errors in the terminal while using it (we are looking for errors that pop up in the terminal while using, not necessarily while launching). Now you just can't use it to get your desired resolution?

---

### Post by Dylan_Morshead on 2015-09-28
everything works fine, as it should. but the problem is

it seems that gnome detects and enables the screen(ubuntu, fedora), while lubuntu doesn't detect nor turn the screen on boot. so I'm left with a screen thats off no matter what I do, sorry if its confusing to explain.

---

### Post by Bucky Ball on 2015-09-28
All good and I get it now. In that case, I'd say there is some software in the other two that is not in Lubuntu regarding screens and graphics. Lubuntu uses the lxde desktop environment. I don't know much about it but I think it uses ldm or gdm as its desktop manager. The other two, I think, use lightdm. Check what you have installed using Synaptics.

It may be that changing to lightdm will help, but that is a guess. There are definitely differences between Lubuntu and the more resource hungry flavours. Your issue could relate to the removal of something from Lubuntu to make it lighter, not by you, but intentionally by the devs.

Have you done a search for 'no dual monitor lubuntu'? Might drag up some clues and tell us the differences. May be a well known issue. :-k

---

### Post by Dylan_Morshead on 2015-10-01
Alright, I'll check that out and let you know how that goes, sorry for the late reply.

---

### Post by Dylan_Morshead on 2015-10-06
hmm, it seems like lubuntu already has lightdm.

---

### Post by Dylan_Morshead on 2015-10-11
bump

---

### Post by Dylan_Morshead on 2015-10-14
Okay, Oddly enough it was just the window manager.

I switched to GDM, and it does the job, interesting.

If anyone has this problem, use GDM, it will fix it.

Thanks for the help.

---

### Post by Bucky Ball on 2015-10-14
Nicely nutted out. :)

Please see the first link in my signature to help others. Good luck.

---

### Post by mos182 on 2016-01-20
Also had issues similar to [COLOR=#000000]OP. I'm currently using Xubuntu. The work around I've been doing is to change the resolution of the second monitor in ARandR. My second monitor was "active" and only started working once I started lowering the resolution a couple of times.

I'm currently now installing gdm, fingers crossed it'll fix my problems permanently![/COLOR]

---

