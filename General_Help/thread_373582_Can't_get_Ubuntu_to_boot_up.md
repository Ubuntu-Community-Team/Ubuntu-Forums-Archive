---
title: "Can't get Ubuntu to boot up"
date: 2007-03-01
forum: General Help
---

### Post by NCStone on 2007-03-01
I have installed Ubuntu on an older Aptiva. (I actualy set up the drive on another machine and just installed the drive.) When trying to boot up, I get an error - error-18 - and the boot-up freezes. All the info I have looked at from IBM's support pages refer to server and license issues. There has been nothing there to point to the issue that's occuring with my machine.

The drive was formated as new before I started the instal and I was able to run Ubuntu without and trouble on my main machine (the one I set up the drive with).

Any ideas would be greatly appreciated.

Thanks

---

### Post by azazel00 on 2007-03-01
You must be sure the drives are in the correct configuration.

For example: if you configured the system on the other machine on your first IDE slot, as a slave. And then install it on your Aptiva as a Master. It may have some truoble finding your ubuntu installation.

Other than that, I dont know what else could be the problem.

---

### Post by NCStone on 2007-03-01
Thanks for the reply.

The OS was installed with the drive as master and was configured as master in the older machine.

---

### Post by Seq on 2007-03-01
Could it be something like LBA/CHS/whatever? Though I have not come across this in a few years, and I would suspect it possibly is not due to the fact that grub is run at all.

---

### Post by NCStone on 2007-03-01
I have gone through and checked BIOS/CMOS and HD jumper configuration and everything seems to be correct.

---

