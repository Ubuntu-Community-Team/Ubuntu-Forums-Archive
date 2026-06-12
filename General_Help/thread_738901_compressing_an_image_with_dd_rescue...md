---
title: "compressing an image with dd_rescue.."
date: 2008-03-29
forum: General Help
---

### Post by Mia_tech on 2008-03-29
I've been able to create an image of my ubuntu box, but it takes lots of space on my network drive, I wonder if I can compress the image with dd_rescue, I've type help but I don't see anything related to compression
if someone can point me in the right direction

thanks

---

### Post by justleen on 2008-03-29
normally i  would compress it on the fly
```

dd if=/dev/sda1  | gzip > /mnt/sdb1/file.gzip 
```

you could just run tar/gzip over the image you have now, and when you need it, decompress it on the fly
```

gzip -dc /mnt/sdb1/file.gzip | dd of=/dev/sda1

```

---

### Post by Mia_tech on 2008-03-29
oh I know that, but I'm talking about dd_rescue which works a lot faster than dd

---

