---
title: "Updated Driver Now I get stuck on black screen please help 14.04"
date: 2015-11-26
forum: General Help
---

### Post by SirenSerena on 2015-11-26
I recieved this laptop from a coworker of my mother. He gave it to us since our laptop had been stolen so i have no previous knowledge with ubuntu or linux at all. At first I had issues with log in loop so i reinstalled ubuntu but now i tried to update my driver, since steam required it and rebooted but it will show bios, loading screen and that is it. Stops and stays at black screen. I am able to get to grub and have tried going to root prompt. Also i cant get to the log in. Sometimes i can use ctrl+alt+f1.

---

### Post by T.J. on 2015-12-01
It sounds like your driver or display manager is not configured properly. The display manager is the program that gives you a login screen. If you are using the AMD Catalyst driver - also known as FGLRX - it may be the source of the problem. AMD's drivers do not support the EGL graphics standard, even though they should.  They also tend to break if you get a bad update.

As a test, I would install the lightdm program to replace the display manager.  You will need to use ctrl+alt+F1 to get to a command prompt, login and then:

*sudo apt-get install lightdm *

Then make sure your setup is configured to use it: 

*sudo dpkg-reconfigure lightdm*. 

After that you should reboot, in order to test it.  Lightdm pretty much works with everything, others tend to be very sensitive to changes. GDM is known not to work at all. 

If that fixes it, great!  If not or if you get stuck, please post back to let me know.  There are some other things we can try.

---

