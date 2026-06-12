---
title: "Simple man page problem"
date: 2017-09-06
forum: General Help
---

### Post by bil0w on 2017-09-06
Hello,

I have a simple man page problem, couldn't find out how to solve it. I am missing two man pages.

```
$ man 5 ar
No manual entry for ar in section 5
See 'man 7 undocumented' for help when manual pages are not available.
$ man 7 undocumented
No manual entry for undocumented in section 7
$

```

I tried to install manpages-dev, manpages-posix and resintall man-db but it does nothing.
MANPATH environment variable is empty.
All other man pages do work well.
locate undocumented.7.gz does throw nothing.

Could someone help me ?
Thank you

---

### Post by sudodus on 2017-09-06
Try

```
man ar
```

---

### Post by bil0w on 2017-09-06
I really need man 5 ar like here: [https://www.gsp.com/cgi-bin/man.cgi?section=5&topic=ar](https://www.gsp.com/cgi-bin/man.cgi?section=5&topic=ar)

I am developing ar utils, so I'd like archive file format explanations instead of the ar command usage.

And for the "man 7 documented" the error message is ironic

---

### Post by sudodus on 2017-09-06
Sorry, I cannot help you with that problem. I get the same error output (and I have no idea how to make it work, if/how it is supposed  to work).

Let us hope that somebody who knows will see your thread. Good luck :-)

---

### Post by Erik1984 on 2017-09-06
I never used the manpages like that, so new for me as well. But did find this: [https://unix.stackexchange.com/questions/293691/how-to-install-section-5-of-man-pages](https://unix.stackexchange.com/questions/293691/how-to-install-section-5-of-man-pages)

The package libarchive-dev installs the following section 5 manpages:
```

/usr/share/man/man5
/usr/share/man/man5/cpio.5.gz
/usr/share/man/man5/libarchive-formats.5.gz
/usr/share/man/man5/mtree.5.gz
/usr/share/man/man5/tar.5.gz

```

This should enable for example:
```
man 5 libarchive-formats
```

Still not this though:
```
man 5 ar
```

---

### Post by mc4man on 2017-09-06
That man was never written for linux

---

### Post by bil0w on 2017-09-07
Thanks a lot for your answers. I didn't knew about libarchive-formats, and as ar format was never really standardized it is possible that the page does simply not exist on linux.

Anyone has an idea for man 7 undocumented though ?

---

### Post by SeijiSensei on 2017-09-07
Google knows about man pages.  Searching for "man 5 ar" gave me this page from the FreeBSD manual: [https://www.freebsd.org/cgi/man.cgi?query=ar&sektion=5](https://www.freebsd.org/cgi/man.cgi?query=ar&sektion=5)

---

### Post by mc4man on 2017-09-07
never mind
(- there is a man(7) & man-pages(7) but likely not relevant.. unless it's just to point as to creating a man
[http://man7.org/linux/man-pages/man7/man.7.html](http://man7.org/linux/man-pages/man7/man.7.html)

---

### Post by cariboo on 2017-09-07
Does this help:

[https://www.freebsd.org/cgi/man.cgi?query=ar&sektion=5](https://www.freebsd.org/cgi/man.cgi?query=ar&sektion=5)

---

