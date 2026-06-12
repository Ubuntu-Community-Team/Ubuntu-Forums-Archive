---
title: "libxml2 problem while compiling"
date: 2006-08-03
forum: General Help
---

### Post by tonyr1988 on 2006-08-03
When trying to compile a program. I got to the ./configure stage, and get this error:

> checking for libxml - version >= 2.0.0... no
*** The xml2-config script installed by LIBXML could not be found
*** If libxml was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XML2_CONFIG environment variable to the
*** full path to xml2-config.
configure: error: libxml2 must be installed.

I have the latest version of libxml2 installed. I even reinstalled it through Synaptic to make sure.

What's causing this? Where's that pesky xml2-config hiding at? A search didn't show where.

Anyone experienced this before?

PS - Sorry if this is the wrong forum. I assumed Programming Talk was for actual programming, not just compiling.

---

### Post by hw-tph on 2006-08-03
You need the libxml2-dev package. The -dev packages contain files required for compiling software that requires the package.

That came out odd. I'll try to explain it like this: Programs that use libxml2 need libxml2-dev in order to compile properly.


Håkan

---

### Post by tonyr1988 on 2006-08-03
Duh - that makes perfect sense.

The ./configure worked great - now I'm crossing my fingers that the rest goes well.

Thanks!

---

