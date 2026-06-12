---
title: "Getting my Dual-head ATI 9700 to work with Ubuntu"
date: 2008-01-27
forum: General Help
---

### Post by Will Pittenger on 2008-01-27
I have a machine with a ATI 9700 with Gusty installed.  I am having problems getting the driver to work.  The secondary monitor is to the left of the primary.  One of the later invariably happens when I reboot after attempting to set the moniters the way I want them (Primary: 1680x1050 widescreen; Secondary: 1280x1024):[LIST=1]
[*]Layout is correct, but the primary displays at 1280x1024.  All panels stretch all the way from one side of the desktop to the other.  All centered windows appear right on the border between screens.  I figure that any maximized window will use the entire virtual desktop.  This is not happening anymore.
[*]Primary monitor's resolution is correct, but Secondary is disabled in Linux and clones the primary monitor.  This was the default when I installed Linux, but now with the ATI driver (which I installed from a download from their site) it is never selected.
[*]Primary monitor displays "DVI-D cannot display this mode."  Secondary shows left half of correct display size for that monitor, but at VGA resolution.  I have to scroll the screen to see much.  What would be on the main monitor doesn't display at all on either monitor.  This is now happening even when I use [FONT=Courier New]aticonfig[FONT=Tahoma] [FONT=Courier New]--intial=dual-head -f -v[/FONT] to reset the config file.[/FONT][/FONT]
[*]Same as #3, but the primary shows garbage at what looks like VGA resolution.  (Definitely not a widescreen layout.)
[*]Ubuntu comes up in "Low resolution mode" with the secondary turned completely off.[/LIST]I have tried using [FONT=Courier New]aticonfig[FONT=Tahoma] [FONT=Courier New]--intial=dual-head -f -v [FONT=Tahoma]in the recovery mode during boot.  That is now resulting in #3, #4, or #5 after I reboot.  Any suggestions?

BTW: the layout I mentioned works just fine under Windows XP SP1 at the same resolutions and monitors.
 [/FONT][/FONT][/FONT][/FONT]

---

