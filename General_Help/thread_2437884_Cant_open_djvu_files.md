---
title: "Cant open djvu files"
date: 2020-03-02
forum: General Help
---

### Post by Dan_Bowser on 2020-03-02
Hello,

I can't open djuv files.

evince gives the error
```
Unable to open document &#8220;file:///home/daniel/Documents/MAT Winter 2020/Topics in Algebra/[Grundlehren der mathematischen Wissenschaften v. 322] Jürgen Neukirch, Norbert Schappacher - Algebraic number theory (1999, Springer).djvu&#8221;.
```

I also tried to in stall libdjvulibre21

```
libdjvulibre21 is already the newest version (3.5.27.1-8ubuntu0.1).
```

I don't know what's broken can someone explain it to me? I kind of need this book to work to finish my homework...

Ah, sorry I didn't copy the entire error,

```
Failed to load backend for 'image/vnd.djvu+multipage': libdjvulibre.so.21: cannot open shared object file: No such file or directory
```

---

### Post by monkeybrain20122 on 2020-03-03
I encountered this problem in Ubuntu 18.04 see this thread [https://ubuntuforums.org/showthread.php?t=2390953&page=2](https://ubuntuforums.org/showthread.php?t=2390953&page=2)
I managed to fix it, see post #11, but as I said it is still a mystery why this happened.

Also qpdfview works (I use it as my default document viewer in place of Evince aka document viewer) You can install it with the [ppa]("https://launchpad.net/~adamreichold/+archive/ubuntu/qpdfview-dailydeb") The version in the repo is old and maybe broken.

Cool book BTW. I never learned algebraic number theory. :)

---

