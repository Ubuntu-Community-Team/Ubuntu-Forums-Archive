---
title: "MAX OS X Print Drivers on Ubuntu"
date: 2008-02-06
forum: General Help
---

### Post by bistromatic on 2008-02-06
Hi everyone,

I'm relatively new to Ubuntu and I'm struggling with printing. Big time. To be more precise: photo printing. I''m coming from Windoze using Photoshop CS3 and an EPSON R2400 and most of my work is B&W. This printer allows to make very fine B&W prints using the EPSON print driver under Windoze. 

I really would like to move completely to Ubuntu but this printing issue makes me go back to Windoze because GIMP, and Gutenprint, and AVASYS PIPS for CUPS, you name it, does not meet my quality expectations. 

Now here is my question: since EPSON has the same driver available for MAC OS X and MAC OS X is a BSD derivative using CUPS (which comes from Apple) shouldn't there be a way to use these drivers on Ubuntu?

The following thread [**Hacking up Apple print drivers for Ubuntu**]("http://ubuntuforums.org/showthread.php?t=441821") was started last year but it somehow dried up. Does that mean there is no way to use these drivers or did just nobody know how to use them?

I would really appreciate some help or ideas on how to solve my printing problem.

---

### Post by bistromatic on 2008-02-07
I cannot imagine that nobody knows anything about this. Is this a taboo issue to talk about  or what's going on?

---

### Post by mrsteveman1 on 2008-02-07
Using the apple driver is unlikely to fix application issues, and the apple drivers tend to be more than simply the ppd file etc.

There is always a lot of control code in the apple drivers just like with windows, for controlling proprietary features etc. That sort of stuff probably can't be used from the OS X drivers.

---

