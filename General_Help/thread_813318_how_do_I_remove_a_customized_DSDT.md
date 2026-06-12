---
title: "how do I remove a customized DSDT?"
date: 2008-05-30
forum: General Help
---

### Post by krantix on 2008-05-30
Hi! I've messed up with my dsdt and would like to return to the normal bios settings. 

How do I remove a DSDT from my boot image?

thanks!

---

### Post by sdennie on 2008-05-30
You should be able to simply:

```

sudo rm /etc/initramfs-tools/DSDT.aml
sudo update-initramfs -u -k `uname -r`

```

---

### Post by krantix on 2008-05-30
thanks vor,

would this bring me back to ACPI as defined by my bios?

---

### Post by sdennie on 2008-05-30
It should, yeah.  I'm not positive about the "-u" option to update-initramfs in this case so, if it doesn't work, maybe try "-c" instead.

---

### Post by krantix on 2008-05-30
thanks Vor! it worked, actually I run 

sudo dpkg-reconfigure linux-image-$(uname -r)

to get the image rebuilt.

For anybody interested do not UPDATE to TOSHIBA P100 BIOS 4.30
it changed the behavior of my CPU fan and I had to go back to 4.20

---

### Post by sdennie on 2008-05-30
It's funny that you mention that Toshiba P100 series of laptops.  The only reason I know anything about DSDT stuff is because of one of those laptops.  It eventually met its rightful fate (me taking a baseball bat to it) but, I was actually one of the people that worked on some of the DSDT solutions for the various BIOS revisions of that laptop.

(As a sidenote, NEVER put absurd values into the VTMP on that machine.  It doesn't break it but, it does scary things).

---

### Post by krantix on 2008-05-30
I've got that dsdt working after months of searching and trying, but then I've failed miserably by installing the new bios (just got out 2 days ago) and the CPU fan was going crazy.

Now I've even discovered that the bios does not enable PAE, even if the Intel Chipset supports it. Installing linux-kernel-server does not make any difference and my 4GB of ram are down to 3GB (I'm also too scared of switching to 64bit right now that everything seems fine!)

:)

---

### Post by sdennie on 2008-05-30
You probably can't switch to 64bit.  I tried to install 64bit Ubuntu on a P100 series machine and it didn't work (the kernel complained that it wasn't supported).  Though, you are lucky in that you were able to even boot with more than 2G of RAM (mine wouldn't).  PM me in a few months with pictures of you taking a baseball bat to the machine and I'll send you mine.  ;)

---

### Post by krantix on 2008-05-30
Seems like Ubuntu is doing huge progress.

LiveCD 64bit runs perfectly on my Toshiba P100-126...

but still only 3GB of memory are seen by the system. Windows Vista declares 4GB but then uses 3GB anyway...

there is room for a class-action, I've bought this laptop has 2GB upgradable to 4GB!!!:mad::mad::mad::mad:

---

