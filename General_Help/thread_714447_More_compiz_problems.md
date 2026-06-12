---
title: "More compiz problems"
date: 2008-03-03
forum: General Help
---

### Post by jsprung on 2008-03-03
Compiz was running fine on my desktop, looking all flashy and pretty. Then I tried to fix my graphics card, which I failed at. My settings are now back to where they were before the attempted fixings, but compiz won't work now. Whn i try to enable it, I get this dialog:

> jonah@ROBOT:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:554d (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity

My graphics card is an ATI x800 XL.

Can anyone help me get compiz abck up? I am at a loss.
Thanks,
Jonah Sprung

---

### Post by Joeb454 on 2008-03-03
It cannot find the XGL driver for your card.

Unfortunately I've never worked with an ATi card. You might want to search Google for "Envy" which is a script to install ATi/Nvidia drivers on Linux.

However installing drivers from the repositories might also be possible, you'll have to see if they're in synaptic :)

---

### Post by jsprung on 2008-03-03
Sadly, Envy has not worked for me. I tried installing Xgl from synaptic, but it did not help. Now i get this dialog when attempting to enable compiz

jonah@ROBOT:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Starting emerald
/usr/bin/compiz.real: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

---

