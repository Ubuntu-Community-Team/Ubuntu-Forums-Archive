---
title: "Wubi interface question"
date: 2007-10-19
forum: General Help
---

### Post by asbjornu on 2007-10-19
In Wubi, the installation asks what partition to install to. What I wonder is; will this partition be wiped? Won't I get the opportunity to partition my harddisk like in usual Ubuntu installations? Or will only Wubi install on the partition I choose and then I choose where Ubuntu installs later? Or what?

It would be nice if this was explained a bit better in the GUI. It confuses me at least. :)

---

### Post by ago on 2007-10-19
> **asbjornu said:**
> In Wubi, the installation asks what partition to install to. What I wonder is; will this partition be wiped?
No, wubi installs Ubuntu within a file, but this file has to be sitting somewhere... ;D

---

### Post by asbjornu on 2007-10-22
Aha! But, "within a file", what does that mean? Is this file extracted upon every boot or what? Why doesn't Wubi allow Ubuntu to be installed normally, like on its own partition? (Sorry for being a bit thick-headed)

---

### Post by ago on 2007-10-22
> **asbjornu said:**
> Aha! But, "within a file", what does that mean? Is this file extracted upon every boot or what? Why doesn't Wubi allow Ubuntu to be installed normally, like on its own partition? (Sorry for being a bit thick-headed)

Because the very idea of Wubi is to allow to install Ubuntu without having to modify the partitions. If you want a dedicated partition, you can use unetbootin or the LiveCD.

Think of Wubi as any other applications. It just creates a "wubi" folder with the required files on one of your disks.

---

### Post by asbjornu on 2007-10-22
Oh, then I've misunderstood the point of Wubi completely. You see, I'm stuck with a computer without a CD ROM or floppy drive, and no way to boot off a network (the BIOS doesn't have the option). I'll buy a floppy drive to update the BIOS, but I still don't think I'll be able to boot off the network.

So I thought a Windows-based installer was the perfect solution. Only to find out now that it isn't at all what I was looking for. I guess I'm the only person alive with the "no floppy, no CD, no network" requirement. :(

---

### Post by ago on 2007-10-22
> **asbjornu said:**
> Oh, then I've misunderstood the point of Wubi completely. You see, I'm stuck with a computer without a CD ROM or floppy drive, and no way to boot off a network (the BIOS doesn't have the option). I'll buy a floppy drive to update the BIOS, but I still don't think I'll be able to boot off the network.
Yeah wubi does allow to skip a CD too... But it still installs within a file. 
If you want to install without CD to a dedicated partition, use Unetbootin: [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by asbjornu on 2007-10-22
Ah, UNetbootin seems like the perfect match. Thanks for pointing it out!

---

