---
title: "gcc not able to link against archives"
date: 2008-02-15
forum: General Help
---

### Post by akwatve on 2008-02-15
I know this may not be the ideal forum for this question ... But I did not get any help from anywhere else so trying my luck.

I am using g++ to compile some cpp files.
When I used
```
g++ a.o b.o c.o  foo.cpp
```
Everything works fine. code gets compiled.
But If I create an archive file using :
```
ar -rc common.a  a.o b.o c.o 
``` and then use```
g++ common.a foo.cpp
```
g++ throws a linking error which basically says that it was unable to find any libraries...
```
foo.cpp:(.text+0x47a): undefined reference to `Class::hello()'
```

Can someone tell me what is going wrong. I also tried creating archive using ark instead of command line but no success. Is there anything else we need to do while building library archive. BTW I did rename archive to libcommon.a and tried -lcommon but that too gives the same problem. Although this is not a show stopper, I am unable to understand why does g++ rejects archive .....

Thanks in advance

---

### Post by lloyd_b on 2008-02-15
(I'd suggest posting questions like this in the "Programming" forum)

Try this:
```
ranlib common.a
```

This creates an index of all symbols in the archive, and stores it in the archive.  There are some issues with routines in the archive referencing other routines that appear later in the archive.  This resolves this.

(Note: this is equivalent to using the "s" option of the "ar" command.)

Having this index also speeds up the linking process, so I'd recommend running it on all archives...

Lloyd B.

---

### Post by akwatve on 2008-02-15
Thanks for reply. I tried that but it still doesn't help..... Even after creating indices in the archive, g++ still cannot find the symbols required in the archive:-(

---

