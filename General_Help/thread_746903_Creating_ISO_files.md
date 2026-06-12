---
title: "Creating ISO files"
date: 2008-04-06
forum: General Help
---

### Post by snoguy986 on 2008-04-06
So I want to back up some data DVDs and CDs that I have into .iso, but I don't know of a good program on linux that can easily create them.  Can anyone help me out?  Thanks.

---

### Post by Gen2ly on 2008-04-06
MasterISO can do this for a GUI app, though dd is the champ:

```
dd if=/dev/dvd of=name.iso
```

**Note:** replacing "/dev/dvd" with your device may be necessary.

Also creating iso from directories can be done by:

```
mkisofs -o name.iso /path/to/file_or_directory
```

---

