---
title: "ldconfig error message while apt-get dist-upgrade"
date: 2005-03-25
forum: General Help
---

### Post by rwabel on 2005-03-25
I get many times this error message when apt is setting up files
for example
Setting up kdelibs4 (3.4.0-0ubuntu3) ...
ldconfig: File /usr/lib/libmcop_mt.so.1.0.0.#prelink#.sTkymf is too small, not checked.

Setting up libktnef1 (3.4.0-0ubuntu5) ...
ldconfig: File /usr/lib/libmcop_mt.so.1.0.0.#prelink#.sTkymf is too small, not checked.

Setting up libkcal2a (3.4.0-0ubuntu5) ...
ldconfig: File /usr/lib/libmcop_mt.so.1.0.0.#prelink#.sTkymf is too small, not checked.

Setting up libkdepim1 (3.4.0-0ubuntu5) ...
ldconfig: File /usr/lib/libmcop_mt.so.1.0.0.#prelink#.sTkymf is too small, not checked.

but it's not happening for every package.

Has anyone an idea what this message means and how I can get rid of it?

thanks

---

### Post by alastair on 2005-03-25
From the man page for prelink :

"prelink  is  a program which modifies ELF shared libraries and ELF dynamically linked binaries, so that the time which dynamic linker needs for their relocation at startup significantly decreases and also due  to  fewer  relocations  the run-time  memory  consumption  decreases  too ...."

It looks like prelink is warning that some libs are too small to process - so nothing to worry about I think.

I don't actually have prelink installed on my v5 install.

---

### Post by rwabel on 2005-03-25
thanks for the answer, good to know

---

