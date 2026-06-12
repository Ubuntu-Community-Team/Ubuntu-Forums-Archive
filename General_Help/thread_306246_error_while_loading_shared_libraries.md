---
title: "error while loading shared libraries"
date: 2006-11-24
forum: General Help
---

### Post by Strelock on 2006-11-24
Hi folks,

I'm installing a in-house developed software on Ubuntu 6.10 and I got "error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory".

Same installation works fine on Redhat.

locate libm.so.6 returns:
/lib/libm.so.6
/lib/tls/i686/cmov/libm.so.6

Both are links to libm-2.4.so which exists in both folders...

I have absolutely no idea what's the problem...
Edit/Delete Message

---

### Post by po0f on 2006-11-24
Strelock,

How did you compile/link your program?  And this doesn't happen to be a 64-bit system, does it?

---

### Post by Strelock on 2006-11-24
Nope, its Pentium M 32 bit one...

Software comes with installation script which basically copy files  and set directories... May be this libm.so.6 is located in different folder in RedHat I'm not sure...

---

### Post by Rui Pais on 2006-11-24
hi, 
do you have libc6-dev?

---

### Post by po0f on 2006-11-24
Strelock,

Run ldd on your program to figure out where *it* thinks the library is:
```
$ ldd your_program
```
This command will spit out all the libraries the binary is linked with.

---

### Post by Strelock on 2006-11-24
> **Rui Pais said:**
> hi, 
do you have libc6-dev?

Now I do - that didn't help... I've also made ln's to the same locations of libm.so.6 as in my remoter RedHat... still not running...

---

### Post by Strelock on 2006-11-24
[QUOTE=po0f;1802566]
```
$ ldd your_program
```

well it looks for it in /lib/tls/i686/cmov/libm.so.6

and I can see it there as ->libm-2.4.so which is also present in these folder...

---

### Post by Rui Pais on 2006-11-24
> **Strelock said:**
> Now I do - that didn't help... I've also made ln's to the same locations of libm.so.6 as in my remoter RedHat... still not running...

maybe running ldconfig first...

---

### Post by Strelock on 2006-11-24
> **Rui Pais said:**
> maybe running ldconfig first...

Just tried that again. Same thing...

---

### Post by KIAaze on 2007-06-08
I know this is an old thread, but I just had the same problem for two programs and solved it by doing this:
> export LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH

More info:
[http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html]("http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html")

---

