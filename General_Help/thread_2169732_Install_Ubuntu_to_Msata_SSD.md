---
title: "Install Ubuntu to Msata SSD?"
date: 2013-08-23
forum: General Help
---

### Post by shane4 on 2013-08-23
Hey guys,

I have a fairly modern laptop,Ivy Bridge i5,6GB Ram,32Gb Samsung Msata SSD + 500Gb Standard HDD

Im trying to install Ubuntu (latest version)..during setup it detects both my drives and i choose the 32GB ssd and install goes well,But on boot i get the error...

```
**No Bootable Device - Insert boot disk and press any key.**
```

Now im assuming at boot its not detecting the 32gb SSD,When i go into the bios the only option i have for the "Hard drives" is just "Hard drive"..i cant actually set which hard drive to boot from!
Or does this SSD only assist the ragular hard drive and im not actually able to use it as a dedicated SSD and use the 500gb drive for storage?

---

### Post by shane4 on 2013-08-24
Nobody? :/

---

### Post by tripp98 on 2013-08-24
on your motherboard bios.  check the boot order.  make sure it is trying to boot to ssd.

at the end of the install did grub get installed?

---

### Post by shane4 on 2013-08-24
Hi and thanks for replying,

But as i mentioned,In the BIOS (Which is VERY basic) it only mentioned "Hard Drive" as a bootable,You cannot actually choose which hard drive to boot from...if i choose "Hard drive" it boots only from the standard 500GB hard drive.and not the MSata SSD.

---

### Post by tripp98 on 2013-08-24
odd but i think you can work with it.  if you swap the sata drives 
take the ssd and put it on sata port 0
then put the 500 on port 1
ubuntu should boot.
however in order to get windows back running you will need to swap them back.

what is the make/model of laptop?

---

