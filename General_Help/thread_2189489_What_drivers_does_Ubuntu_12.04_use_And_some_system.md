---
title: "What drivers does Ubuntu 12.04 use? And some system related qs"
date: 2013-11-22
forum: General Help
---

### Post by ballistic turtle on 2013-11-22
For the screen display? It seems to do a way better job at brightness and colour than Windows 7 does on my laptop. Although in some places it looks a bit fuzzy compared to 7

And how do I see a list of installed hardware and drivers (and therefore be able to roll them back)?

---

### Post by Bashing-om on 2013-11-22
keys.snickers; Hi !

In direct response to the drivers:
Launcher -> System Setting -> Additional Drivers;

As to hardware; a different mind set than that of what you are accustomed to; I prefer to look at my system from the command line as I prefer black and white text over a pretty picture:
lspci : List all PCI buses and devices connecrted to the machine;
lsusb : List all USB buses and any connected USB devices;
lshal : List all devices the Hardware Abstraction Layer (HAL)  knows about .. which should be most hardware on your system --- in version 13.10 HAL has been superseded, this command may no longer apply (??)
lshw : List of hardware on the system .

Reading is good ! see: (for instance)
```
 
man lspci

```

[INDENT][INDENT]hey, just try'n to help
[/INDENT][/INDENT]

---

