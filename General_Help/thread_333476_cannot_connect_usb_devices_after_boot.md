---
title: "cannot connect usb devices after boot"
date: 2007-01-07
forum: General Help
---

### Post by fugative on 2007-01-07
:confused: my ubuntu box has developed a little problem... I cannot connect usb devices after it has booted. what ever is attached when i start up (ipod, flash drive voip phone etc) works fine but if i try to plug in any of these after the machine is up and running it doesn't mount them. this is new and i have probably done an update recently, i have set up an ad-hoc network with internet share but that's it.

any ideas:-k

---

### Post by tzulberti on 2007-01-07
You should check your configuration in Desktop, Preferences, Removable Drives and Media...

---

### Post by fugative on 2007-01-08
Yeah,  i tried there but everything seems to be in order. Got to be something deeper in the system.  It's like the usb ports power down as is I eject a device then plug it back in it doesn't even light up.

Thanks for the suggestion anyway....anything else.

---

### Post by dcstar on 2007-01-09
> **fugative said:**
> :confused: my ubuntu box has developed a little problem... I cannot connect usb devices after it has booted. what ever is attached when i start up (ipod, flash drive voip phone etc) works fine but if i try to plug in any of these after the machine is up and running it doesn't mount them. this is new and i have probably done an update recently, i have set up an ad-hoc network with internet share but that's it.

any ideas:-k

Check if you have the Splash option un-ticked in System-Preferences-Sessions (if so, put it back), and also check if the gnome-volume-manager process is loaded.

---

### Post by fugative on 2007-01-09
That did it, thanks dcstar. I had a line in the session start-up which said "gnome- volume-manager --sm-disable" i diabled this and all's well. I spose i can delete it from the session start-up but what do you think could have put it there?

thanks again it's the simple things that are the most annoying.

---

### Post by dcstar on 2007-01-09
> **fugative said:**
> That did it, thanks dcstar. I had a line in the session start-up which said "gnome- volume-manager --sm-disable" i diabled this and all's well. I spose i can delete it from the session start-up but what do you think could have put it there?

thanks again it's the simple things that are the most annoying.

I have a similar weird bug in my system, but it only arises when I de-select the Splash screen on startup.

BTW, I still have "gnome- volume-manager --sm-disable" in my system and my stuff still works, but it may be related in some screwy way.

There is some bug in Gnome that only affects a few of us, hopefully someone (at sometime) will figure it out.

---

