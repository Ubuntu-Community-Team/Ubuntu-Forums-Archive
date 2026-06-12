---
title: "Ubuntu cell phone"
date: 2007-07-09
forum: General Help
---

### Post by kdarkentity on 2007-07-09
Is there a way to boot ubuntu or another version of linux off of a razer cell phone?

---

### Post by daou on 2007-07-09
Short answer: theoretically yes, practically no.

Long answer:
This is pretty much a quick description of embedded development:
If there is no development branch to get Linux working on that cell-phone, it won't be anything as simple as plugin and install.
You would need to pretty much develop the platform yourself.

First, you would need to find out what kind of processor it uses (ARM-11 perhaps?). If that processor has Linux support, you would then need to cross-compile it (and find a cross-compiler as well for that processor).
Then you would have to dig up how to get your own boot loader on the device. You would need to configure the boot loader (and get a version that is supported by the processor, if one exists). Then upload it to the correct location in memory so that it takes over the device during boot. And even then, some part of the process is probably blocked by Motorola.
Now, if you can get both the boot loader and the kernel on the device, there is some hope.
Then you would have to configure a window manager with xserver (or another variant) to work on the device. Two problems come up straight away: a nonstandard resolution and input mechanisms. For example, you no longer have a mouse and a keyboard. You would have to develop drivers for the cellphone buttons to act as a keyboard and include them into the kernel. You would need to cross-compile and possibly change the code in each application that you want to use on the device.  Ah.. the list just keeps going.

Basically, it's not exactly a one man job. And a lot of experience is needed to even know where to start. The best way to get a taste of what this is all about is to get a phone that already has Linux, then start hacking at it.

---

### Post by kdarkentity on 2007-07-09
ok thanks man... i really dont think i have the patience for an attempt at that kind of project tho... oh well it was just an idea

---

### Post by Tautoa on 2007-07-10
There are communities that modify motorolas in interesting ways. Doing stuff with the bootloader is definitely possible, and you can flash new software to the phone to change it completely. I've done this with my L7, but I don't completely understand the process, but you can always ask around at [http://www.planetmotox.net/](http://www.planetmotox.net/)

I believe they also have a section for motomodders who use Linux (on their home PC, not phone :) )m so there maybe others who have had this idea :)

---

### Post by kdarkentity on 2007-07-10
thank you this may be somewhat helpful

---

