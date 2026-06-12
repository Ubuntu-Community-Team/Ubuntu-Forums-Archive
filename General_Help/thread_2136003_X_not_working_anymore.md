---
title: "X not working anymore"
date: 2013-04-16
forum: General Help
---

### Post by Dragonsong on 2013-04-16
Hello,
Trying to boot my laptop today it turned out my X is no longer working. What happens is, after booting it complains about not being able to find my monitor / graphics card / input device and offers me several options such as going to a console, viewing the error message and all that. X is unresponsive there so I cannot select any of the options.
VT switching works though.
Any ideas what might be the problem / what to do to figure the problem out? Everything was working fine until today.

I uploaded various logs here:
[http://heavylobster.com/files/dmesg](http://heavylobster.com/files/dmesg)
[http://heavylobster.com/files/Xorg.0.log](http://heavylobster.com/files/Xorg.0.log)
[http://heavylobster.com/files/Xorg.failsafe.log](http://heavylobster.com/files/Xorg.failsafe.log)

Thanks in advance!

---

### Post by dargaud on 2013-04-16
I can't figure out what kind of graphic card you have. Intel maybe ? If it's nvidia, try running "sudo nvidia-xconfig"

---

### Post by Dragonsong on 2013-04-16
> **dargaud said:**
> I can't figure out what kind of graphic card you have. Intel maybe ? If it's nvidia, try running "sudo nvidia-xconfig"
It is an intel card (ivy bridge, so HD 4000)
In case it matters I also have the geforce 640M (it's an optimus laptop) with bumblebee.

---

