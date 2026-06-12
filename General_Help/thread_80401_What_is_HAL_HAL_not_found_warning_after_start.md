---
title: "What is HAL?????? HAL not found warning after start"
date: 2005-10-22
forum: General Help
---

### Post by metalbird on 2005-10-22
The title pretty much explains it my problem!  Anyone?

---

### Post by ReadAloud on 2005-10-22
Starting synaptic (package management)

```
sudo synaptic
```

and searching for HAL yields the following:

[I]Hardware Abstraction Layer
HAL provides an abstract view on hardware.

This abstraction layer is simply an interface that makes it possible to
add support for new devices and new ways of connecting devices to the
computer, without modifying every application that uses the device.
It maintains a list of devices that currently exist, and can provide
information about those upon request.[/I] 

Couldn't have said it better :)  This seems to be basically the piece of software that lets you use your USB port and the like. If it's missing, your computer will most likely give you serious problems when connecting a device, such as an USB stick.

Now, if it's still missing (your post is quite old by now), just install the package via synaptic.

---

