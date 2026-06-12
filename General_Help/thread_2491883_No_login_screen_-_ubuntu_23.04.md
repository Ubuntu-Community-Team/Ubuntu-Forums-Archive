---
title: "No login screen - ubuntu 23.04"
date: 2023-10-24
forum: General Help
---

### Post by jezzaw007 on 2023-10-24
Only just noticed this issue - ubuntu 23.04 was checking stuff prior to preparing to uplift to 23.10

The screen has been locking to login page and I have been logging back to wayland gnome desktop fine, 
rebooted and now no logon screen.
On further checking, if i manually logout of the desktop there is no logon screen either it goes to shell 

I have tried reinstall gdm3 with no luck, and I am not finding any reason in logs that I can see as it seems to be only partially working when screen locks.

Which log files can I check further for troubleshoot this?

---

### Post by MAFoElffen on 2023-10-24
So are you saying it boots to a black screen without going to GDM3? Or that it boots to a login prompt at the vtty console?

I would say, if black screen, then simultaneously press <Cntrl><Alt><F4> to try to toggle to vtty4 and log in.

Check 
```

sudo systemctl status gdm3 --no-pager
journalctl -b -l -u gdm3 --no-pager

```

---

### Post by jezzaw007 on 2023-10-25
Many thanks

I ran those commands, still didn't see anything, but then checked again and spotted in auth.log the gdm account was failing to start gdm-launch-environment
not what i was expecting but I have now resolved it

---

