---
title: "trouble building swmill from source with ./config"
date: 2007-06-26
forum: General Help
---

### Post by izak on 2007-06-26
Hi all

I'm trying to build swfmill-0.2.12 from source on Ubuntu Dapper 6.06. It is one of the tools needed for open source flash development. ([www.osflash.org](www.osflash.org)). I haven't built many things from source before, so sorry if this is a stupid question

I run ./configure like it says in the readme and it checks many things but then stops at:
"
checking for XML... configure: error: Package requirements (libxml-2.0) were not met:

No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XML_CFLAGS
and XML_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
"

I checked the synaptic package manager for libxml, but there is no package named 'libxml-2.0' only 'libxml2' which is obviously (?) the same but with the wrong name? libxml2 was already installed.

So should i set the XML_CFLAGS variable in the config script to something? But what? Also, what should the XML_LIBS variable be? Or is there something I am doing wrong?

Thanks for the help!
Izak

---

### Post by PaulFr on 2007-06-26
Is **libxml2-dev** installed ? You need that for the development files.

---

### Post by izak on 2007-06-26
Aha! Thanks for the help Paul! Now its stopping one step further, but I'll just check for the relevant dev package.

---

### Post by izak on 2007-06-26
Ok, I made some progress by installing dev packages, but now the config script stops at:

[INDENT]"
checking for FREETYPE... configure: error: Package requirements (freetype2) were not met:

No package 'freetype2' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables FREETYPE_CFLAGS
and FREETYPE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
"[/INDENT]

I installed freetype2 using synaptic, but it is a dummy package. What is that? According to synaptic:

> Dummy package for transition to libttf2
This dummy package provides a transition from the previous FreeType 1
package (freetype2 [sic]) to libttf2.  It may be safely removed once
all the packages are re-built with correct dependency to libttf2.

Checking the output of pkg-config:

[INDENT]
pkg-config --cflags --libs freetype2[/INDENT]

returns 

[INDENT]Package freetype2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `freetype2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'freetype2' found[/INDENT]

after installation of the dummy package.

Should I edit the environment variable in the config file to use libttf2? How would that look?

Thanks!
Izak

Also how do I get that nice typewriter formatting in a forum post?

---

### Post by PaulFr on 2007-06-26
I think you need **libfreetype6** and **libfreetype6-dev** for FreeType2. As for the indented block, you can wrap any text as [ QUOTE ]<text>[ /QUOTE ] (without the spaces around the QUOTE) to get > <text> - same goes for [ CODE ]<text>[ /CODE ]

---

### Post by izak on 2007-06-27
Thank you very much. I managed to build swfmill from source with your help :D

---

