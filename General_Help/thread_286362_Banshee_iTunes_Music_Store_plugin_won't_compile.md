---
title: "Banshee iTunes Music Store plugin won't compile"
date: 2006-10-27
forum: General Help
---

### Post by Aranel on 2006-10-27
Hi there. I'd like to be able to access the iTunes music store from Ubuntu, and I'd heard about a plugin for the Banshee Media Player that allows one to do just that. So I installed the banshee, build-essential, and subversion packages and their dependencies, as per [the instructions](http://www.banshee-project.org/Plugins). I then downloaded the plugin to the desktop and launched the autogen.sh script.

It said I needed autoconf and automake before it could do anything, though, so I installed those too. When I tried to run it again, it began okay but returned an error (see below) that I also needed the mono package. I obliged with a "sudo aptitude install mono" and tried running the autogen.sh again. Now it simply repeats that message when I run the script:

> I am going to run ./configure with no arguments - if you wish 
to pass any to it, please specify them on the ./autogen.sh command line.
Running aclocal -I .  ...
Running automake --gnu  ...
Running autoconf ...
Running ./configure ...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for MONO... configure: error: Package requirements (mono >= 1.1.13) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_CFLAGS
and MONO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

It does the same thing when I also add the arguments given in the aforementioned instructions. I'm by no means an expert to compiling, obviously, and I have no clue what's wrong here. Any ideas?

---

### Post by Aranel on 2006-10-27
Got that to work by installing mono-devel, monodevelop, and libmono-dev. Now it's giving me this:

configure: error: No C# 2.0 (gmcs) compiler found

That makes even less sense to me... Obviously, I need to install a "C# 2.0 (gmcs compiler," but I have very little notion of what that is. Any ideas? :confused:

---

### Post by Aranel on 2006-10-27
> **Aranel said:**
> Got that to work by installing mono-devel, monodevelop, and libmono-dev. Now it's giving me this:

configure: error: No C# 2.0 (gmcs) compiler found

That makes even less sense to me... Obviously, I need to install a "C# 2.0 (gmcs compiler," but I have very little notion of what that is. Any ideas? :confused:

Heh. Searching in Synaptic for "gmcs," I came across a package called "mono-gmcs." It seems to have done the trick; it compiled and installed with no errors (albeit with a couple cryptic warnings), and Banshee recognizes it. But I'm getting a blank screen when I try to access it from Banshee, so that's also not a good sign. Oh well... I'll see what I can find out.

Thanks for letting me have this monologue. :D

---

### Post by Manny C on 2006-11-04
Aranel

Use the Search facility. 

You'll find results popping up.

---

