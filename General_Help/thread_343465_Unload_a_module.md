---
title: "Unload a module"
date: 2007-01-21
forum: General Help
---

### Post by dmsn on 2007-01-21
Hey i wonder how i can unload a module.

rmmod blabla
ERROR: Module blabla is in use

Any ideas? What file/s has the modules which start in boot?

---

### Post by teaker1s on 2007-01-21
as far as I'm aware 
[COLOR="Red"]sudo modprobe -r nameofmodule[/COLOR]

but I installed and use
**module-assistant**

---

### Post by dmsn on 2007-01-21
dmsn@box:/etc$ sudo modprobe -r ipv6
FATAL: Module ipv6 is in use.
dmsn@box:/etc$

---

### Post by teaker1s on 2007-01-21
why are you removing ipv6 networking module

---

### Post by ztirffritz on 2007-01-22
I'm trying to connect a printer using vmware.  The printer requires access to the parallel port.  When I try to unload the module "lp" in Linux I get:

sudo rmmod lp
ERROR: Module lp is in use

Anyone know how to get around this?

---

### Post by LucasCosta on 2007-03-20
Just log off of your current user session, and then press Ctrl+Alt+F1.
there just do "sudo modprobe -r nameofmodule".
to go back to the login screen press Alt+F7

---

