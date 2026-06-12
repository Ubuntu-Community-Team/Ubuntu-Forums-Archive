---
title: "Finding a File"
date: 2014-08-16
forum: General Help
---

### Post by daniell59 on 2014-08-16
Please forgive me if this is an inane question. I googled it, but could not understand how to do it.
I just created an ISO of a CD. I cannot locate it. How do I search for it?

Ubuntu 12.4 64

Thanks

---

### Post by thnewguy on 2014-08-16
Assuming you know what you called the image file (my-cd.iso, perhaps?) you can either use the find or the locate utilities.

locate my-cd.iso
or
find ~ -iname my-cd.iso

---

### Post by daniell59 on 2014-08-16
> **thnewguy said:**
> Assuming you know what you called the image file (my-cd.iso, perhaps?) you can either use the find or the locate utilities.

locate my-cd.iso
or
find ~ -iname my-cd.iso

I could not locate "find"?

---

### Post by daniell59 on 2014-08-16
I am somewhat confused. My file is iso.com but I cannot find it. Any assistance will be appreciated.

---

### Post by ubudog on 2014-08-16
Have you tried running the command:
```
find ~ -iname my-cd.iso
```

by itself?

---

### Post by daniell59 on 2014-08-16
Thanks, I found it in the home folder.

---

