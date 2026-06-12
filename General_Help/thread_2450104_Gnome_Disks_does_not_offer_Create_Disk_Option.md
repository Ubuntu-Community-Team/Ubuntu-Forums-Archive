---
title: "Gnome Disks does not offer Create Disk Option"
date: 2020-09-07
forum: General Help
---

### Post by Dave_Davis on 2020-09-07
I have read several places that Gnome Disks can be used to create a disk image.

When I try to do so I am presented with an option to create a partition image but not one to create a Disk Image.

Where am I going wrong?

Thanks

---

### Post by SeijiSensei on 2020-09-07
You want to create an image of a disk with multiple partitions?  I'd use dd:
```
dd if=/dev/sdX of=disk.img
```
would create an image of a device like /dev/sda and write it as a file called disk.img in the current directory.

---

### Post by speartip on 2020-09-07
Disks can indeed create disk images.
Assuming you're using a USB. Plug it in, open Gnome Disks, highlight your USB in the left panel, click the 3 bars near the top right corner of Disks, choose "Restore Disk Image", then navigate to the .iso you want, & click "Start Restoring".

---

### Post by Dave_Davis on 2020-09-08
Problem solved.

My problem was the Gnome Disks no longer has a "gear" icon on the title bar.  I has three vertical dots.

The post I was reading said to click on the "gear" icon and the only gear icon was on dialog for each partition.

---

