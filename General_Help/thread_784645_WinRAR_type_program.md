---
title: "WinRAR type program"
date: 2008-05-06
forum: General Help
---

### Post by mcgooie on 2008-05-06
Just wondering if there is a program out there for ubuntu like WinRAR which can handle pretty much all types of files - zip, rar, img, iso, ccd etc....?

---

### Post by mikewhatever on 2008-05-06
Archive Manager, should be pre-installed. The package name is 'file-roller'.

---

### Post by gnivler on 2008-05-07
Unfortunately it doesn't seem to support all RAR archives, I suspect the newer versions.  Still researching a way to access them...  so far just using WinRAR and wine, but it's not particularly streamlined in my method.

Any suggestions would be appreciated!

xarchiver reports "the proper archiver is not installed!"
while file-roller reports "Archive type not supported."

---

### Post by edm1 on 2008-05-07
Just install the (non-free) package called 'unrar' in the repositories. It will integrate into the archive manager and give full support. Or kill two birds with one stone and install 'p7zip-rar'.

```
sudo apt-get install unrar
```

or

```
sudo apt-get install p7zip-rar
```

---

### Post by Monicker on 2008-05-07
> **gnivler said:**
> Unfortunately it doesn't seem to support all RAR archives, I suspect the newer versions.  Still researching a way to access them...  so far just using WinRAR and wine, but it's not particularly streamlined in my method.

Any suggestions would be appreciated!

xarchiver reports "the proper archiver is not installed!"
while file-roller reports "Archive type not supported."

Install these packages:

p7zip-full
p7zip-rar
[I]
Edit: late again!   :P[/I]

---

### Post by gnivler on 2008-05-07
Thanks a bunch to both of you.  I had already found the p7zip-full and -rar, and installed them via the package manager and was still having the errors I quoted earlier.  BUT - the unrar (not -free, didn't try it) package seems to have solved it, every rar I've tried has opened fine and passed the Test integrity check.

I think maybe the p7zip-rar supports the older rar format, there was a version milestone at some point where even WinRAR wouldn't open the new format/encoding... iirc it may have been version 3.  Unfortunately all the rar files I get are in the new format, so I'm very glad to have it working now!

---

### Post by ekss on 2008-05-09
> **edm1 said:**
> Just install the (non-free) package called 'unrar' in the repositories. It will integrate into the archive manager and give full support. Or kill two birds with one stone and install 'p7zip-rar'.

```
sudo apt-get install unrar
```

or

```
sudo apt-get install p7zip-rar
```



it works for me

---

