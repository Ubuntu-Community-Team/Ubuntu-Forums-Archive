---
title: "Any way to mount a bzipped disk image?"
date: 2007-10-10
forum: General Help
---

### Post by katoodifaas on 2007-10-10
Hi,

I made a low-level backup of my entire Windows disk and piped it through bzip with

```
dd if=/dev/sda | bzip2 > img.bz2
```

I'm wondering if there's any way to mount the NTFS partition in the compressed image if I just want to restore a few specific files - I can't uncompress it because there's no space. But if that's not possible, is it possible to even mount the *uncompressed* raw disk image? Any help is appreciated.

---

