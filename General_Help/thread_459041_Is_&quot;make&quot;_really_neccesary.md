---
title: "Is &quot;make&quot; really neccesary?"
date: 2007-05-30
forum: General Help
---

### Post by happysmileman on 2007-05-30
In all the installation from source I've seen the steps are always "./configure", "make", "sudo make install"...

However "./configure", "sudo make install" seems to work perfectly fine for everything I've used it on...

Is there a reason to run the "make" command?

---

### Post by steevols on 2007-05-30
Well, I don't know what happens when you type "make install" in your case!

Theoretically, "./configure" sets up the software for your environment, "make" compiles it, and "make install" copies it to your installation directory, i.e. "/opt/programname".

Perhaps when you run "make install" w/out actually having run "make", "make" is run automatically?

---

### Post by Tesiph on 2007-05-30
It is usually true that "make install" will also execute "make" if that isn't done before. The difference is that by "sudo make install" you also run "make" with elevated privileges.
That will usually make a mess out of the directory you run it in, because it will create a lot of files owned by root.

---

### Post by happysmileman on 2007-05-30
Ah ok... I get it now...

---

### Post by Bachstelze on 2007-05-30
Running make alone is also useful when you don't want to install the software with make install (for exemple if you want to use checkinstall to build a DEB for it, or even not install it at all).

---

