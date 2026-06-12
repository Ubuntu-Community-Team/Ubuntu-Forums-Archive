---
title: "Grub boot sequence?"
date: 2007-01-16
forum: General Help
---

### Post by McBlue on 2007-01-16
Hi again Guys. I’m trying to do a graphic that shows the flow of the boot process when Grub is installed to the MBR and is configured to boot Windows.
[http://www.multibooters.co.uk/images/grub.png](http://www.multibooters.co.uk/images/grub.png)

As I understand it, part of Grub goes to the MBR and replaces the Windows bootcode in the MBR (the Initial Program Loader) Now this part of Grub is always set to boot the Linux partition, from where the main part of Grub will then jump to the PBR (Partition Boot Record) of the Windows OS you choose from the Grub boot menu.

Now the thing I don’t know is - does the MBR part of Grub start the PBR of the Linux partition, which then starts the main part of Grub on the partition. Or does the MBR part jump straight to the main part of Grub on the partition, actually by-passing the PBR of the Linux partition?

My graphic shows the PBR is used. Does anyone know if this is correct or not? Also, does Lilo differ from Grub at all in this area?

Thanks.

---

