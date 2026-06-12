---
title: "Broken mouse icon"
date: 2006-10-16
forum: General Help
---

### Post by madcow72 on 2006-10-16
A silly problem that I would love to fix...  I just configured my system for dual-head using ```
aticonfig --initial=dual-head
```
and then adjusted my xorg.conf to use xinerama for big-desktop.  Everything works great after an X-server restart, but when my mouse is on the 2nd monitor, the icon turns into a large block that somewhat resembles an iconic screenshot of what monitor 1 looks like. (If that makes any sense.  If it doesn't, then just stick to the description - "mouse icon looks like a large square on 2nd monitor.")

Any ideas how to fix that?  Is it just something screwy with my xorg.conf file?

Cheers!

---

### Post by adarof on 2006-11-01
I confirm this problem.

Adding 
Option      "SWCursor"    "true"
to the Device Section solves it, but does really ugly things around the mouse 
instead.
Goolging for "mouse cursor fglrx" shows, this could be fglrx related?
I'm running on a ThinkPad R52 (ATI X300) 
For dapper everything was fine.

What hardware do you use?

best regards

---

### Post by madcow72 on 2006-11-13
Hey!

Sorry, I hadn't checked this post in a while because there was no response. Thanks for your reply!  I am running a home-built system:  P4 2.4GHz, 1.5 GB RAM, ATI Radeon 9250, using the fglrx driver.  I'll try your:
```
Option "SWCursor" "true" 
```
"semi"fix and see what else I can dig up.  I have gone back to a previous xorg.conf setup in the meantime because I couldn't use the mouse.  If I get this fixed, I'll let you know.

Cheers!

---

### Post by adarof on 2006-11-15
Switching to the old one helped solving the problem?
Does the old one use the radeon driver?

My temp. solution:
I switched back to the radeon driver and its fine for me.

Thanks for feedback.

---

### Post by madcow72 on 2006-12-19
How does switching back to the Radeon driver affect your 3D acceleration and overall performance?  Actually, and I feel kinda sill about this, but I realized that:
```
sudo aticonfig --dtop=horizontal
``` will generate the dual head xorg.conf file that I needed as well as keeping the fglrx driver and, most importantly for this thread, does NOT screw with my mouse.  :o   Now, everything is working beautifully!

To summarize, just in case this helps anyone, I'm now running Edgy Eft, using an ATI Radeon 9250 and this requires the 8.28.8 driver, which I downloaded from [[COLOR="Blue"]here.[/COLOR]]("http://ati.de/support/drivers/linux/linux-radeon-prer200.html")  I used [[COLOR="Blue"]this install method[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") to install the driver under Edgy, (yes, using the 8.28.8 driver, not the 8.32 - don't know if that works yet.)  And, after following their directions explicitly, I logged back into X, verified that the driver was working, and then used:
```
sudo aticonfig --dtop=horizontal
``` to get dual head working.  Finally, a simple restart of X was all I needed and Voila!

Hope this helps!

---

