---
title: "bonobo activation problem and other issues"
date: 2008-07-04
forum: General Help
---

### Post by sandipg on 2008-07-04
Hi,

Im running Hardy LTS on AMD 3200+ with nvidia graphics. When I login, I get two errors saying:

Nautilus cannot be used now to an unexpected error from bonobo when trying to register the file manager view server.

and 

The panel encountered a fatal error 

Details> Could not register the bonobo-activation-server (error code:3) and will exit. It may be automatically restarted.

Due to these errors, I cannot see the panels - just a blank desktop is visible. Hence I am forced to use the Failsafe mode.

I have heard that this is a known bug; used killall bonobo-activation-server at the terminal and killall nautilus, but still the error persists.

Another problem: fsck at the terminal gives :

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=7efbad88-c7d1-4ccd-a97d-7c3079a2c952'

I used vol_id -u /dev/sda8 to check the UUID and it matches, so I dont see where the problem is arising. 

I also randomly face grub problems (Error: 18 and Read Error) as well as slow loading times.

I wonder what is wrong with my box...

sandip

---

### Post by SphereCat1 on 2008-07-21
Hi! This is my first post in the Ubuntu forums!

I'm having the exact same problem, with the panel and nautilus. I just installed two days ago, so I haven't tried fsck to see if that happens too.
I'm using Dapper Drake on a PowerBook G3, Pismo to be exact. I managed to get it running until shutdown yesterday by messing around in the Failsafe command prompt and then rebooting after I flashed the PRAM, but now it won't work even after trying the same thing. If anyone knows what's going on, I'd be very grateful.

:confused:
SphereCat1

EDIT: also, I can get the panel running by hitting my shortcut for the terminal (set it yesterday to be safe -- looks like it was a good idea.) and typing in gnome-panel, but none of the applets work, i get a seperate error for each one, something about the OAFIID and monikers, I think. Doing the same for Nautilus won't work.

---

