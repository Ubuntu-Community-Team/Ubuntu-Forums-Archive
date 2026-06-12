---
title: "File Managers Image Thumbnails Mixed up"
date: 2013-01-16
forum: General Help
---

### Post by texpat on 2013-01-16
Somehow the thumbnails of a bunch of JPEG images shown in the file manager got mixed up and now the images shown as thumbnails do not correspond to the actual image in that file.

I get the same problem with gThumb where the thumbnail shown in the bottom row isn't of the picture in the file shown in the main panel.

I'm on Xubuntu 12.04. I've tried Thunar, Nautilus and PCmanFM and all three have the same problem. I'm at a total loss as to what could have caused this or how to correct it. I've got to manage and maintain hundreds of images and this is causing me a major headache, so any pointers are greatly appreciated.

Thanks

---

### Post by LewisTM on 2013-01-16
You can try to delete the cached thumbnails. They will be regenerated when you visit the folders again.
```
rm -rf ~/.thumbnails ~/.cache/thumbnails
```

Cheers!

---

### Post by texpat on 2013-01-16
Looks like that did it. Thanks a lot!

---

