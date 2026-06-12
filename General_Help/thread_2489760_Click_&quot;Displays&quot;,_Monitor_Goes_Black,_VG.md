---
title: "Click &quot;Displays&quot;, Monitor Goes Black, VGA to HDMI, Display across two monitors"
date: 2023-08-09
forum: General Help
---

### Post by webmanoffesto on 2023-08-09
I have an old System76 Meerkat wich has a VGA output, and runs Ubuntu recent stable. 

I'm trying to send that output to two monitors which have HDMI input. 

I want the two monitors to act as one monitor, like I can drag a window off one monitor and onto the other.

I have managed to send the same exact output to the two monitors at the same time, and it displayed fine.

But then I wanted to define them as one monitor so I went to "settings / displays". When I went clicked on "Displays" the monitors both went blank. Please help me resolve this problem.



Details:

Out of computer - VGA to HDMI adapter
HDMI splitter: 1 in and 2 out
Goes to one computer monitor and one Visio TV.
This is used mainly to display a Feh slideshow. 
The other monitor could be used for regular computing.

---

### Post by TheFu on 2023-08-09
How many video outputs does the laptop have?  
Does the GPU support driving 2 external monitors?

The GPU and drivers for it will be the main aspect of what's necessary.
Just because the plugs fit, that doesn't mean the GPU can drive them separately with different outputs.  With nvidia GPUs, 
[https://help.ubuntu.com/stable/ubuntu-help/display-dual-monitors.html](https://help.ubuntu.com/stable/ubuntu-help/display-dual-monitors.html) is the 22.04 guide for setting up 2 monitors.

I have no idea if Wayland supports this stuff or not.  I use X11 and was forced to switch from VGA to HDMI a few years ago. Actually, one of my monitors doesn't support HDMI input - it has VGA and DVI-D and Display Port connections, but no HDMI.

---

### Post by MAFoElffen on 2023-08-09
LOL. Which version of System76 Meerkat? I think they started selling them in 2015... and are still selling that Meerkat model. But now they have a number after the name.

If you can get a display working, Please run the [Ubuntu 'system-info' script]("https://github.com/UbuntuForums/system-info") so we can look at the hardware to see what it can support and so we can come up with ideas for you. Select upload to pastebin, and post the URL of where it uploads the report to.

---

