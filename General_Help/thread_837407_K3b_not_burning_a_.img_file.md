---
title: "K3b not burning a .img file"
date: 2008-06-22
forum: General Help
---

### Post by Gargleman on 2008-06-22
I am trying to burn a .img to a blank dvd, and whenever I try to pull the file up in K3b, I get a file type invalid. I have also tried renaming it to a .iso and I get the same error.

---

### Post by Vivaldi Gloria on 2008-06-22
> **Gargleman said:**
> I am trying to burn a .img to a blank dvd, and whenever I try to pull the file up in K3b, I get a file type invalid. I have also tried renaming it to a .iso and I get the same error.

Install ccd2iso program using synaptic. Then convert the .img file to a .iso file using the command

```
ccd2iso input.img output.iso
```

---

