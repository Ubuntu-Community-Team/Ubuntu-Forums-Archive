---
title: "Hang After New Login / Switch User"
date: 2006-12-11
forum: General Help
---

### Post by dshan on 2006-12-11
I've installed 6.10 (plus latest patches) on a Dell Inspiron 1300 with 1GB RAM and two logins (both admins). Everything is working fine, even wireless n/w. I can login as either user from a cold boot or restart just fine and all is well, however if I try to switch to the other user using either Applications>System Tools>New Login or System>Quit>Switch User when the new user's Gnome desktop appears after the login the whole system is hung - mouse pointer frozen, nothing responds. Ever. ctrl-c, even ctrl-alt-del does nothing, if I press the power button it brings up the Suspend/Hibernate/Restart/Shutdown screen but even that is frozen and unresponsive to mouse clicks or keyboard. I have to press and hold the power button again to force a shutdown and then reboot to get things going again. I've done this several times now and it seems very reproducable. 

Is this a known problem or does anyone have any idea what could be wrong?

---

### Post by Ashrael on 2006-12-11
ATI video?

---

### Post by PurplePenguin on 2006-12-11
The same thing happens to me... I've got a feeling it is related to the video driver (nvidia) that I'm using.  I changed the login theme back to the standard one (I had downloaded one from gnome-look a while ago), so we'll see if it helps out at all.  

Maybe you could let us know a bit more about your setup and see if we can draw some parallels?

---

### Post by PurplePenguin on 2006-12-11
After writing my post, I uninstalled my nvidia driver - now everything works perfectly!  Except, of course, my 3d games. ;)

---

### Post by dshan on 2006-12-12
Well PurplePenguin your comment about themes made me think, both of my users were set to the Clear Looks theme (and their desktop backgrounds to solid colours); I changed them both back to the default Human theme and desktop background, and the hangs stopped! Now user switching works fine. Wow, how weird is that? Damn, I changed them to Clear Looks 'cause I hate brown...

My Inspiron has Intel graphics - Mobile 915GM/GMS/910GML Express. Yes, I'm using the 915resolution module (1280 X 800).

Fixed, but not happy... :-(

---

### Post by Simon G Best on 2006-12-13
> **PurplePenguin said:**
> After writing my post, I uninstalled my nvidia driver - now everything works perfectly!  Except, of course, my 3d games. ;)

I have a similar problem, in that my system seems to hang almost completely when I log out (from X).  But I don't think it's to do with the graphics drivers (at least in my case).

When I log out, instead of returning to gdm's graphical login thingy, it just hangs.  Before I disabled ACPI (because of other problems), I could still shut the system down (and have it shut down properly) by pressing the power button on my PC (so it didn't seem to hang completely, just nearly completely).  But now, now that ACPI is disabled at boot time, I've ended up pressing the reset button - I hate doing that!

My graphics thingy is neither ATI nor nVidia, but an old SiS 6326 thingy.

---

