---
title: "AbiWord won't install: something about unicode map"
date: 2007-03-22
forum: General Help
---

### Post by Comrade42 on 2007-03-22
(I'm on Edgy Eft)

I downloaded the AbiWord install package from here: [http://www.abisource.com/download/](http://www.abisource.com/download/) and followed the Linux download instructions. When installing, everything went perfect, until I got this message:

```
Error: Package 'Unicode character map' was found but was of the wrong version and the correct version could not be located.

[IV 4.0 for @gnome.org/libgucharmap]

Error: Unable to prepare package AbiWord Word Processor.

```

How can I fix this?

(Note: I am only using AbiWord because I tried to install OpenOffice 2.1 and it somehow not only failed to install, but took out my current OpenOffice 2.0 in the process, leaving me naked and without a functional word processor. I might leave more details in another post.)

---

### Post by kerry_s on 2007-03-22
Is there a reason your trying to compile everything?
You can use synaptic to install all that without dependency hell.

press alt+F2 and type> gksu synaptic

---

### Post by Comrade42 on 2007-03-22
Thank you! It is fixed now.

---

