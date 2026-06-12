---
title: "Firefox - Big fonts.. ?"
date: 2008-04-25
forum: General Help
---

### Post by Naatan on 2008-04-25
Hi, I have a problem with firefox 3 on hardy, well actually.. im not sure if it's related to hardy.. but I definitely think it's related to Ubuntu since I don't have the problem on windows.

On some sites (like google) some of the fonts are really big for no apparent reason.. check the screenshot.

Is anyone else having this? 

I've tried running firefox with sudo so it wouldn't use the settings that were transfered from firefox 2 but it has the same problem.

Also - I DID check the zoom option, it's set to it's default size.

---

### Post by DarthTibault on 2008-04-25
Same problem here.
Most text has the right size, but some parts on sites like this one, Google, launchpad, ... are simply huge.
GDM also has big fonts (my username is "higher" than the box)

I think this is because of the nvidia drivers. The GDM issue at least started after installing the proprietary drivers.
I've had the same problem in GDM with feisty as well. I can't remember how to fix it though...

---

### Post by Naatan on 2008-04-25
hmm you could be on to something there, I'm also using the proprietary drivers. Do you have compiz enabled as well?

---

### Post by DarthTibault on 2008-04-25
I indeed have compiz enabled. (Though I doubt compiz has anything to do with fontsizes inside windows)

This problem occurs on my laptop -a Dell Inspiron 1520 with a nvidia 8600M GT- but NOT on my desktop (which has some ATI card).
Both run Hardy. The only software difference between the two would be the display drivers: nvdia-new <-> fglrx
Because the problem started after installing the nvidia drivers I'd say the drivers are to blame...
But how to fix it?

---

### Post by Naatan on 2008-04-27
I fixed it :D thanks to this guys post:

[http://ubuntuforums.org/showpost.php?p=1725039&postcount=3](http://ubuntuforums.org/showpost.php?p=1725039&postcount=3)

Thank god :)

---

### Post by exception on 2008-04-29
Fixed it for me too! Thanks a lot!

---

### Post by pertti on 2008-04-29
Some of the fonts in my Firefox are quite large, i.e. launchpad.net, but I have an ATI card, not an nVidia, and I'm using the proprietary drivers (fglrx). Is this a fault in the ATI drivers aswell?

---

