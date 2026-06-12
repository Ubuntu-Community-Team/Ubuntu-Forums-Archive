---
title: "Is there a need for a separate boot partition?"
date: 2008-06-11
forum: General Help
---

### Post by armandop on 2008-06-11
What am I trying to do:
Doing new system build on 500GB SATA drive. Will have Ubuntu as main OS and I'll be trying out other distros on same drive different partitions (openSUSE, LinuxMint).

I also have XP on another IDE drive and I want the Ubuntu drive to be main bootable drive in machine for dualbooting to XP.

Do I need to set aside a boot partition on the 500GB drive ? Does this have to be mounted as /boot for my Ubuntu install ? Are they related at all ?

---

### Post by Victormd on 2008-06-11
The only thing you need to keep in mind, is that Ubuntu should be installed after Windows because windows won't recognize your ubuntu install and therefore, no "easy" dual-boot.
You don't need to worry about creating a separate boot partition, but depending ou how much playing around you're going to be doing, it might be a good idea, simply to keep it clean. On that note, keep in mind that, everytime you install a different distro, your boot menu will be updated to reflect the new distro so if you want to go back to ubuntu you'll need to have something like Supergrub.

---

### Post by Sef on 2008-06-11
> Do I need to set aside a boot partition on the 500GB drive ? Does this have to be mounted as /boot for my Ubuntu install ? Are they related at all ?

No.

> everytime you install a different distro, your boot menu will be updated to reflect the new distro so if you want to go back to ubuntu you'll need to have something like Supergrub.

[Super GRUB Disc]("http://www.supergrubdisk.org/") is there.

You can also manually change the boot order by going into GRUB.

---

### Post by adrian15 on 2008-06-12
> **armandop said:**
> Do I need to set aside a boot partition on the 500GB drive ? Does this have to be mounted as /boot for my Ubuntu install ? Are they related at all ?

**Yes.**

Please check:
[Grub Error 18](http://www.supergrubdisk.org/wiki/GrubError18) (Check Herman's resource).

When multiboot I recommend 300 MB for /boot.
Please also check:
[The Best Linux Installation (ES)](http://www.supergrubdisk.org/wiki/TheBestLinuxInstallation/es)

(Sorry it is written in Spanish and should be translated to English. Nobody has offered himself to translate it yet. However you can check the proposed partition layout.)

Finally some tricks on how to boot when multibooting:
[Multi Distribution Boot Howto](http://www.supergrubdisk.org/wiki/Multi_Distribution_Boot_Howto).

About mounting it... yes you should mount it as /boot in your Ubuntu installation.

adrian15

---

### Post by devonharlan on 2008-06-13
I have a question. Exactly how big does the boot partition have to be. I have to put a boot partition on my windows drive and it will only let my shrink it down 223 mb even thought there is 170gb free. Is 223mb enough?

---

### Post by adrian15 on 2008-06-14
> **devonharlan said:**
> I have a question. Exactly how big does the boot partition have to be. I have to put a boot partition on my windows drive and it will only let my shrink it down 223 mb even thought there is 170gb free. Is 223mb enough?

For most of the cases is enough, yes.

adrian15

---

