---
title: "How to preserve directory paths on backup CD/DVDs"
date: 2007-09-12
forum: General Help
---

### Post by howcome on 2007-09-12
I have a big file system where I store all my email, images etc. Here's a sample:

  /files/img/2007/08/...
  /files/img/2007/09/...
  /files/mail/2007/08/...
  /files/mail/2007/09/...

The direcories above store email and images from August and September this year. So far, so good.

The problem I'm trying to solve appear when I make backup CD/DVDs. I can't backup the whole /files/mail directory -- it's too big to fit on a DVD. I can fit /files/mail/2007 on a disc, but the backup programs I've seen add directories without preserving their place in the directory structure. If I make a disc with /files/mail/2007, I wouldn't be able to distinguish it from /files/img/2007 -- both would be called "2007".

Therefore, I would like a program that preserves the path names of directories. Perhaps not all the way from the top, but from some sensible starting point (/files in my case).

Ideally, mkisofs/growisofs would have an option to add a direcotory while preserving the directory path. I can't find it, though.

Help is much appreciated.

---

### Post by stinger30au on 2007-09-12
what are you using to backup wtih? have you tried Kdar backup?

---

### Post by howcome on 2007-09-12
At the moment I'm using mkisofs and growisofs. None of these have the option I'm looking for. At least, I havn't found them.

I've also tried k3b. 

I'm willing to switch to a new appliaction that provides this capability.

---

### Post by howcome on 2007-09-16
Research on kdar led me to 'dar' which I'm happily using now.

Thanks!

---

