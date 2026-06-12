---
title: "Can't compress large files"
date: 2013-02-02
forum: General Help
---

### Post by Hungry Man on 2013-02-02
I've tried compressing large files with rar and 7z but neither will work. I can compress a small file, a few MB, just fine. But when I try to compress a large 799MB video file it gets partway and then just stops - it sits there. The process isn't hung, it's just the progress bar not moving.

Ideas?

I have plenty of disk space, plenty of processing power, etc.

---

### Post by SeijiSensei on 2013-02-02
Most video files are already compressed.  You won't see much improvement using something like zip.

As a test, try using gzip on the file:

```
gzip /path/to/file
```

If that works, do you see much reduction in size?

---

### Post by Hungry Man on 2013-02-02
Reduction in size isn't the goal. Passwording the files is.

Gzip doesn't seem to be working either. Just sits there.

---

### Post by sudodus on 2013-02-02
Are you writing to external media (for example a USB pendrive)? That is slow, and the computer seems to just sit there, while writing to the media.

Or is your system swapping, when you compress such a big file? Swapping makes it very slow. You can check this with the command ```
top
```

I have compressed images of several tens of gigabytes with gzip, so I know it is possible.

But there are alternatives.

- Try gpg! Read ```
man gpg
``` there are examples near the end of the manual.

- Or try to compress the file booted from a live Ubuntu CD or USB drive! This should work if the problem is that something is wrong with your installed system.

---

### Post by Lars Noodén on 2013-02-02
+1 for gpg.  If you are just trying to encrypt the file with a password, then that is what you need.

---

### Post by dcstar on 2013-02-04
> **Hungry Man said:**
> I've tried compressing large files with rar and 7z but neither will work. I can compress a small file, a few MB, just fine. But when I try to compress a large 799MB video file it gets partway and then just stops - it sits there. The process isn't hung, it's just the progress bar not moving.

Ideas?

I have plenty of disk space, plenty of processing power, etc.

Are you **100% sure** your /tmp folder has sufficient free space (at least the size of the file)?

---

