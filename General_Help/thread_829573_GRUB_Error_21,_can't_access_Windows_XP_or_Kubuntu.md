---
title: "GRUB Error 21, can't access Windows XP or Kubuntu"
date: 2008-06-14
forum: General Help
---

### Post by beidandy on 2008-06-14
I installed Kubuntu on a partition on my external 500gb HD, using the installer to partition. I have Windows XP on my internal hard drive. My family decided they didn't like Kubuntu, so they wait til the GRUB loader to select Windows XP. I don't know what happened, but now, I can't even access the GRUB loader with the list of OSes! It always says GRUB Error 21. Please help on how I can uninstall Kubuntu & restore the external hard drive (no more partition) and how I can access Windows XP by default again.

Sorry if someone has posted something like this before, it's an emergency and I hope you can help.

---

### Post by meierfra. on 2008-06-14
[Herman's Uninstall Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by sam_delta on 2008-06-15
get a supergrub disk, burn it / or copy the image to a diskete and restore your grub
[www.supergrubdisk.org](www.supergrubdisk.org)

sam

---

### Post by pb_online on 2008-06-15
With a Linux Live CD you can install "testdisk"

sudo apt-get install testdisk

then type...

sudo testdisk

You can write new MBR and make partitions bootable.

---

