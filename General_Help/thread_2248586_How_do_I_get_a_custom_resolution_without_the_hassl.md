---
title: "How do I get a custom resolution without the hassle?"
date: 2014-10-15
forum: General Help
---

### Post by sbomb90 on 2014-10-15
Hello, 

Im not a complete linux beginner but im still a very casual user. (i usually avoid it if it doesnt use a GUI). 

I've had this problem for a while now and I know others have as well over the years. My external display is 1360x768. The only way to force ubuntu into the correct resolution is to run the following. 

> 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline "1360x768_60.00" 84.75 1360 1432 1568 1776 768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 1360x768_60.00
xrandr
cvt 1360 768
xrandr --newmode "1360x768_60.00" 84.75 1360 1432 1568 1776 768 771 781 798 -hsync +vsync
xrandr --addmode VGA1 1360x768_60.00


I actually figured out a way to run it at start up buy making a script for lightdm or something in "bin". Sorry i dont really remember the details as it was a while ago. The downside is now I HAVE to have it connected to the display. The native laptop screen no longer works because of whatever the script does. (thats fine as the battery is shot).

Unfortunately the computer is giving me internal error messages upon startup. The computer still works mostly but every once in a while the display quits and I have to hard reboot. If im watching a video or something the sound still plays but the computer is unresponsive. I imagine whatever the problem is is linked to the resolution issues. 

I was thinking of just reinstalling the OS. Its easy enough as I keep all my stuff backed up... But id like to find a better solution to this resolution issue before I go through the hassle. Why is it so complicated to get an OS to display at this res?

Any advice? Is there a distro (doesnt even have to be ubuntu) that handles this better?

---

