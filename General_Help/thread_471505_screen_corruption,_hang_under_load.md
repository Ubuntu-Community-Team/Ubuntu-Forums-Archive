---
title: "screen corruption, hang under load"
date: 2007-06-12
forum: General Help
---

### Post by bobtins on 2007-06-12
I'm setting up a development system and I started out installing the 7.04 server iso. I then added the ubuntu desktop metapackage to get graphics. In the process of mucking with dselect, I also got the 2.6.20 kernel. Hardware is:
amd athlonx2 4600+
Asus M2A-VM HDMI motherboard with amd 690g chipset & sb600, using integrated video
2G ram
WD 150G raptor SATA drive
SATA optical drive

I had to add the following boot options to get install running: pci=nomsi irqpoll noapic acpi=off

I set up a java dev environment which included tomcat, mysql, maven, etc. 
Doing a large build goes OK, but when I do unit tests, which hit mysql a lot, the computer would hang more than half the time. This would often be accompanied by the video getting corrupted. I originally was doing a graphical login but I disabled this along with the splashscreen on boot. In text mode I would see random spots all over, so it seems like something was overwriting video memory.
My system is pretty much unuseable at this point and I'm thinking of going back to just a plain server install, possibly to the 6.* version. 
It looks like something is overwriting video memory; this is a pretty new mobo so maybe the drivers aren't all the way there, and something is confused about what memory is used for.
Anyone have a clue? 

Thanks,
Bob

---

### Post by bobtins on 2007-06-12
](*,) help!!!

One other thought...since I don't think I'm using X at all (I don't see any *gart modules being loaded with lsmod), maybe the prob isn't video at all...but something writing over the memory...or some kind of weird mem problems. I'll try running some memtest. Any other ideas???

---

### Post by bobtins on 2007-06-13
This turned out to be a faulty stick o' ram--I just had to run memtest to find the problem. When I removed one of the sticks, I was able to run just fine.

---

### Post by salpis on 2007-08-21
> **bobtins said:**
> This turned out to be a faulty stick o' ram--I just had to run memtest to find the problem. When I removed one of the sticks, I was able to run just fine.

I seem to have same problem and since I am quite new with linux, please let me know how can I do that memtest and remove sticks if needed.  :)

---

