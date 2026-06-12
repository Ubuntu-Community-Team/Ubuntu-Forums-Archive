---
title: "Login Screen Off Center"
date: 2007-05-13
forum: General Help
---

### Post by Jackie_Treehorn on 2007-05-13
Hello everyone.

First, I'd like to say hello.  I'm new to Linux.  I am trying a brand new install on my home built rig.

It's an AMD machine.  Nvidia GeForce 5900 vid card.

I have XP loaded on my main SATA disk.  I have two other IDE disks.  One for backup and one were I've installed a fresh copy of Ubuntu - latest version.  Everything is working great!  I really love Ubuntu.

I have two video related problems.  First, let me say that I do have the Nvidia graphics drivers loaded and I believe them to be working.  I can get the Nvidia control panel by typing 'nvidia-settings' in terminal.

Problems:

1.  My login screen is about two inches left of center on my screen.  I'll assume it's because the nvidia drivers are not yet installed at that point.  Not really a huge problem, but a minor annoyance that I'd like to correct.  Is there a way?

2.  My resolution settings don't seem to 'stick' when I restart my machine.  Meaning, if I select my preferred monitor resolution, 1152x864, in the nvidia control panel, then restart the machine, the resolution reverts back to 1024x768.  What am I doing wrong here.

I'm sure this will be my first of many posts here.  I look forward to learning much from these forums.

Take care everyone, and thank you very much for your time and your help.

Jackie

---

### Post by Wim Sturkenboom on 2007-05-14
Your driver is already loaded when the login screen appears. On my box, I see a nVidia splash screen before the login screen appears; this indicates that the driver is loaded. I can't tell you what gos wrong in your situation.

With regards to the resolution, you can check the file /etc/X11/xorg.conf.
- Go to the section *screen* and determine the defaultdepth (e.g. 24).
- Next locate the subsection *display* that has the same depth.
- Add your preferred resolution as the first resolution (as marked in red below)
```
**Section "Screen"**
Identifier "Screen0"
Device     "Card0"
Monitor    "Monitor0"
**DefaultDepth 24**
SubSection "Display"
Viewport   0 0
Depth     1
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     4
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     8
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     15
EndSubSection
SubSection "Display"
Viewport   0 0
Depth     16
EndSubSection
SubSection "Display"
Viewport   0 0
**Depth     24**
modes     **[COLOR="Red"]"1280x960[/COLOR]**" "1024x768"
EndSubSection
EndSection

```
Please make a backup first of the file so you can revert back to the original if you make a mistake

PS you need root privileges to edit the file.

---

### Post by hartz on 2007-05-14
When you see the login screen shown "off-center" it is usually in the center of the Desktop, which is different from the center of the "Monitor".

Check that your desktop size and monitor resolution is set the same.

Unless you want this effect.  I usually enable a larger desktop on low-res monitors.  If you move the mouse around to the edges of the screen you should see that the desktop scrolls around, bringing into view the strips along the side which is off the monitor.

I've seen this happen when you plug in a monitor which is not capable of displaying any desktop size that you have in your xorg.conf.  For example when I go lugging my PC arround, I usualy don't take my 19" 1600x1200 monitor, but rather take a lowly 1280xsomething LCD panel which is more portable.

---

### Post by Derspankster on 2007-10-19
I have the same issue with my splash screen and my xorg.conf is fine. My screen resolution also matches my preferred xorg resolution. Something happened somewhere along the line to cause this but have no clue what.  It doesn't really bother me but I've wondered why it's doing that. My login screen is fine.

---

