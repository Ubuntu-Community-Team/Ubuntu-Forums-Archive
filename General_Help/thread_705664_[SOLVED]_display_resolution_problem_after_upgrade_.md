---
title: "[SOLVED] display resolution problem after upgrade to 7.10"
date: 2008-02-23
forum: General Help
---

### Post by mikepet on 2008-02-23
I just upgraded from ubuntu 7.04 to 7.10 and my display resolution is no longer correct.  The xorg.conf file is unchanged from the one I used with success on the previous several releases.  I looked in my xorg.conf file and found that Monitor section referenced an widescreen monitor that I used a while back, but no longer use.  The monitor that I've been using successfully with this xorg.conf file for the past two years is a Hitachi CM751.  I played around with various settings in xorg.conf (rebooting after each change), but nothing seems to change the resolution.  I'm attaching my old xorg.conf that used to work along with the latest version of the new xorg.conf based on my experiments.  Any idea what might be wrong?

---

### Post by gwoodruff on 2008-02-23
Are you saying the desktup will not keep a selected res, or the choice is not available to you? System/Preferences/Screen Resolution has a check box to default to selected. This will overide choices made in System/Administration/Screens and Graphics. Hope this helps

---

### Post by mikepet on 2008-02-23
Thanks for your response.  No matter whether I try to change the display settings with xorg.conf or with System/Administration/Screens and Graphics, it doesn't seem to have any effect.  Based on your suggestion, I also tried using the check box on the System/Preferences/Screen Resolution menu, but that also seems to have no effect.

When I use System/Administration/Screens and Graphics, I try various resolutions and refresh rates but the screen always looks the same (too wide, too short, and low brightness and contrast).  Nothing had changed with my setup other than the upgrade to 7.10 and everything had been working well thru previous upgrades without any changes to xorg.conf or System settings.

---

### Post by gwoodruff on 2008-02-24
I took a look at the conf files. Try System/Preferences/Screen Resolution  and set your monitor to 	"DELL 2001FP". Ijf that does not help post the new conf file that will be created.

---

### Post by mikepet on 2008-02-24
I'm not exactly sure what fixed the problem, but after trying several experiments with the System/Preferences/Screen Resolution settings, my resolution is back to normal now.  Thanks for pointing me to this menu.

---

