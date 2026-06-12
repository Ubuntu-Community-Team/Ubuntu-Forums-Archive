---
title: "Files only appear on the desktop under certain circumstances"
date: 2013-05-06
forum: General Help
---

### Post by kornfan71 on 2013-05-06
Hello all,

I've been having a rather annoying issue with my Ubuntu 13.04 install. (As a note, I have already reinstalled 13.04 on this system due to other issues. The same problem existed on the other installation.)

Basically, files only show up on my desktop if they were created by right clicking on my desktop, and doing "New Document > Empty Document".
Creating them by using a "standalone" Nautilus window at ~/Desktop does not work. "touch ~/Desktop/file" does not show cause "file" to appear on my desktop, but it will appear in the ~/Desktop directory in a Nautilus window and in a terminal.

I'm at a total loss as to what's going on. 

Does anyone have any suggestions?

---

### Post by dino99 on 2013-05-06
that is "handle the desktop" feature, which is off by default. Can be tweaked with gnome-tweak-tool

---

### Post by kornfan71 on 2013-05-06
Thanks for the reply dino.
I grabbed gnome-tweak-tool, and the "handle the desktop" feature was already on. I toggled it off then back on, tried to put things in ~/Desktop, and still nothing showed up...:-?

---

### Post by CatKiller on 2013-05-06
I don't know how it might have happened, nor how to fix it, but it'd possible that the files are being displayed on the Desktop, just outside the viewable area in some fashion.

---

### Post by kornfan71 on 2013-05-06
> **CatKiller said:**
> I don't know how it might have happened, nor how to fix it, but it'd possible that the files are being displayed on the Desktop, just outside the viewable area in some fashion.

CatKiller, it looks like you're right.
Here's a look at my display setup. This is probably why it's happening:
[ATTACH=CONFIG]242271[/ATTACH] 
[SIZE=1](Click to enlarge)[/SIZE]

If I set it back to "Mirror Displays," the desktop icons show up fine.

This is the relevent output of "xrandr --current"

```

HDMI1 connected 1920x1080+0+446 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080      60.0*+   50.0     60.0  
   1920x1080i     25.0     30.0  
   1600x1200      60.0  
   1680x1050      59.9  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1366x768       59.8  
   1152x864       75.0  
   1280x720       50.0     60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  

HDMI2 connected 1080x1920+1920+0 right (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080      60.0*+   50.0     60.0  
   1920x1080i     25.0     30.0  
   1600x1200      60.0  
   1680x1050      59.9  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1366x768       59.8  
   1152x864       75.0  
   1280x720       50.0     60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   720x576        50.0  
   720x480        59.9  
   640x480        72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  


```

If I do "[FONT=courier new]xrandr --output HDMI1 --pos 0x0[/FONT]", the desktop icons are displayed. However, to get everything to line up, I need to run "[FONT=courier new]xrandr --output HDMI2 --pos 1920x-440[/FONT]". Unfortunately, the -440 *actually* sets HDMI1's position to 0x440, and HDMI2's position to 1920x0, resulting in the desktop icons being off-screen.

I'm not quite sure where to go from here.

---

