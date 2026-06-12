---
title: "deleted files"
date: 2007-12-25
forum: General Help
---

### Post by Luke111 on 2007-12-25
Are files actually deleted from the disk or just renamed? If they aren't actually deleted then is there a program that will wipe files in Linux?

---

### Post by Sef on 2007-12-25
> re files actually deleted from the disk or just renamed?

The link to the files is removed.   The computer does not know where the files are any more.

> f they aren't actually deleted then is there a program that will wipe files in Linux?

Yes there is - [DBAN]("http://dban.sourceforge.net/").

---

### Post by Luke111 on 2007-12-26
Ok, thanks. I'll check it out.

---

### Post by heindsight on 2007-12-26
As far as I know DBAN is intended to securely delete an entire hard disk, not just individual files.
If you're looking for something to securely delete individual files, you can use shred, which is
installed on Ubuntu by default as part of the coreutils package. For details on how to use it, try
```
man shred
``` and for even more details, have  look at the info pages for shred:
```
info coreutils shred
```

---

### Post by Luke111 on 2007-12-27
Yeah, shred is what I was looking for. Thanks.

---

