---
title: "Comparing two directories"
date: 2007-09-14
forum: General Help
---

### Post by Glenn Jones on 2007-09-14
Hi there,

I have a number of directories which I work in which have the same source code but have different inputs. I've decided to put the source code in 1 directory so that I don't have multiple copies of it. The plan is to delete the multiple copies of the source code in my working directories so that it they will only hold the input generating code there. However due to my naming convention I don't know which is my code and which is the source code in these working directories . 

Is there a way of checking both the source code directory and my working directories and deleting the multiple copies of the source code so that only input generating code there?

Cheers

---

### Post by yota on 2007-09-14
This can help:
> 
FDUPES(1)                                                                                                                                                     FDUPES(1)

NAME
       fdupes - finds duplicate files in a given set of directories

SYNOPSIS
       fdupes [ options ] DIRECTORY ...

DESCRIPTION
       Searches the given path for duplicate files. Such files are found by comparing file sizes and MD5 signatures, followed by a byte-by-byte comparison.



---

### Post by Glenn Jones on 2007-09-17
Thanks for that fdupes is great

---

