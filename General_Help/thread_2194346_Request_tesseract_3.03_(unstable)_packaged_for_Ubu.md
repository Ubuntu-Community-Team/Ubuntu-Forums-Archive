---
title: "Request: tesseract 3.03 (unstable) packaged for Ubuntu"
date: 2013-12-17
forum: General Help
---

### Post by syntaxerror74 on 2013-12-17
Hi, although tesseract works damn well on Saucy here, there is an ugly bug in there when using *-psm 4* option which is reportedly not fixed yet in 3.02.01-* and -.02-*: 
[http://code.google.com/p/tesseract-ocr/issues/detail?id=653](http://code.google.com/p/tesseract-ocr/issues/detail?id=653)

So my question is: has anybody packaged a 3.03+ version for Ubuntu yet? Thought I might find something on PPA, but no...

---

### Post by ian-weisser on 2013-12-17
Apparently not.

```
$ rmadison -u [COLOR=#ff0000]ubuntu[/COLOR] tesseract-ocr
 tesseract-ocr | 2.04-2    | lucid/universe   | amd64, armel, i386, ia64, powerpc, sparc
 tesseract-ocr | 3.02.01-2 | precise/universe | amd64, armel, armhf, i386, powerpc
 tesseract-ocr | 3.02.01-6 | quantal/universe | amd64, armel, armhf, i386, powerpc
 tesseract-ocr | 3.02.02-1 | raring/universe  | amd64, armhf, i386, powerpc
 tesseract-ocr | 3.02.02-1 | saucy/universe   | amd64, armhf, i386, powerpc
 tesseract-ocr | 3.02.02-1 | trusty/universe  | amd64, armhf, i386, powerpc


$ rmadison -u [COLOR=#ff0000]debian[/COLOR] tesseract-ocr
 tesseract-ocr | 2.04-2+squeeze1 | squeeze | amd64, armel, i386, ia64, kfreebsd-amd64, kfreebsd-i386, mips, mipsel, powerpc, s390, sparc
 tesseract-ocr | 3.02.01-6       | wheezy  | amd64, armel, armhf, i386, ia64, kfreebsd-amd64, kfreebsd-i386, mips, mipsel, powerpc, s390, s390x, sparc
 tesseract-ocr | 3.02.02-1       | jessie  | amd64, armel, armhf, i386, ia64, kfreebsd-amd64, kfreebsd-i386, mips, mipsel, powerpc, s390x, sparc
 tesseract-ocr | 3.02.02-1       | sid     | amd64, armel, armhf, hurd-i386, i386, ia64, kfreebsd-amd64, kfreebsd-i386, mips, mipsel, powerpc, s390x, sparc
```

---

### Post by syntaxerror74 on 2013-12-17
Thanks for the printout! Never knew this tool before, it's way handier than always combining apt-cache and grep!

---

