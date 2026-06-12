---
title: "Freezing during boot"
date: 2008-03-31
forum: General Help
---

### Post by RoyalPro on 2008-03-31
I have been using Ubuntu 7.10 as part of my mythtv pc setup.  When it just started to lock up requiring a hard restart/shutdown.  This started to happen more and more frequently until it was booting up and doing a disk check that never got past 30% then it never got past 9%.  I booted the live cd and ran gparted check on the disk then when I reboot it lock on the ubuntu screen.  If it boot in recovery mode it stalls on the info below.  If you need any other info let me know.
```
Begin: Running /scripts/init-bottom ...
Done.
init: Error parsing configuration: No suck file or directory
[    7.636000] Kernel panic - not syncing: Attempted to kill init!
```

---

### Post by PmDematagoda on 2008-03-31
I think you may have corrupted the init scripts through all the hard reboots, this is very bad and I really do not think there is much to do than to do a clean reinstall.

Also, whenever Ubuntu locks up again please try and use the [magic SysRq]("http://ubuntuforums.org/showthread.php?t=617349") keys to reboot the system cleanly instead of doing a hard reboot all the time.

---

### Post by RoyalPro on 2008-03-31
I was afraid of that and thanks for the info on the keys.

---

### Post by RoyalPro on 2008-03-31
Well after all that, I think it was the PSU that was going out.  Now the switch on the back that used to start my fans before the power is pushed just gives them a little nudge and the power button does nothing.

---

