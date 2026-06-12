---
title: "a directory full of .zip archives - can I uncompress them with a single CLI command?"
date: 2007-01-20
forum: General Help
---

### Post by ajm2005 on 2007-01-20
to unzip a single file, it is:

**unzip file**

or

**unzip file.zip**

I assumed to unzip every zip archive in a directory it would be:

**unzip *.zip**

but this gives an error message. ](*,)

---

### Post by kerry_s on 2007-01-20
-> [http://www.nada.kth.se/cgi-bin/man?p=unzip&M=/pkg/gnu-pack/1.0/man/&f=y](http://www.nada.kth.se/cgi-bin/man?p=unzip&M=/pkg/gnu-pack/1.0/man/&f=y)

Here's the man page, it looks like it's "  unzip \*.zip  "

---

### Post by vidak on 2007-01-20
> **ajm2005 said:**
> to unzip a single file, it is:

**unzip file**

or

**unzip file.zip**

I assumed to unzip every zip archive in a directory it would be:

**unzip *.zip**

but this gives an error message. ](*,)

in the worst case you could still do it with a for-loop:

for i in `ls *.zip`; do echo $i; unzip $i; done

---

### Post by david_2001 on 2007-01-20
An alternative way of unzipping all of the .zip files in the current directory would be to use find:
```
find . -name "*.zip" -exec unzip '{}' \;
```
(Be aware that find also searches subdirectories.)

---

### Post by ajm2005 on 2007-01-20
thank you all for your responses!  =D> 

(How interesting there are so many ways of doing it, altho for simplicity I went with the first suggesation)

---

