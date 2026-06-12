---
title: "Broke my Ubuntu-X won't work"
date: 2007-01-12
forum: General Help
---

### Post by sevesteen on 2007-01-12
Was trying to get ndiswrapper and CRT support working in my laptop, and now Linux won't boot, even in recovery mode.   I suspect it's a problem with Xorg, because if I ctrl-alt-del when it hangs, I can get to a text logon.  I screwed up, and the instructions I followed for enabling the CRT were for the wrong Intel chipset.

When I boot normally, I'll get a flashing dash cursor that hangs forever. Ctrl-alt-del gives me an error message "could not start the X server (your graphical envoronment) due to some internal error.  Please contact your system administrator or check your syslog to diagnose.  In the meantime this display will be disabled.  Please restart GDM when the problem is corrected. "  ctrl-alt-del again will (sometimes) bring me to a text login screen.  

Recovery mode scrolls through the various stuff, stops for a while on the line 
[17179600.72400] ndiswrapper version 1.33 loaded 9preempt=no, smp=yes]
I thought it got past this line before, but hasn't the last two times. Ctrl-alt-del gets me to a root prompt.  

I can still boot from a live Edgy CD, and I'm able to mount the old drives and access/edit/save config files, but I don't know which files to  change.  

How do I get rid of the ndiswrapper stuff. to eliminate that from the equation? How do I get the Xorg stuff back to default? 

What's the best first step in fixing this?  I'd rather not have to reinstall.

---

### Post by pissedoffdude on 2007-01-12
try this: ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by sevesteen on 2007-01-12
> **pissedoffdude said:**
> try this: ```
sudo dpkg-reconfigure xserver-xorg
```

Looks like I need to do something different first--I get an error "Cannot create regular file '/etc/x11/xorg.confi.20070112005226': Read-only file system".   Same if I do a sudo mount -a first.

---

### Post by sevesteen on 2007-01-12
I don't think it's a problem with the xorg.conf files, the last change date is Dec 2, and it has been rebooted several times since.

---

