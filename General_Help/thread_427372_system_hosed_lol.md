---
title: "system hosed lol"
date: 2007-04-29
forum: General Help
---

### Post by sefs on 2007-04-29
hi i somehow managed to messup

how can i reinstall just the kernel image 

i have no access to internet and ubuntu is not recognizing cd file system due to kernal gone bad 

how to re-install kernel

---

### Post by Sammi on 2007-04-29
I'm somewhat of a noob too. But from the top of my head I would suggest you do a search for "Linux kernel" or "Linux image" in Synaptic and then just reinstall that.

---

### Post by sefs on 2007-04-29
that would require access to net or the cd rom,  do you know where i can manually download the debs for

linux-generic
linux-image-2.6.20-15-generic
linux-image-generic

Thanks.

---

### Post by nullfactor on 2007-04-29
Sounds like a similar situation I just ran into yesterday.  I attempted to recompile my kernel to change my processor timing... after that I had no network, no CD-ROM, and no USB.  I just booted back to the live CD, bit the bullet, and reinstalled my system.  Probably not the fix you're looking for, but it'll most likely be the quickest...

Best of luck.

---

### Post by sefs on 2007-04-29
not that again....

I think i want to just download the debs manually first and have a go that way.

---

### Post by nullfactor on 2007-04-29
Is your USB still working?  If so, can you find another system to download the necessary debs onto a USB drive and load them from there?  

Best of luck.

---

### Post by Sammi on 2007-04-29
You should be able to find the debs on the install cd...

---

### Post by Rui Pais on 2007-04-29
> **sefs said:**
> that would require access to net or the cd rom,  do you know where i can manually download the debs for

linux-generic
linux-image-2.6.20-15-generic
linux-image-generic

Thanks.

[here]("http://packages.ubuntu.com/").

---

### Post by sefs on 2007-04-29
In an amazing move there seems to be no linux-image-2.6.20-15-generic package available!  what the hell.


> **Rui Pais said:**
> [here]("http://packages.ubuntu.com/").

---

### Post by Rui Pais on 2007-04-29
> **sefs said:**
> In an amazing move there seems to be no linux-image-2.6.20-15-generic package available!  what the hell.

weird! they forgot to update the thing... If you follow the links to get a 2.6.20-14 it fails (cause thats was one with a bad bug that appeared 1weak before release and was remove).

download from here (for usa):
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux-source-2.6.20/](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-source-2.6.20/)

for europe:
[http://ftp.oleane.net/pub/ubuntu/pool/main/l/linux-source-2.6.20/](http://ftp.oleane.net/pub/ubuntu/pool/main/l/linux-source-2.6.20/)

good luck

---

### Post by sefs on 2007-04-29
Thanks for that Rui.  I'm up and running again.

---

### Post by Rui Pais on 2007-04-29
you're welcome :)

---

