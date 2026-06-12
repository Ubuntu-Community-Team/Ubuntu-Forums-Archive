---
title: "file comparison"
date: 2007-03-18
forum: General Help
---

### Post by zorkerz on 2007-03-18
I am trying to find a program that compares the contents of two files.  I would be using this for text files.  All i am looking for is a way to see what is different between two text files without needing to read them both line for line.  There must be some way to do this.
Thankya
i guess if worse comes to worse i could always use wikipedia's wiki program which has a good method for doing this.

---

### Post by colo on 2007-03-18
You'd want to check the inodes' recorded length in bytes first - if they don't match, the files by definition cannot be identical bit-wise. As comparing byte for byte may prove tiresome to implement (2 threads for reading, probably with some nifty synchronisation mechanism), you should just resort to some kind of hashing algorith (crc32, md4, md5, sha1...), and compare the calculated checksums. There's a ton of library functions in right about any language you can dream of for that kind of work, and there are CLI apps, too.

Hth.

---

### Post by zorkerz on 2007-03-18
Im thinking more. for situations where I know the files are different I just don't know every place where they are.

---

### Post by Mr. C. on 2007-03-18
man diff

---

### Post by zorkerz on 2007-03-18
wonderful

---

### Post by ardchoille42 on 2007-03-18
If you want a gui way to do it:
```

sudo apt-get install meld

```

---

### Post by Qew on 2007-03-18
You can also use vimdiff for this kind of thing, which will allow you to edit either file, if you so choose.

---

### Post by zorkerz on 2007-03-18
imy trying out meld where can i get vimdiff does not seem to be in the repositories unless i missed itsomehow.

---

### Post by Qew on 2007-03-18
install vim-common. You'll then be able to use vimdiff in a console/xterm: vimdiff file1 file2

---

### Post by szako on 2008-07-24
Thanks for the meld tip ;)

---

