---
title: "can't install imagemagick"
date: 2005-08-18
forum: General Help
---

### Post by gradedcheese on 2005-08-18
Hello.  I really need imagemagick but i cannot seem to install it.  apt tells me:

```
imagemagick:
  Depends: libmagick6 (=6:6.0.6.2-2.1ubuntu1) but 6:6.0.6.2-2.1ubuntu1.1 is to be installed

```

Is there a way to resolve this easily?  Thanks!

---

### Post by gradedcheese on 2005-08-18
ah, I solved it!  FYI, in my case I needed it for php4-imagick, which was already installed somehow.  I removed libmagick (which removed php-imagick) and then added everything again, this time doing imagemagick first, which allowedit to install.

---

