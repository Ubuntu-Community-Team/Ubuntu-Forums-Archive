---
title: "Random/spurious log-outs getting more frequent..."
date: 2013-05-25
forum: General Help
---

### Post by memilanuk on 2013-05-25
So... I have Xubuntu 13.04 installed on my Lenovo T530 laptop (~6 months old).  Everything seemed to be working fine, up until a couple days ago.  Then I suddenly got logged out when I went to click on some feature of the browser bar on the upper right corner of Firefox.  I thought maybe I had gotten sloppy and clicked on something I shouldn't have, or triggered some 'hot spot' in the window manager, and just sucked it up and logged back in.  A while later, I went to open a PDF... and got logged out again.

This was very odd, and had me scratching my head, but I couldn't find any correlation so I continued on.  Over the last few days there has been a handful of security updates, and the problems honestly seem to have gotten worse.  In the last hour, I got logged out probably 10 times, first when just clicking on something to open it - sometimes a PDF, sometimes a program from the application menu - always when trying to open the start-up and window manager sessions settings to try and not have so many programs opening up when I logged back in.  Finally it just got to the point where I could barely close out all the newly opened program windows, sit there for a few seconds... and then I would be logged out again and have to start all over.  

Right now the machine is powered off and stuffed in my backpack so I don't do something I'd regret to it.  I'm at a loss as to what the heck might have been causing this behavior - I'd fired up psensors and checked the temps... nothing above 43-44C (couldn't connect to the nvidia card though).   I was online connected via my cellphone thru a VPN when it started behaving more and more erratically....

Any ideas or suggestions?

Monte

---

### Post by 2F4U on 2013-05-25
Did you look into the log files? Can you provide some more information about your hardware, including graphics card and driver? Is that a fresh install or did you upgrade from a previous version? Such random problems could also be due to bad RAM. Therefore I would suggest that you run memtest, for example from a liveCD.

---

### Post by memilanuk on 2013-05-25
> **2F4U said:**
> Did you look into the log files? 

Not exactly feasible, with the system kicking me out in a couple minutes max towards the end of this mornings session.

> 
Can you provide some more information about your hardware, including graphics card and driver?


Lenovo ThinkPad T530, dual booting Win7Pro 64-bit & Xubuntu 13.04
Intel i5 3320M @ 2.6GHz
16GB DDR RAM (OEM/Samsung)
15" 1600x900 display
Intel HD 4000 (built-in)/ nVidia NVS 5400M w/ 1GB RAM
Crucial M4 256GB SSD (/, /home)
Toshiba 500GB SATA drive (/srv/data) mounted in drive caddy in optical bay


 > Is that a fresh install or did you upgrade from a previous version? 

Had been running Ubuntu 12.10, ran into a kernel bug shortly before 13.04 that affected the second video card.  Got that fixed; switched to openSUSE 12.3 for a short while, then did a fresh install of Xubuntu 13.04.  Was running just fine until recently... which included some kernel updates, which makes me a bit suspicious in that direction...  Win7 seems to still run fine and shows no issues.

> Such random problems could also be due to bad RAM. Therefore I would suggest that you run memtest, for example from a liveCD.

How likely is that, really, on a system that is relatively new (~6 months) and has been working fine up til now?  Woudn't the whole system be crashing, not just logging me out of XWindows?  I'll see if I can run a test later, but FWIW, when booted into Win7 (now) the vendor (Lenovo) hardware test programs show nothing wrong.

Thanks,

Monte

---

### Post by memilanuk on 2013-05-25
Well... spent the better part of an hour sitting through MemTest running thru umpteen tests on 16GB of RAM... nothing.  Booting into Xubuntu... same thing as before - I barely have time to close out the open application windows before getting kicked back out to the login screen.  Any attempt to logout in an orderly manner i.e. click on the logout button gets me dropped out with no confirmation, nothing.

Booting back into Windows 7 (where I'm typing this from)... no problems or anything out of the ordinary.

What the heck?!?

---

### Post by HiImTye on 2013-05-25
instead of logging in, hit ctrl+alt+f1 then log in there (to return to Uhuntu hit ctrl+alt+f7) then
```
cd /var/log; ll
```
to open a log file to view, use less
```
less syslog
less kern.log
```

---

### Post by memilanuk on 2013-05-25
Okay... any hints as to what I might be looking for?

---

### Post by memilanuk on 2013-05-26
Guess its *not* just my imagination:

[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1104435](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1104435)

Kind of curious how its going on three weeks with no fix... kind of a show-stopper.

---

### Post by fresnofred on 2013-06-24
I am running a desktop with ubuntu 11.04 and had the same problem with my pc- random logouts and keyboard problems.  i thought it was compiz or nvidea drivers but i was wrong.  I found the problem.  It was the optical mouse I was using.  I replaced it with a new optical mouse (and put it in a different usb port just to be safe, and my problems all went away.  Compiz works fine now, no spontaneous log outs and keyboard problems.  I suspect there was a conflict with the video driver and the mouse driver, which is also an optical, video device.

---

### Post by Dastardlydeed on 2013-08-10
Just experienced this bug myself. Very annoying, especially when in irc and looking (and getting) for anwsers (losing them in the process of kicking kicked back to the login screen.  :mad:

 Looks like there is an alleged fix on launchpad. Hopefully that will end this very intrusive bug. Will post again in a day or so. The previous post on the optical mouse is interesting since I use one as well. Will keep an eye on it.

---

### Post by pqwoerituytrueiwoq on 2013-08-10
sounds like this bug to me, i think the fix is out now, maybe it is still just in proposed
[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1104435](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1104435)

---

### Post by Dastardlydeed on 2013-08-13
Looks like the 4.10.1 update on launchpad did the trick. No spontaneous log outs in two days. Happy camper now!  \\:D/

---

