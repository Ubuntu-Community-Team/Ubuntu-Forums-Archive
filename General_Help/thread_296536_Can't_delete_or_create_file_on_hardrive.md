---
title: "Can't delete or create file on hardrive"
date: 2006-11-09
forum: General Help
---

### Post by Mooseus on 2006-11-09
Hey everyone,

I have a portable hard drive but I can't seem to add files to it or delete them when I'm using Ubuntu. It believes that the hard drive is read only. So I went into the permissions to try and change it but it still believed it was a read only file. The drive works on my windows computers but not Ubuntu. I can copy things off of the drive but I just can't place things onto it. Anyone know what the problem is?

---

### Post by kidders on 2006-11-09
Is your filesystem mounted in read-only mode, or perhaps with unsuitable permissions maps (in the case of FAT filesystem, that don't support the idea of permissions). What filesystem are you using?

---

### Post by Mooseus on 2006-12-22
I believe the hard drive is an NTSC file system. How would I change the filesystem from mounting in read-only modes?

---

### Post by kidders on 2006-12-22
Perhaps you mean NTFS? (NTSC is a video standard.) If so, I wouldn't recommend mounting it in read/write mode, unless you're pretty familiar with its inner workings ... you'd need some filesystem recovery experience if something were to go wrong!

---

