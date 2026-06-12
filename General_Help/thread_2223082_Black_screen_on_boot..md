---
title: "Black screen on boot."
date: 2014-05-09
forum: General Help
---

### Post by geraldbrent1 on 2014-05-09
I have been out of the Ubuntu scene for a while, and my Windows install (of course) is giving me issues. I made a backup image of my system, and am planning to format the drives and install Ubuntu to verify if the problems are hardware or software related. When I try to boot from a USB (14.04), it gives me a black screen. When it gets past the splash screens, I can hear the drums of the login screen, yet nothing ever shows up. If I move my finger on the trackpad, the pointer does appear, but will not allow me to click anything. If I switch to tty1, I get a terminal, and can type commands. I'm assuming this has something to do with lightdm, but I can't pinpoint the problem. I would like to be able to at least get a LiveCD running before I install the full OS. Any help would be greatly appreciated.

---

### Post by Bashing-om on 2014-05-09
geraldbrent1; Hi ! 

Let's say that when ubuntu loads that there is no graphics driver available to support the GUI. Fixable !
Try this:
Boot the liveCD;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s)space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line is now available, one may append "other" desired boot parameters to the end of the line that are not present in the "presets".
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.
Additional Drivers, location varies depending on the version, I have not seen 14.04 so can not say exactly where, maybe->
Left side of screen is the launcher ->ubuntu Software Center ->Software Sources(edit menu option on top task bar) ->Additional Drivers (tab in Software Sources) [must have 'net connectivity ]//assumes that 3rd party software sources have been enabled// .
From the Additional Drivers utility install the recommended driver.

If this works in the live environment we can make it work in the install !..

[INDENT]ain't nothing but a thing
[/INDENT]

---

### Post by jim_deadlock on 2014-05-09
Do you have dual monitors? I had a d'oh moment with a fresh install a while back - I kept getting a black screen on login with nothing but a mouse pointer, just as you describe, eventually to discover that my desktop was displayed on my other monitor which was swiched off :oops:

---

### Post by drac-noc on 2014-05-10
Sounds like a graphics chip issue.

I know Ubuntu/Unity loves to use 3D acceleration, and that can create problems. Try Xubuntu, and see if you have the same issues. If you can get to a normal Xubuntu desktop, you might fare better with installing and getting the desktop to work.

---

### Post by geraldbrent1 on 2014-05-12
> **Bashing-om said:**
> geraldbrent1; Hi ! 

Let's say that when ubuntu loads that there is no graphics driver available to support the GUI. Fixable !
Try this:
Boot the liveCD;
At the purple splash screen (stick figure keyboard emblems at bottom of screen) -> hit any key ->
Language screen -> escape key to accept the default ->
Booting options screen -> f6 key (other options) -> arrow down to the preset option(s)space or enter to accept and then the escape key to exit; 
Try "nomodeset" at this time; for other additions the boot options kernel boot line is now available, one may append "other" desired boot parameters to the end of the line that are not present in the "presets".
Enter key to continue the boot process to the GUI desk top; Degraded graphics is OK at this point.
Additional Drivers, location varies depending on the version, I have not seen 14.04 so can not say exactly where, maybe->
Left side of screen is the launcher ->ubuntu Software Center ->Software Sources(edit menu option on top task bar) ->Additional Drivers (tab in Software Sources) [must have 'net connectivity ]//assumes that 3rd party software sources have been enabled// .
From the Additional Drivers utility install the recommended driver.

If this works in the live environment we can make it work in the install !..
[INDENT]ain't nothing but a thing
[/INDENT]

Excellent! Works great! Finishing up the last part of the install now. It's going to be great to get some stability back on my machine. :)

---

### Post by Bashing-om on 2014-05-12
geraldbrent1; Great !

Pleased ya got it all sorted out.

[INDENT][INDENT]all in the care and feeding
[INDENT][INDENT][INDENT][INDENT]of your ubuntu
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

