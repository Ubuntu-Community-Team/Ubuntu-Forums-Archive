---
title: "Background picture not clear"
date: 2020-06-18
forum: General Help
---

### Post by satimis on 2020-06-18
Hi all,

Ubuntu 20.04 Gnome desktop
running on VM of VirtualBox

All background pictures are not clear.  Please refer to attached photo.

Kindly advise how to fix the problem.  Thanks

Regards

---

### Post by &amp;KyT$0P# on 2020-06-18
What version of VirtualBox?
If 6.0 or above, what type of graphics controller is this VM using?
Do you have 3D acceleration enabled or disabled for this VM?  Does toggling that setting make any difference?

---

### Post by sdsurfer on 2020-06-18
Looks like file corruption to me, can you locate the image and see if it opens in GIMP or some other image editor?

---

### Post by satimis on 2020-06-18
> **sdsurfer said:**
> Looks like file corruption to me, can you locate the image and see if it opens in GIMP or some other image editor?
The files are not corrupted.  They can be viewed with "Image Viewer" without problem

Regards

---

### Post by satimis on 2020-06-18
> **halogen2 said:**
> What version of VirtualBox?
If 6.0 or above, what type of graphics controller is this VM using?
Do you have 3D acceleration enabled or disabled for this VM?  Does toggling that setting make any difference?
Hi,

Version 6.0
Graphic Controller: VMSVGA
Acceleration [tick] Enable 3D Acceleration

All photos can be viewed on "Image Viewer" w/o problem but some of them corrupted when displayed as background image

Regards

---

### Post by satimis on 2020-06-18
Hi all,

Problem solved by [uncheck] Enable 3D Acceleration

Thanks

Regards

---

