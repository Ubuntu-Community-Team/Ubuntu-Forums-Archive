---
title: "[SOLVED] Keyboard Layout Settings won't stick after reboot"
date: 2008-05-30
forum: General Help
---

### Post by Thanh-BKK on 2008-05-30
Hello :)

Here's my first problem with Hardy on this machine - and a weird one. 

Testerday for the first time i took care of getting my boyfriend to use Linux - well, test Linux on my machine, so i installed the Thai keyboard for him. Thai fonts was no problem, already installed, just the Thai keyboard and possibility to switch between Thai and English.

It worked fine.

However, after a reboot, it does NOT work anymore. The indicator is still there in the panel, but the alt+shift, like i set it to switch layouts, does nothing, and clicking the layout thingy in the panel makes it change from "USA' to "THA" but it still types in English only. 

I checked in the preferences and it is all still like i set it yesterday, it just doesn't work anymore. 

If i "remove" the Thai keyboard and then "add" it again, it works again, incl. the alt+shift for switching..... how can i make this stick?

I appreciate any replies on this matter.... thank you very much :)

Best regards.....

Thanh

---

### Post by Thanh-BKK on 2008-05-31
*bump*

Anyone? There must be more users out there who are bilingual and require two different inputs..?

Regards....

Thanh

---

### Post by prshah on 2008-05-31
> **Thanh-BKK said:**
>  so i installed the Thai keyboard for him. Thai fonts was no problem, already installed, just the Thai keyboard and possibility to switch between Thai and English.

It worked fine. However, after a reboot, it does NOT work anymore. 

Faced the same problem; it's a known bug. You can fix it by adding "setxkbmap" to your gnome startup (sessions), as follows:

Click System-Preferences-Sessions-Startup Programs-Add: 

Name: setxkbmap (or whatever you like)
Command: setxkbmap
Comment: Set Keyboard Layouts (or whatever you like)

Then click OK, Close and restart to check if it works!

---

### Post by SyL on 2008-05-31
had the same issue too, just run **setxkbmap **do the job!

---

### Post by Thanh-BKK on 2008-05-31
Good morning :)

Thank you both very much!! I didn't know of the existence of this program - i mean, just typing "setxkbmap" into a terminal is SO much faster than removing and re-adding the keyboard layout via GUI :)

So i have no done the advised, i added it to the startup programs, and will see upon next reboot what it does :)

With kind regards.....

Thanh

---

### Post by prshah on 2008-06-01
> **Thanh-BKK said:**
> 
So i have no done the advised, i added it to the startup programs, and will see upon next reboot what it does :)


If it works (and it will!) please mark this thread solved. Near the top righthand side of the page, click on "Thread Tools"-"Mark Thread as Solved"

---

### Post by Thanh-BKK on 2008-06-01
Hi :)

And so i have done, again, as indeed it does work. Normally i would only shut down my machine in about two hours from now and start again tomorrow morning, but i just HAD to test this - yup, problem indeed solved :)

Everyone involved a big "thank you" from me :)

Kind regards.....

Thanh

---

