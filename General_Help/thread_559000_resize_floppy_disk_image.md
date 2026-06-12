---
title: "resize floppy disk image?"
date: 2007-09-24
forum: General Help
---

### Post by maybeway36 on 2007-09-24
I am trying to use ISOLINUX and MEMDISK to boot DOS floppy images. Unfortunately, some images are in 720KB format and some in 1.44MB. To make matters worse, they are not the standard sizes; most are sizes like 252KB or 198KB. Is there a way I can use either Linux or DOS to convert and resize these images?

---

### Post by tszanon on 2007-09-27
> **maybeway36 said:**
> I am trying to use ISOLINUX and MEMDISK to boot DOS floppy images. Unfortunately, some images are in 720KB format and some in 1.44MB. To make matters worse, they are not the standard sizes; most are sizes like 252KB or 198KB. Is there a way I can use either Linux or DOS to convert and resize these images?
I don't think the image size matters, because it reflects what's inside the image. If you create a cd image with only one file in it, the image will have about the same size of that file it contains, not 650/700 MB. I think that no resize is needed.

---

