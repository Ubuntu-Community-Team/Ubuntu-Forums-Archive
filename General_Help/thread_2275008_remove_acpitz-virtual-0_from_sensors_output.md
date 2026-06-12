---
title: "remove acpitz-virtual-0 from sensors output"
date: 2015-04-23
forum: General Help
---

### Post by mrJTparadise on 2015-04-23
[SIZE=3][COLOR=#111111][FONT=Ubuntu]I am able to ignore certain readings (in0, in1, temp1, fan1, etc).
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Is there a way to ignore entire chips?
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The obvious answer is to unload the module, and if so what module is associated with acpitz-*?
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I do not desire having acpitz-virtual-0 displayed.  

man sensors.conf doesn't say it is possible.

acpitz-* isn't in sensors3.conf.dpkg-dist either.
[/FONT][/COLOR][/SIZE]
```
root@xxx:/# sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.8Â°C  (crit = +100.0Â°C)
temp2:        +29.8Â°C  (crit = +100.0Â°C)
temp3:        +34.0Â°C  (crit = +125.0Â°C)
```

[SIZE=3][COLOR=#111111][FONT=Ubuntu]I've tried ignore "acpitz-*" but sensors3.conf does not like it.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any help would be great. Thanks all.[/FONT][/COLOR][/SIZE]

---

