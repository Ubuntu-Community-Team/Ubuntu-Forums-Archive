---
title: "GRUB menu transferred from external HDD to the onboard SSD"
date: 2019-12-02
forum: General Help
---

### Post by ronaldmartin on 2019-12-02
I replaced my hard drive with a solid state drive, and then installed Ubuntu 19.10.

I hooked up to the old hard drive with a USB tether and deleted the partition table and formatted the entire drive.

Somehow the onboard SSD loaded the bootloader from the old hard drive, which had three Ubuntu 18.04 systems.

So when I start-up I get the GRUB menu for three systems.

The onboard 19.10 works, because the first partition aligns correctly.

I do not need the GRUB menu, because I only have one O/S on the machine.

How do I delete the erroneous Grub Menu?

---

### Post by crip720 on 2019-12-02
A simple sudo update-grub should fix grub menu.  Was the hard drive connected by USB when installing 19.10 to SSD, that should be only way for grub to pickup the old OSs.  Grub could be handy if a new updated kernel gets wonky in the future, or something else happens.

---

### Post by ronaldmartin on 2019-12-03
> **crip720 said:**
> A simple sudo update-grub should fix grub menu.

Thanks, it looks like that fixed it. I did not hook up the old hard drive until I received the tether a couple of weeks after I installed the SSD. So, somehow 19.10 read the old HDD efi partition and did it. I obviously, am not a programmer - just a novice that learns from the Internet when things go awry.

---

