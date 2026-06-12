---
title: "Xubuntu wont recognise cf ide drive?"
date: 2008-06-05
forum: General Help
---

### Post by shreaded_teddy on 2008-06-05
I've got an old 400mhz desktop that i'm trying to set up as a home server using this guide [http://www.techenclave.com/guides-and-tutorials/how-build-low-cost-linux-home-102018.html](http://www.techenclave.com/guides-and-tutorials/how-build-low-cost-linux-home-102018.html).  so far I've tried ubuntu server, xubuntu live & alternate, and none of them will install.  the motherboard is an old ali aladdin V with an amdk6-2 processor and the 2Gb flash card is connected with this [http://www.newegg.com/Product/Product.aspx?Item=N82E16822998003](http://www.newegg.com/Product/Product.aspx?Item=N82E16822998003) syba cf to ide adapter.  i got windows xp to install & boot no problem but the alternate cd is the only distro that would even start the install.  in the beginning it gives a message about forcing ACPI because it's older than 2000 (1999) and works fine until it gets to the partitioner thing. this is where it fails to recognize the hdd and asks me which drivers i want to use?  i tried the "ide-general" and "ide-disk" from the huge list but neither one worked and didn't want to go through the entire list.  syba says the product supports linux and doesn't offer any downloads in their support section.  i also tried messing with what ever i could in the bios but no luck there either.  I'm stumped, any suggestions?

i know 2gb isn't enough storage space for a server, I've got an external 500Gb hdd i plan to use.

---

### Post by Baelus on 2008-06-05
I have an older machine that did not like ubuntu at all. It's an old Compaq Presario 2292. I remember things got hung up when the partitioner started too. Plus, it also used the AMDk6-2 processor, which may or may not be a part of the problem.

It's working great today, though. Guess what, it likes Debian. I'm running Etch and it's been fine. Your Ubuntu knowledge will absolutely translate to Debian.

You can also try [Damn Small Linux]("http://www.damnsmalllinux.org/") or [Feather Linux]("http://featherlinux.berlios.de/"), both light distro's, just to see if linux likes the whole CF card setup (fdisk -l, mounting, etc).

- B

---

