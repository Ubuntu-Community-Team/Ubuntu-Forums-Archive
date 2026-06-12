---
title: "C compiler cannot create executables"
date: 2007-05-12
forum: General Help
---

### Post by Sale on 2007-05-12
Hi,
I'm trying to install Claws Mail 2.9.2 on Feisty 64 bit, and here is what happens when I run sudo ./configure :

```
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gnome-config... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GNOME2... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

I've looked for the answer on Google but everything I found was wague and general...Any Ideas?

BTW, why is Claws repo not working...for feisty, at least?

---

### Post by tino27 on 2007-05-12
For compiling, try running "sudo apt-get install build-essential"

Don't know 'bout the repositories. I see package sylpheed-claws, but haven't tried it myself.

---

### Post by Sale on 2007-05-12
Thanks...this worked.

I keep forgetting about "build essential" :)

---

