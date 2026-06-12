---
title: "Creating bootable ISO image for Files/Folders.."
date: 2016-01-20
forum: General Help
---

### Post by latha2 on 2016-01-20
Hello all,
I want my 8Gb folder to boot able ISO image .. I tried xfburn,acetone iso,k3b but i didn't get bootable iso which in turn created just iso image file and
I  also tried clone zilla but it's for whole system (OS) image which is not necessary for me right now..
could anyone please help me out 
Thank you !

---

### Post by ajgreeny on 2016-01-20
Sorry, but can you explain in more detail what you are trying to do as it does not make complete sense to me.

Do you want a bootable iso image of your current install within that 8GB space, which is probably not a folder but a partition?
Have you investigated **mkisofs** which may be able to do what you want; I have no experience of this but it may help you. This is part of the genisoimage package which is in the repos.

have a look at [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) which may help you sort out what you want.

---

### Post by grahammechanical on 2016-01-20
A iso image file is a kind of archive. For an iso image file to be bootable the image would need to include a boot loader. And for data in the image to be accessible there would also need to be an OS and applications to access the data files all included in the iso image.

This is what we have in a Ubuntu iso image.

There may be other ways of achieving what you want. Apart form wanting to create a bootable iso image out of a 8 GB data folder, what do you really want to achieve? Do you want something like a disk full of data that when inserted into the drive will automatically load a web browser or PDF reader to access the data on the disc? Something like that?

Regards.

---

### Post by latha2 on 2016-01-21
First of all thank you for your help towards this...
I downloaded linux-4.4 to which I patched RTpatch-4.4 which means I patched my linux-4.4
I got assigned a work to represent the same in virtual box so I thought to create an bootable ISO image for that folder which is of 8GB (linux-4.4-patched) .Ultimately in virtualbox I can boot image like general OS..
I do not know is this possible but trying my way to complete the task..
I hope you could help me out 
Thank you in advance.

---

### Post by sudodus on 2016-01-21
If your system is based on Ubuntu (standard Ubuntu, Kubuntu ... Xubuntu, Linux Mint or a community re-spin based on Ubuntu), one solution might be to use the [One Button Installer](https://help.ubuntu.com/community/OBI) and create a tarball of your system (which I guess is located in a 8 GB partition).

Then you can create a system from the tarball into an external drive (for example a USB pendrive), and it would be possible to boot computers from that USB pendrive and run your system with a patched linux-4.4 kernel.

If necessary, it would be possible to clone from the USB pendrive to a virtual drive in VirtualBox, and then you can boot your system in VirtualBox.

---

