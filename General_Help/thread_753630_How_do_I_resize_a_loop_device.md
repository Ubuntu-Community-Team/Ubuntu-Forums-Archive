---
title: "How do I resize a loop device?"
date: 2008-04-12
forum: General Help
---

### Post by Ice_Dragon on 2008-04-12
I downloaded a file that's an ext2 loop device.  I want to add a some files to it, but there's no space available.  Is there a way to resize it without making a whole new file?

---

### Post by SorryGoFish on 2008-04-12
It's my understanding that a loop device is an image (for example if you mount a CD image (iso) it's a loop device). As an image, it can not be modified by definition. You'd have to copy the contents out, like copying off a CD, then make changes and re-package the contents. [http://en.wikipedia.org/wiki/Loop_device]("http://en.wikipedia.org/wiki/Loop_device")

---

### Post by Ice_Dragon on 2008-04-13
I know it's used for CD images, but in this case it's meant to be a file system packed inside a file.  The files are editable, there just isn't any room to add more.

---

### Post by bingoUV on 2008-04-13
Yes, your case is not hopeless. Backup your image, and then do the following to resize it to e.g. 2GB. Unmount it before doing this. You do not need to be root to use the following resize2fs command.
```

resize2fs /path/to/image/file 2G

```

To test whether it worked, now mount it, write more data than the initial size could hold, an unmount it. See the size of the image file now.

---

### Post by Ice_Dragon on 2008-04-13
> **bingoUV said:**
> Yes, your case is not hopeless. Backup your image, and then do the following to resize it to e.g. 2GB. Unmount it before doing this. You do not need to be root to use the following resize2fs command.
```

resize2fs /path/to/image/file 2G

```

To test whether it worked, now mount it, write more data than the initial size could hold, an unmount it. See the size of the image file now.

That worked great.  Thank you very much. :)

---

