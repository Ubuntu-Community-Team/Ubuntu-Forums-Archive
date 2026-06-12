---
title: "System blacks out"
date: 2007-05-08
forum: General Help
---

### Post by fourthdimension on 2007-05-08
Hey All

I enabled desktop effects on fiesty and ever since then I can't log on.  I either get a black screen or a white screen, but nothing else happens.  I logged on through failsafe mode and it says the effects aren't enabled anymore, but the normal mode is still non-functional.  I'd appreciate any help anyone has.
Thanks a lot.


(I wasn't sure if this should go in the desktop effects section for the obvious reason or the general help because of the sys blackout...)

---

### Post by abc123456 on 2007-05-08
Had that happen when Ubuntu 6.06 removed my zsh on a dist-upgrade.  When I installed zsh from alt f2 then it worked again.  Hope this helps.:popcorn:

---

### Post by fourthdimension on 2007-05-09
Well, I didn't know how to install it from Alt+F2, so I installed it from the terminal and restarted.  The system only got as far as loading the  "foot-like icon in the brown rectangle" (I know, that sounds terribly noobish...) before the screen went black then white again.  That originally started the moment I clicked "enable desktop effects", but I checked for the fourth time now and they're still supposedly disabled.
Thanks for the quick response.

---

### Post by fourthdimension on 2007-05-10
Maybe there's a start-up script I can edit (since the system runs fine without the scripts in failsafe mode) to disable the effects on the startup...?

---

### Post by fourthdimension on 2007-05-19
Any help would be greatly appreciated...  I'm reluctant to reinstall my OS for the fourth time now since I have a relatively old hard drive.

All the best.

---

### Post by Cene on 2007-05-19
Look for any compiz and/or GLdesktop related stuff from ~/.config/autostart folder (ls ~/.config/autostart/). If there are any, delete or move them away from there.

Check also the ~/.xsession file for compiz/gldesktop entries (cat ~/.xsession).

---

### Post by Robbie Pence on 2007-08-19
> **fourthdimension said:**
> Any help would be greatly appreciated...  I'm reluctant to reinstall my OS for the fourth time now since I have a relatively old hard drive.

All the best.

It's pretty simple really.
Go to safemode(in GRUB menu...)
and it should let you log in.

From there, disable Desktop Effects, (same way you enabled it)
and restart to normal mode. 

Good to see you on here, 4-d. :)

---

