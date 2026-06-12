---
title: "how to install realproducer basic?"
date: 2008-01-07
forum: General Help
---

### Post by chunchengch on 2008-01-07
I download the Realproducer Basic "realproducer_basic_111_linux_setup.tgz", and type command "sh realproducer_basic_111_linux_setup.tgz" as indicated to install it, but I get error message, has anyone ever installed it successfully? thanks for any reply!

$ sh realproducer_basic_111_linux_setup.tgz
realproducer_basic_111_linux_setup.tgz: 1: Syntax error: Unterminated quoted string


here is the instruction of installation from Real.com

Once you've successfully completed the download, you will be ready to install the RealProducer. To do this, you must type 'sh <name of file you downloaded>' from the command prompt.

      Example: sh realproducer_basic_111_linux_setup.tgz

---

### Post by heindsight on 2008-01-07
It looks like their instructions are wrong. The tgz suffix indicates that the file is a gzipped tar archive
to extract it, do something like:
```

mkdir realproducer
cd realproducer
tar -xzf ../realproducer_basic_111_linux_setup.tgz

```

How to proceed from there, depends on the exact contents of the archive. Hopefully there is a
README or INSTALL file somewhere in there with proper instructions.

---

### Post by chunchengch on 2008-01-10
Unfortunately, there is no README or INSTALL file in the file realproducer_basic_111_linux_setup.tgz,
any more comment about this? thanks a lot!

---

### Post by ron999 on 2008-03-02
Hi
I've had problems too trying to install the Linux version of RealProducer.:(

But the Windows version runs with Wine.:)

---

### Post by georger13 on 2008-03-21
I've had the same problem.  This doesn't make any sense.

There doesn't seem to be any way to either "make" the program or use the producer executable that the instructions say will run the software.

Googling this produces zero results as well.

Is there something wrong with the file?

---

### Post by ron999 on 2008-03-21
Hi
I've given up with it.
The Windows version works OK with Wine.
:)

---

### Post by dschaller on 2008-05-11
I have RealProducer Basic working in 7.10 (Gutsy). There is no installer, but the producer executable works after simply unpacking the tarball. You need to install the older libstdc++5 from the repos first before it will run, though. I created a directory /usr/local/RealProducer and then put the contents of the tarball into there. Then I created a symlink to the executable in /usr/local/bin so it would be in my path. RealProducer now seems to be working fine for me. But you're right, the instructions from Real on how to install this are a worthless mess.

---

