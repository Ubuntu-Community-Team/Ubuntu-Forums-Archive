---
title: "Place filesystem.squashfs inside initrd.gz for PXE boot?"
date: 2012-10-20
forum: General Help
---

### Post by Patrick Verner on 2012-10-20
I know you can boot the livecd with other methods. I was wondering if you can put the filesystem.squashfs inside the initrd.gz and somehow make it find the squashfs.

Parted Magic PXE does it this way and I would like Ubuntu livecd to do the same thing. Parted Magic does it by putting the squashfs in the / of the initrd. You can do the same thing with the Gentoo livecd with some more tinkering.

Like this: [http://www.j-schmitz.net/blog/how-to-boot-a-gentoo-livecd-via-pxe](http://www.j-schmitz.net/blog/how-to-boot-a-gentoo-livecd-via-pxe)

Is it possible to get the Ubuntu livecd to do this?

---

### Post by Patrick Verner on 2012-10-20
I've been trying to do this most of the day and within a 1/2 hour of posting this I figured it out. :P

---

### Post by johannesa on 2012-10-24
Would you mind to share your experience? Thank you.

---

