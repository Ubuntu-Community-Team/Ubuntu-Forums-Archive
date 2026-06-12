---
title: "Migrating data from SSD to HDD, part 2"
date: 2013-04-09
forum: General Help
---

### Post by Calinou on 2013-04-09
I have an HDD formatted using MBR, I'd like to migrate its / and /home partitions to the SSD (which will probably use GPT to align partitions) then edit the /etc/fstab so that it boots properly on the SSD.
I also have an unused /boot/efi partition on the HDD (since I used MBR and not GPT, due to Ubiquity), which I won't use on the SSD.
How can I do this, without reinstalling if possible?

---

### Post by oldfred on 2013-04-09
Grub will boot in BIOS mode from gpt partitioned drive on SSD as that is what I do. You do need a small 1MB unformatted partition with bios_grub flag. Then grub installs correctly.
I do not understand efi partition on MBR drive. Or is that just not used? UEFI boots from efi partition on gpt partitioned drives.

While you may be able to copy / & /home to new partitions, and reset fstab with new UUIDs and reinstall grub, I prefer copy just /home and reinstall using the existing (new) /home.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
It would be similar commands to copy / also. Just be sure to include the parameters that preserve ownership and permissions & all hidden files.

---

