---
title: "`GLIBC_2.4' not found"
date: 2007-01-16
forum: General Help
---

### Post by terry98 on 2007-01-16
hi i've just installed rar, but when i try to unrar something it gives me this error

rar: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by rar)

i have instaled glibc packages but i dont know what the problem is... any ideas???

---

### Post by sympeltun on 2007-01-22
I have the same problem as well, but this is with torcs, i cant run it each time i try to run it by entering "torcs" in the terminal it gives me the exact error message! :'(

---

### Post by ranjan392b on 2007-04-03
I just installed linuxdcpp and I am also getting a similair error message
"linuxdcpp: /lib/tls/libc.so.6: version `GLIBC_2.4' not found (required by linuxdcpp)"
Please help me out! I am stuck!

---

### Post by vedanuzal on 2007-04-11
Yeah the new java wireless toolkit 2.5 also gives me this message when i run an emulator but there doesn't seem to be a package for it in the repositories.  It means that it can't find the 2.4 version  of the c libraries.  I did find some mail archives saying a source package had been accepted [here]("http://lwn.net/Articles/218822/") and [http://mirror.linux.org.mt/mirror/ubuntu/pool/main/g/glibc/](http://mirror.linux.org.mt/mirror/ubuntu/pool/main/g/glibc/) this contains what i think is a debian source package but not sure if we should use these.   Can any ubuntu developers post the fix to this problem as it seems to be mostly ignored when the question is asked (found alot a few posts asking this question but no replies).

---

### Post by cristinaDubtes on 2007-11-26
hello,

I have a similar problem. I try to execute an application and an error saying GLIBC_2.4 not found appears.
I have 'libc.so.6' but I don't know how to get the proper one.

Can anybody help me?

---

### Post by vedanuzal on 2007-11-26
I did end up getting around/fixing the problem but can't remember what it was.  You could try installing older versions of glib or it could be that you are not installing the program properly (or the way it expects) more informations is needed ie what commands you type etc and the result you get.

---

### Post by cristinaDubtes on 2007-11-27
Thank you very much. I have the solution.
I have tried with another computer with Ubuntu 7.10 and it works.

---

### Post by jcoffland on 2007-12-28
If you found a solution don't you think you should post it?

---

