---
title: "[SOLVED] Missing Glib2.0 headers for compiling Pidgin (Feisty)"
date: 2008-01-04
forum: General Help
---

### Post by mustbealennox on 2008-01-04
How do I go about installing the development header files for GLib 2.0? I downloaded the latest Pidgin tar ball and got this error when running the ./configure command:

```
checking for GLIB... no
no
configure: error:

You must have the GLib 2.0 development headers installed to build.

If you have these installed already you may need to install pkg-config so
I can find them.
```

According to Synaptic, I already have the libglib2.0-0 (and other corresponding packages) installed

---

### Post by PeterJS on 2008-01-04
> **mustbealennox said:**
> How do I go about installing the development header files for GLib 2.0? I downloaded the latest Pidgin tar ball and got this error when running the ./configure command:

```
checking for GLIB... no
no
configure: error:

You must have the GLib 2.0 **development headers** installed to build.

If you have these installed already you may need to install pkg-config so
I can find them.
```According to Synaptic, I already have the libglib2.0-0 (and other corresponding packages) installed

Try installing libglib2.0-0-dev.

---

### Post by mustbealennox on 2008-01-04
Thanks, that was the missing package (libglib2.0-dev).

---

