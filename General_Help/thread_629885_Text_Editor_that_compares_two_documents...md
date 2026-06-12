---
title: "Text Editor that compares two documents.."
date: 2007-12-02
forum: General Help
---

### Post by kyleabaker on 2007-12-02
I'm trying to find a good programming text editor in Ubuntu and have been using SciTE for a while, however, it has a few things about it that I find to be very annoying. I always have to select "all files" when opening and browsing from php files to edit, etc. Also, it seems to lack a lot of common features that are present in several windows text editors I used a while back.

Is there a good text editor available that can also compare two documents for differences? I really need this as I'm constantly doing debugging work and it helps to pin point problems. Thanks.

---

### Post by dagnabit dang doohickey on 2007-12-02
You can always use diff to compare files:
```
diff -s file1 file2
```

As far as text editors go, I'd recommend taking a look at [Geany]("http://geany.uvena.de/"). It doesn't have a built-in file compare, but is otherwise a very good text editor.

---

### Post by drs305 on 2007-12-02
I've recently switched from gedit to cream, which is a variant of vim. It has a DIFF mode.  I haven't used it but here is a screenshot of how the DIFF mode looks:
[http://cream.sourceforge.net/screenshot2.html](http://cream.sourceforge.net/screenshot2.html)

Cream is in the universe repository.

---

### Post by niteshifter on 2007-12-03
emacs and xemacs are in the repositories. Either will let you compare 2 or 3 buffers / files / directories, or regions of text word by word or line by line. 

Of the two xemacs is probably the "easiest" to use, the emacs is an X11 version and it's GUI effects take a bit of getting used to.

---

### Post by hugmenot on 2007-12-03
Meld is a newish GTK diff tool

---

