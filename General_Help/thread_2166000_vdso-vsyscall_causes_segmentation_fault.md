---
title: "vdso-vsyscall causes segmentation fault"
date: 2013-08-07
forum: General Help
---

### Post by 3wais on 2013-08-07
I tried to run a program. It generates a long output in the form of a memory map (I guess). those are the last 3 lines:
```
7fff584cb000-7fff584ed000 rw-p 00000000 00:00 0                          [stack]
7fff58563000-7fff58565000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Segmentation fault (core dumped)
```

I searched  a bit for this and found that vdso has a bug that causes the seg fault. I found a bug fix for redhat:
[https://bugzilla.redhat.com/show_bug.cgi?id=673616](https://bugzilla.redhat.com/show_bug.cgi?id=673616)
I just don't know how to use this bug fix for ubuntu.

I also read somewhere that the problem could be related to linux-vdso.so or linux-gate.so. I tried to install them but there was nothing with these names.


can anybody help ?? either with .so files or the big fix or anything to fix the problem ??

---

### Post by CitadelUniversal on 2013-08-07
If the file is a patch try using the "patch" command line here's the manual for it [http://manpages.ubuntu.com/manpages/lucid/man1/patch.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/patch.1.html) - this however only applies to lucid I don't know if it will work for 12.04 LTS or 13.04.

---

### Post by 3wais on 2013-08-07
> **CitadelUniversal said:**
> If the file is a patch try using the "patch" command line here's the manual for it [http://manpages.ubuntu.com/manpages/lucid/man1/patch.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/patch.1.html) - this however only applies to lucid I don't know if it will work for 12.04 LTS or 13.04.

The command is working in 13.04. But I still have a problem.

I type the command like this: ```
patch -i attachment --verbose 
``` where attachment is the bug fix file.
it then asks me for the file to patch(file to be changed) and I don't know what should it be:
```
Hmm...  Looks like a unified diff to me...can't find file to patch at input line 17
Perhaps you should have used the -p or --strip option?
The text leading up to this was:
--------------------------
|From 13fac179aa50556ba3c60790a9beb6ca9d0b1b8b Mon Sep 17 00:00:00 2001
|From: Andrey Vagin <avagin@openvz.org>
|Date: Fri, 28 Jan 2011 23:31:20 +0300
|Subject: [PATCH rh5] vdso: export vdso_sysctl_vsyscall
|
|Signed-off-by: Andrey Vagin <avagin@openvz.org>
|---
| arch/x86_64/vdso/vclock_gettime.c |    4 ++--
| arch/x86_64/vdso/vextern.h        |    1 +
| include/asm-x86_64/vsyscall.h     |    1 +
| 3 files changed, 4 insertions(+), 2 deletions(-)
|
|diff --git a/arch/x86_64/vdso/vclock_gettime.c b/arch/x86_64/vdso/vclock_gettime.c
|index 5e15d01..3e586bf 100644
|--- a/arch/x86_64/vdso/vclock_gettime.c
|+++ b/arch/x86_64/vdso/vclock_gettime.c
--------------------------
File to patch:
```

this is the full bug bix file (named attachment). [https://bugzilla.redhat.com/attachment.cgi?id=475892](https://bugzilla.redhat.com/attachment.cgi?id=475892)

---

### Post by 3wais on 2013-08-09
Is there a way to disable VDSO or Vsyscall from the kernel?

---

