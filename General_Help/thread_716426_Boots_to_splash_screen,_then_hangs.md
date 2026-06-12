---
title: "Boots to splash screen, then hangs"
date: 2008-03-05
forum: General Help
---

### Post by benny_boy on 2008-03-05
I think this was the first time I rebooted after the last wine update came out, but not certain.  It froze for a bit on the splash screen with the progress bar about 1/3 complete then went to a blank screen with a blinking underscore at the top left corner, no error messages or anything.  I'm pretty new to ubuntu/linux, any help?

---

### Post by shotty on 2008-03-05
same here, except my loading bar doesnt even go that far, pretty sure that is irrelevent.
but i have tried booting from the cd, that doesnt work either. same effect

---

### Post by pointone on 2008-03-05
Are you able to boot into recovery mode?

---

### Post by benny_boy on 2008-03-05
Yes, it will boot in recovery mode.

and I have dual boot with XP btw.

---

### Post by benny_boy on 2008-03-06
I realized that the problem might have something to do with matlab (R2007a) that I just installed on XP.  So I uninstalled and ubuntu boots fine now.  I need it for school and the school only has the windows version available for free.  Any ideas on getting it to work with matlab installed on XP?

---

### Post by kesman on 2008-03-06
So you think some application in windows could cause Ubuntu not to boot? I really don't think so =D
Try editing your /boot/grub/menu.lst file to remove splash and quiet -parameters from the end of the line that boots ubuntu and then reboot your computer. This way you'll able to see what causes the crash during boot.

---

### Post by benny_boy on 2008-03-06
Yeah, not sure if it's related but i've booted sucessfully ~4 times since uninstalling it after about 10 failed attempts with it installed.  I'll do what you suggested, reinstall matlab and see if it fails again.

---

