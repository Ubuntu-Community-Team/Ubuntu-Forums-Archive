---
title: "Why and how bootloaders affect OS robustness"
date: 2013-01-07
forum: General Help
---

### Post by d0ugparker on 2013-01-07
I did a search, but didn't find anything 
on this.

Mac G5 desktop running 10.5.8 dual booted 
with Ubuntu 12.04.01. 

When I boot into OS X using yaboot, X will 
eventually lock up. If I hold down the 
option to get Apple's bootloader, I don't 
have lockup problems. 

I also believe I have no problem starting 
Ubuntu using either bootloader. 

So, my question is, "What is it about 
different bootloaders that affects the 
robustness of an OS," or "Why might yaboot 
freeze my 10.5.8 desktop session?" :)

Thanks. 

Doug P
Orlando, FL
USA

---

### Post by ajgreeny on 2013-01-07
Do the two bootloaders have, or allow, different kernel boot options, that may be set differently.

For example using grub it is possible to set kernel boot options such as nomodeset in a configuration file which can help to boot to a GUI with some nvidia graphics hardware in particular.  I don't know anything about apple-mac hardware or software so may be talking out the back of my head, but it could be worth investigating.

---

