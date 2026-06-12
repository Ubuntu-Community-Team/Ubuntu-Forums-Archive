---
title: "Problem with UCK not finding .iso file"
date: 2016-10-18
forum: General Help
---

### Post by antaris2 on 2016-10-18
I've been trying to create a distribution with Ubuntu Customization Kit following the instructions : [https://peteris.rocks/blog/customize-ubuntu-desktop-live-cd-usb/](https://peteris.rocks/blog/customize-ubuntu-desktop-live-cd-usb/)
Whenever I try to do 
sudo uck-remaster-unpack-iso isoname

I get this error:

sudo uck-remaster-unpack-iso ubuntu-mate-16.04.1-desktop-i386.iso
Mounting ISO image...
mount: ubuntu-mate-16.04.1-desktop-i386.iso: failed to setup loop device: No such file or directory
Cannot mount ubuntu-mate-16.04.1-desktop-i386.iso in /home/erika/tmp/remaster-iso-mount, error=32

The ubuntu-mate-16.04.1-desktop-i386.iso file is in my Downloads.
Any ideas on whats going wrong and how to fix this problem?
Thanks in advance!

---

### Post by &amp;KyT$0P# on 2016-10-18
If I understand correctly, UCK is dead -
[https://sourceforge.net/projects/uck/](https://sourceforge.net/projects/uck/)
> !!!PROJECT DISCONTINUED!!!
And last release is from January 2013.

[This instructions]("https://help.ubuntu.com/community/LiveCDCustomization#System_Requirements") does work.

---

