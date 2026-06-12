---
title: "cannot load thinkpad-acpi module"
date: 2008-01-23
forum: General Help
---

### Post by holihue on 2008-01-23
I can't load the thinkpad-acpi module:
```
sudo modprobe thinkpad-acpi
```


I get this:
```
FATAL: Error inserting thinkpad_acpi (/lib/modules/2.6.22-14-generic/kernel/drivers/misc/thinkpad_acpi.ko): No such device
```



kernel version: 2.6.22-14-generic




I want to load this module to try to get temperatures that was missed after upgrading to Gutsy.


Thanks

---

### Post by neozen on 2008-02-21
don't know if it helps.  But I can confirm your problem with loading this module... I am unable to load it either... and get the same message you do.  Haven't really seen a fix for this at all.... annoying b/c the /proc/acpi/ibm/* tree doesn't exist w/o this module being loaded....

Thinkpad model R60e

---

### Post by vaxius on 2008-03-16
I can confirm the same on Thinkpad R60 with Linux Mint (Ubuntu 7.10 with extra features).  I remember this working a few months ago.  It looks as if thinkpad-keys is loading anyway, but with no way to access the keys through the thinkpad module, it's less than useless.

"/etc/init.d/hotkey-setup start" gives:
```
FATAL: Error inserting thinkpad_acpi (/lib/modules/2.6.22-14-generic/kernel/drivers/misc/thinkpad_acpi.ko): No such device
/etc/init.d/hotkey-setup: line 37: /proc/acpi/ibm/hotkey: No such file or directory
grep: /proc/acpi/ibm/hotkey: No such file or directory
```

Found this in the logs, so the problem may be limited to the kernel module.
```
Mar 16 02:49:28 lva0398 kernel: [   30.104000] input: /usr/sbin/thinkpad-keys as /class/input/input8
```

---

