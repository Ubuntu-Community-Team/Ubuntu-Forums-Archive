---
title: "Shutdown/Restart hangs"
date: 2006-11-20
forum: General Help
---

### Post by ChadMC on 2006-11-20
When I try to restart or shutdown it hangs on this line:
```
Stopping system message bus dbus...
```
I'm not sure what to do. If I do this command, everything seems to work right:
```
chad@chad-linux:~$ sudo /etc/init.d/dbus restart
Password:
 * Stopping System Tools Backends system-tools-backends                  [ ok ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ ok ] 
 * Stopping Hardware abstraction layer hald                              [ ok ] 
 * Stopping system message bus dbus                                      [ ok ] 
 * Starting system message bus dbus                                      [ ok ] 
 * Starting Hardware abstraction layer hald                              [ ok ] 
 * Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ ok ] 
 * Starting System Tools Backends system-tools-backends                  [ ok ] 

```
I'm not sure why it won't stop when trying to shutdown/restart.

Any suggestions? I'm running Edgy.

-Chad

---

### Post by ChadMC on 2006-11-20
Anyone? Also, where are the logs placed for the shutdown process?

---

### Post by pliktrologos on 2006-11-21
I have also the same problem with edgy although I don't even see the boot splash screen either on loading/starting or shutting down/restarting...

---

### Post by dacool25 on 2007-03-16
sorry to bring this up again, but i'm also having this problem.  After "stopping system message bus dbus" it hangs and nothing happens, and i have to do a hard shut down.  Anyone have any ideas?

---

### Post by jwalker46 on 2007-04-30
Sorry to add the fourth request for help: An install of 7.04 works fine, except that on restart I get a fuzzy screen (like a poor tv test pattern), and the system simply will not hand off to the bios for a reboot.

Can anyone please help ??

System: dual-boot, Vista & 7.04, GRUB installed in root, EasyBCD boot mgr (works fine, i.e. finds & boots both OS), Intel dg965wh mobo.

---

### Post by jwalker46 on 2007-05-01
(bump)

---

### Post by wxnker on 2007-06-22
Well. I also have a similar problem. If I press "log out" "shut down" or "restart" Ubu & Kubu will hang. The desktop icons will be gone, but I still get the wallpaper, menu and panel/kicker. CTRL+ALT+Backspace and CTRL+ALT+F2 solutions do not work. All I can do is shut down or reset the PC.

The problem does not occur every time I want to reboot, shutdown or log out, but most of the times it does.

I have been investigating this but I've found no reasonable solution. It's an anoying problem, but Ubu/Kubu is not my main Linux OS so I guess I'll just have to wait it out.

Regards
w

---

