---
title: "mkisofs don't use -z flags on hardy"
date: 2008-05-06
forum: General Help
---

### Post by bip91 on 2008-05-06
Dear,

i'd like to build a live CD archive (i have very big mail folders which i want to acces from time to time from a CD).
Thunderbird folders contain mostly text, so compression option from rockridge format seems to be a good solution... But it won't compress on my Hardy system :

A example :
>ls -l
-rw-rw-rw-   1 root root 150824347 2006-01-03 16:13 foo

>  mkisofs -r -z -o /tmp/bar.iso foo
Warning: using transparent compression. This is a nonstandard Rock Ridge
         extension. The resulting filesystem can only be transparently
         read on Linux. On other operating systems you need to call
         mkzftree by hand to decompress the files.
  6.77% done, estimate finish Tue May  6 10:04:35 2008
   .....
Total translation table size: 0
Total rockridge attributes bytes: 245
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 0
73820 extents written (144 MB)

> ls -l
-rw-rw-rw-  1 root root  151183360 2008-05-06 10:04 bar.iso

Result and input files have quite the same size.
With a simple gzip, i get 77 Mo which is better result

A idea ? do i forget a flag ?  some others tools are better ?
thanks,
bip

---

