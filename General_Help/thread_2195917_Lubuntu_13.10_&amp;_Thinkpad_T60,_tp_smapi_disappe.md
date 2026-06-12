---
title: "Lubuntu 13.10 &amp; Thinkpad T60, tp_smapi disappears"
date: 2013-12-27
forum: General Help
---

### Post by Matti.niemiranta on 2013-12-27
Hello

I have strange problem with this battery management module. Installed with these instructions:

[http://wiki.ubuntuusers.de/TP-SMAPI](http://wiki.ubuntuusers.de/TP-SMAPI)

Works fine at first, but after boot/sys/devices/platform/smapi/  folder disappears and battery management stops working. What could cause this, never had such behaviour or other problems with tp-smapi:confused:

---

### Post by tgalati4 on 2013-12-27
Perhaps it is in a blacklist because it causes problems.  Look in your blacklist:  /etc/modprobe.d/blacklist.conf.  Check the other files as well for conditional load statements.

Check your log files: /var/log/syslog.  There should be a message as to why it is being unloaded. 

Finally, check all of your switches:

```
modinfo tp_smapi
```

---

### Post by Matti.niemiranta on 2013-12-28
Thank you for help!

There was nothing in those blacklist-files. Syslog had notes about installation:

Dec 23 00:22:07 xxxx kernel: [  433.274633] tp_smapi 0.41 loading...
Dec 23 00:22:07 xxxx kernel: [  433.274807] tp_smapi successfully loaded (smapi_port=0xb2)

modinfo prints this:

filename:       /lib/modules/3.11.0-14-generic/updates/dkms/tp_smapi.ko
license:        GPL
version:        0.41
description:    ThinkPad SMAPI Support
author:         Shem Multinymous
srcversion:     B6841670771B2FF5222BFFD
depends:        thinkpad_ec
vermagic:       3.11.0-14-generic SMP mod_unload modversions 
parm:           debug:Debug level (0=off, 1=on) (int)

I tried to install Linrunner's TLP, and tp_smapi started to work normally with it. Don't know why, but atleast it works! So this is solved :)

---

