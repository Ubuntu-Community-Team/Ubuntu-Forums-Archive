---
title: "Permission denied PDF Doc viewer"
date: 2012-12-29
forum: General Help
---

### Post by Simoo on 2012-12-29
Hi,

Quite a strange one this.

I download a PDF to the Downloads dir and everything works fine, documnent viewer opens it up.

However, I copy it to a different dir (which is actually an NFS share) and the Document viewer says 'Permission Denied' even though:

```
$ ls -l
-rw-rw-r-- 1 simon simon 735679 Dec 29 17:43 viewTaxReturnPdf
```

It should be fine.

I also tried the same thing with another downloadable PDF and there was no problem.

Any ideas why that might be?

---

### Post by mJayk on 2012-12-29
Could it be a DRM problem?

---

### Post by Simoo on 2012-12-29
I guess it's possible...

I can move the file around the local drive fine but experience the same issue if I try to copy it to a memory stick.

That would mean the file must some how 'know' which drive it was downloaded too.

---

### Post by mJayk on 2012-12-29
I think (think being the word I don't know) thats how DRM works it contains a little file that has the HDD id and maybe location?

---

### Post by Simoo on 2012-12-29
It think you're right. I previously thought that any form of DRM would render the PDF completely unreadable in a generic Linux PDF reader.

It seems a bit stupid though, how am I supposed to keep a digital copy of my tax return.... DRM.. sheesh...

I guess a screen-shot will do it!

---

