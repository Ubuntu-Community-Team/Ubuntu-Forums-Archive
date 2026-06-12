---
title: "How to start wubi?"
date: 2008-05-24
forum: General Help
---

### Post by okinaro on 2008-05-24
Hi, sorry if this is really basic - Im new!
I've installed Wubi from the CD and I can't work out how to open it and run Ubuntu!
According to the guide on the Wubi website, I should get a windows boot menu, but I don't, it just starts automatically into windows. Please could someone tell me how to fix this?

Thanks



:popcorn:

---

### Post by ago on 2008-05-24
What OS do you use? If it is XP check boot.ini, in vista use EasyBCD. You should have a wubi option.

---

### Post by blazemore on 2008-06-01
Vista: start-> type msconfig.exe and press enter

Locate the "boot" tab and click it.
Ensure the "timeout" option is set to 10, and there is an option for Wubi in the list.

---

### Post by Paul-Devon-UK on 2009-04-24
@okinaro

I ended up here grom a Google search as I was just as confused. I guess you did the same as me. Rushed into this, all excited, but forgot to RTFM first. I thought it would be a VM type install that would run from XP.

Oh well, off to reboot and see if, yet again, the graphics drivers for my 1440x900 screen are pants.

---

### Post by Paul-Devon-UK on 2009-04-25
> **Paul-Devon-UK said:**
> Oh well, off to reboot and see if, yet again, the graphics drivers for my 1440x900 screen are pants.

Sorry for the double post but YAY!!! IT WORKS!

'Out of the box' wireless AND graphics. The most minor of GUI tweaks and I was wirelessly browsing at 14400x900.

This is finally looking like a viable distro to dump XP.

Thanks :P

---

