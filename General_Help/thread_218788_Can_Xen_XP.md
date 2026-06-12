---
title: "Can Xen XP ?"
date: 2006-07-19
forum: General Help
---

### Post by kroiz on 2006-07-19
I just read a new article about Xen.:shock:
Just curious :rolleyes:
Is it possible to run my windows as a guest in xen hosted on my ubuntu?
Theoretically or practically?

---

### Post by x64Jimbo on 2006-07-19
Unfortunately no. Xen works because it has kernel integration in the guest, and since Microsoft owns the Windows Kernel, well... You know the rest. It's been developed, but only under an NDA (Non-Disclosure Agreement) with Microsoft (greedy bastards....)

---

### Post by RAOF on 2006-07-19
> **x64Jimbo said:**
> Unfortunately no. Xen works because it has kernel integration in the guest, and since Microsoft owns the Windows Kernel, well... You know the rest. It's been developed, but only under an NDA (Non-Disclosure Agreement) with Microsoft (greedy bastards....)

As far as I'm aware, with the latest Xen (is that version 3?) you **can** run an unmodified XP as a guest OS.  I forget if that required hardware virtualisation support or not, though.

So, if you've got a recent Intel chip, it's definitely theoretically possible.

---

### Post by kroiz on 2006-07-19
I see thanks,
I guess it will be awhile until I get to run it then.

---

### Post by RAOF on 2006-07-19
From the Xen Wiki:
> 

1.4. Does Xen support Microsoft Windows?

The paravirtualized approach we use to get such high performance has not been usable directly for Windows to date. However Xen 3.0 added Intel VT-x support to enable the running of unmodified guest operating systems, including Windows XP & 2003 Server, using hardware virtualization technology. We are working on implementing support for the equivalent AMD Pacifica technology.


There you go.  Recent Intel or AMD processor required :)

---

### Post by kroiz on 2006-07-19
I see.
 Thanks

---

