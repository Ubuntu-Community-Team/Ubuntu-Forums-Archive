---
title: "sudden screen resolution problems..."
date: 2006-12-15
forum: General Help
---

### Post by weird_c00kie on 2006-12-15
once again, ubuntu went off and did strange things on its own.
i put it on standby yesterday before i went to work and it was all fine. when i got back, i turned the computer on and it crashed while trying to get out of hibernation mode as it sometimes does. when i restarted, after ubuntu went through its loading process, it took me to the login screen. problem was, instead of my usual 1280 x 1024 resolution, it was in 640 x 480. i logged in and went straight to Preferences > Screen Resolution to fix it and discovered something weird...

all of a sudden, 640 x 480 at 60Hz is the *only* resolution i can set screen to now.
the only thing i could think of was to reinstall my nvidia drivers, which i did, but it didn't do anything. does anyone have any ideas?

i'm running 64-bit dapper, by the way

---

### Post by weird_c00kie on 2006-12-15
i just logged into my XP installation to make sure it isn't a problem with my graphics card or monitor and it worked fine, so i guess it has to be a software issue within ubuntu

---

### Post by weird_c00kie on 2006-12-16
no one? anyone?

---

### Post by weird_c00kie on 2006-12-16
i think it was a problem with the nvidia drivers...

i used 
> sudo dpkg-reconfigure xserver-xorg
and set it to use "nv" instead of "nvidia" and i'm back to 1280 x 1024 again, though 60Hz is still the only option it gives me, whereas before i had up to 75Hz available to me.
strange....

*edit*

okay, i take that back. i don't know what the problem was. i did it again, this time setting it to use the "nvidia" drivers and it still works.
now i just need to figure out how to make the other refresh rates available again...

---

### Post by weird_c00kie on 2006-12-16
well this concludes my monologue. i edited the xorg file with
> sudo gedit /etc/X11/xorg.conf
and entered my monitor's vertical and horizontal sync rates that i found on the internet and boom! i'm running back on 75Hz now :D

by the way, this thread helped:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

:D

---

### Post by rooster78383 on 2007-01-01
Thanks for the information. I had the same exact problem after an upgrade. A simple reconfig resolved the problem.

Also appreciate the imbedded link which helped a lot.

rooster

---

