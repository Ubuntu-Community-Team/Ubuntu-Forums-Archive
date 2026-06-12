---
title: "Booting GParted from HDD"
date: 2015-01-02
forum: General Help
---

### Post by binchunsu on 2015-01-02
So I just made a 1GB partition, how can I boot GParted from there? I downloaded the iso but Startup Disk Creator doesn't let me install it on the partition.

---

### Post by Bucky Ball on 2015-01-02
Just curious as to why you'd want to install it on a partition ... generally goes to disk or USB and kept for fix-it tools. [Sys Rescue]("http://www.sysresccd.org/SystemRescueCd_Homepage") includes Gparted and a heap of other helpful tools and is another option.

Do you have Gparted installed in your regular Ubuntu install? It is in Software Centre ...

---

### Post by binchunsu on 2015-01-02
I currently don't have a USB available, and I want to edit the partition that I am currently using. Thanks for the quick reply! :)

---

### Post by Bucky Ball on 2015-01-02
> **binchunsu said:**
> I currently don't have a USB available, and I want to edit the partition that I am currently using.

Ah, ha. Makes sense. How did you install Ubuntu? Via disk or USB? If so, boot with that, Try Ubuntu. This will get you to a desktop and Gparted may be there. If not, you may be able to install it to RAM (just use Software Centre as per normal to do this) and that should get you there. This WON'T install Gparted to the Live USB/DVD or hard drive and will be gone if you boot from that again. It will allow you to manipulate the partition you have Ubuntu installed on.

Installing Gparted to hard drive will be problematic and not really the intention of the ISO. Once installed you would need to add it to the grub menu so you could select to boot from that partition I suspect.

---

### Post by binchunsu on 2015-01-02
I installed Lubuntu from a USB, but I don't have access to it right now. Installing to RAM...is there a way to install it to the partition I just made?

---

### Post by Bucky Ball on 2015-01-02
I meant you can install Gparted if you boot from the Live Lubuntu USB, and no, not that I know of. Never heard of it being done. Perhaps try a search for 'install gparted to hard drive' and see what surfaces. Is there any instructions on doing this at the Gparted site?

* Update. Ok. Discovered some things. You need the 'Gparted Live' version. You need to use the Gparted Live method to install to hard disk. See [HERE]("http://gparted.sourceforge.net/livehd.php").

---

### Post by binchunsu on 2015-01-02
[http://gparted.org/livehd.php](http://gparted.org/livehd.php) Is this it?

---

### Post by Bucky Ball on 2015-01-02
Yep. Same link as in my last post. ;)

Good luck.

---

### Post by binchunsu on 2015-01-02
Thanks! XD

---

