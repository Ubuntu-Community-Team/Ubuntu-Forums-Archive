---
title: "ghostscript question"
date: 2006-12-11
forum: General Help
---

### Post by dbbolton on 2006-12-11
linuxprinting.org told me to use the following (see this thread [http://www.ubuntuforums.org/showthread.php?t=317078](http://www.ubuntuforums.org/showthread.php?t=317078) )


```
gs -DIVICE=stp -sMODEL=lexmark-z52
```first off, i think i think this is flat out wrong. it kicks back an error about "-dvar=name"

should it perhaps be more like:

```
gs -sDEVICE=stp -sDeviceModel=lexmark-z52
```or do i need to tweak a make file or something?
EDIT: this gives error "unknown device: stp"

references:

[http://www.linuxprinting.org/xerox-faq.html#s_3](http://www.linuxprinting.org/xerox-faq.html#s_3)
[http://www.cs.wisc.edu/~ghost/doc/cvs/Use.htm]("http://www.cs.wisc.edu/%7Eghost/doc/cvs/Use.htm")
[http://www.cs.wisc.edu/~ghost/doc/cvs/Devices.htm]("http://www.cs.wisc.edu/%7Eghost/doc/cvs/Devices.htm")

---

### Post by dbbolton on 2006-12-12
i'm pretty sure there's at least one person in this forum who knows something about ghostscript.

---

### Post by dbbolton on 2006-12-12
perhaps not.

---

### Post by hod139 on 2006-12-12
I'm confused.  Can't you just install the printer, then after Ubuntu chooses the wrong driver change it using the gnome printers settings.  System->administration->printing
then right click the printer, select properties, and click the driver tab.
Under here select the manufacturer as lexmark and choose Z52.

Or am I really confused with what you are trying to do?

---

### Post by dbbolton on 2006-12-12
i tried both drivers, and neither worked. see the link in my sig for more info

---

### Post by matchstich on 2006-12-13
ok, i went to system, administration, printing, then add printer, the wizard came up, and i am on the last step, what do i put in description and location?
thanks

---

### Post by dbbolton on 2006-12-13
> **matchstich said:**
> ok, i went to system, administration, printing, then add printer, the wizard came up, and i am on the last step, what do i put in description and location?
thanks
it doesnt matter. those are just for your personal reference

example description "xerox printer"
example location     "upstairs"

---

