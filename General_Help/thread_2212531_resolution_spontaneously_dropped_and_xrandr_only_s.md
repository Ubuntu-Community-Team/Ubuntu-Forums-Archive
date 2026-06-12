---
title: "resolution spontaneously dropped and xrandr only shows one mode"
date: 2014-03-21
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-03-21
I have 2 nearly identical partitions of 13.10 built from the mini.iso up, with openbox as the de, on the same machine. One started as a clone of the other and hasn't evolved much beyond that yet.  The graphics card is an Nvidia GeForce 6600.  I haven't been able to get virtualbox to work on either recently, presumably an update broke it. That is a subject for another thread if it comes to that. I mention it here only because it's just barely possible it might have some bearing on the issue of immediate concern:

On one of the systems I tried purging and reinstalling virtualbox* and dkms. Everything seemed to be proceeding normally. I clicked a menu entry I have put on my openbox menu that normally starts firefox and then wmctrls the window size and placement. Instead of firefox coming up x seemed to shut down. Suddenly all I had was a black monitor with a cursor in the upper left corner. Not even a prompt, just the one "character" of the cursor that looks like an underline. It wouldn't respond to the keyboard or mouse at all. Cntrl-alt-F[1-7] keys didn't get any response. Nothing changed for several minutes so I pushed the shutdown button. If I recall correctly that worked normally, though I can't swear I didn't have to just cut power manually.  Anyway, when I booted into that system the resolution had changed to 640x480 by the time the login (lightdm) was up, which made that system almost impossible to use graphically since I've set the fonts fairly large. But I did manage to login to openbox typing blind so to speak.  With cntrl-t I got lxterminal up and managed to set its font size low enough to make it usable.  Using xrandr to to attempt to set the rez back to my
normal 1920x1080 it claimed that 640x480 was the only mode available. Using just plain "xrandr" which defaults to a query about what modes are supported also showed 640x480 as the only option. 
I tried reinstalling nvidia-current, which I think at the moment is 304. I tried nvidia-settings, a gui manager for setting up what you want an nvidia card to do, and it claimed something along the lines of "xserver not started" which didn't make any sense to me since I was USING a gui app, nvidia-settings itself. I'm sorry I'm a little vague about the exact error messages but the the combination of the low rez and my large fonts made that system extremely awkward to use.  I tried purging nvidia* and rebooting. I tried installing nvidia-319 and rebooting. I tried cold rebooting. The resolution resolutely refused to change and I resolved to reboot (hey, I didn't read Tom Swift for nuthin') into the other, nearly identical system to see if it was a hardware problem. I did. It isn't.

This is what xrandr gives me on the system which works normally:```
~$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 4096 x 4096
VGA-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 531mm x 298mm
   1920x1080      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
DVI-I-0 disconnected (normal left inverted right x axis y axis)
TV-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
```

This is all very puzzling to me. If I had thought of it, I would have avoided using wmctrl in this working system, for fear it might have somehow caused the problem. But I didn't think of it, so I started firefox the way I normally do, the way I did on the broken system just before the trouble began, with a menu entry pointing to a script that starts firefox and then beats it into line with wmctrl. This system still works normally, so wmctrl doesn't seem to be the culprit.

I'm contemplating looking for likely config files on this working system I can copy over their counterparts on the broken one. Or maybe I should purge and reinstall x. If that fails and nobody has a better idea, I'll have to restore from an fsarchiver backup, but I'll lose some tweaks I've made since I made the backup and I'm not sure I remember what they all were.

Any ideas on what might have caused this and how I might fix it short of the brute force methods I mentioned?

---

### Post by Dreamer Fithp Apprentice on 2014-03-24
Solved .
Answering rather than editing so it won't be in the unanswered list.
Impatience won out over caution.
I made this script with a short, memorable name, while running the working system:```
#!/bin/bash
sudo apt-get purge xorg* | tee -a ~/output.txt
sudo apt-get install xorg | tee -a ~/output.txt
/bin/bash
```,saved it in ~ on the broken system, and made it executable. Rebooted into the broken system, ran that script, reinstalled nvidia-current and dkms. Everything seems to work now and I can peruse the saved output file looking for things that might need to be reinstalled if I run into problem, but a quick scan suggests purging xorg* didn't take nearly as much with it as I feared it would. Anyone with a similar problem finding this - I'd recommend this solution - it didn't seem to break anything, which surprised me, and it worked.

---

