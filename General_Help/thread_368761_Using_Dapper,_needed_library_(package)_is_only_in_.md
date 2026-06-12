---
title: "Using Dapper, needed library (package) is only in Edgy"
date: 2007-02-23
forum: General Help
---

### Post by kag on 2007-02-23
I need the libmono-cairo2.0-cil library which is only available on Edgy and Feisty ([link]("http://packages.ubuntulinux.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=libmono-cairo2.0-cil")). What are my options?

---

### Post by sdide on 2007-02-23
Download from 
[http://ftp.fi.debian.org/debian/pool/main/m/mono/libmono-corlib2.0-cil_1.2.2.1-1_all.deb](http://ftp.fi.debian.org/debian/pool/main/m/mono/libmono-corlib2.0-cil_1.2.2.1-1_all.deb)
do 

# dpkg -i libmono-corlib2.0-cil_1.2.2.1-1_all.deb

if that doesn't work, you mkight want to remove the package again with 

# dpkg -P libmono-corlib2.0-cil

---

### Post by po0f on 2007-02-23
kag,

Upgrade, or compile the library from source.  The second choice is not too hard.  Start by grabbing the source and reading through the included files, normally the README and INSTALL files, for any prerequisites to compilation.

[EDIT]

Too slow.  :)

You might want to try what sdide suggested if "compile" and "source" make you squeamish.  ;)

---

### Post by kag on 2007-02-24
I'm not sure exactly after what step it happened, but now when I open Synaptic, it says mono-jit and libmono-corlib2.0-cil are broken.

When I open libmono-corlib2.0-cil_1.2.2.1-1_all.deb with the package manager, it says "Error: failed to satisfy all dependencies (broken cache)". When I first downloaded it, it said something like "Error: Dependency is not satisfiable: mono-jit". 

I already had mono-jit but a lower version than needed by this package. That's when I downloaded mono-jit_1.2.2.1-1_i386.deb. I'm not sure how it could have went wrong because I cannot even install this package - it says libc6 is needed.

From what I understand, I tried to install the new libmono-corlib2.0-cil but it needed a new mono-jit. I tried to install the new mono-jit but it needed libc6. Now those packages are broken in Synaptic... I don't get it.

---

### Post by kag on 2007-02-25
For others who might encounter the same problem, I went in Synaptic, selected mono-jit, went in Package -> Force version, and forced the version that came with Ubuntu. I pressed apply and it repaired everything. It also removed libmono-corlib2.0-cil but that's fine.

---

