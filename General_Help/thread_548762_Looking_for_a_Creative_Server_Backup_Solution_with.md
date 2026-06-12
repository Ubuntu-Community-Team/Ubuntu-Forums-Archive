---
title: "Looking for a Creative Server Backup Solution with USB"
date: 2007-09-11
forum: General Help
---

### Post by the ev on 2007-09-11
Okay.  So I got cute with my server and epitomized separation of OS & Content by installing Ubuntu Server directly to a flash thumb drive, which I mounted all neat-like inside the chassis using a modified USB PCI slot (so nothing's attached outside - very clean).  It works great! Bootups are relatively quick, since the OS is already pretty lean.  That way I can have my 500 giggers be purely data, which makes for managing replacement drives and the like much easier.  

Now, I'd like to have a way to clone that little flash stick in case I somehow screw up my installation (easy reinstallation), or if the drive dies on me for whatever reason.  I know there are plenty of liveCD's that can do this, but I'm sitting here looking at this spare internal USB port and I got to wondering...

...would there be any way to put an even smaller, slimmer, leaner linux install on a second flash drive, such that I can have a cron job that restarts the machine to the second usb stick, have a boot script that runs on it that clones the first and saves the image to a compressed file on one of my hard drives, then reboots back to the first, main OS?  So in every x time frame, the server would reboot, clone it's OS internally to a hard drive, then boot back up like normal?

Does that sound feasible?

---

