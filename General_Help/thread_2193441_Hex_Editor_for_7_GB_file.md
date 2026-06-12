---
title: "Hex Editor for 7 GB file"
date: 2013-12-12
forum: General Help
---

### Post by Resistent on 2013-12-12
Hi all,

I have a 7 GB file, which was deleted in Windows, then recovered.
I want to open it somehow, view Hex level, so I can find out what is it.
Is there a Hex editor, which can handle such huge files, or just open a
portion of it?



thx

---

### Post by steeldriver on 2013-12-12
You could use a command-line utility such as od and give it a specific number of bytes to load e.g.

```
od **-N 1024** -tx1 *yourfile*
```

You can also skip bytes using -j if you want to examine particular portions of the file.

You may also find the 'file' utility useful - it will try to identify the file type based on magic bytes

```
**file ***yourfile*
```

---

### Post by Resistent on 2013-12-15
thank you !

---

### Post by efflandt on 2013-12-16
**ghex** is a gui hex editor that shows both hex and ascii side by side. It does not mention any size limitation.

---

