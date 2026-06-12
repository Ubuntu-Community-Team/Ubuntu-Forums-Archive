---
title: "Is it possible to rebuild a deb package with my CFLAGS? tried pbuilder, apt-build,etc"
date: 2007-04-28
forum: General Help
---

### Post by interzoneuk on 2007-04-28
Hi.

I've been trying in vain to rebuild deb packages with my CFLAG settings.

I have been trying (as an example) to recompile tremulous.

Although I managed to recompile by editing the debian/rules file most packages you cannot do this (and its a really ugly hack).

I have used apt-build and set up my cpu type, however when you build the package it totally ignores my settings (unless i manually edit the debain/rules files - but again you cannot do this for many packages)

I have also tried pbuilder again it ignore all my settings and recompiles it to i486 (like apt-build)

I know many people will say why bother recompilng, but I know tremulous is a tad faster on my gentoo setup and also on yoper (a totally optimized i686 distro - very fast but in beta at the moment). Besides which it would be good to know.

Any help/links would be welcomed.

If I can find a way i may dump gentoo..

---

### Post by interzoneuk on 2007-04-30
Does anyone have any ideas?

The lack of optimization is debian packages is the only thing preventing me using it full time.

It seems strange that the apt-build, etc tools simply ignore flags.

---

### Post by az on 2007-04-30
There have been many discussions about this in the distant past.  (Check the Debian mailing lists) The concensus is that compiling the userspace binaries for 686 would not yeild any optimisation, as opposed to running a kernel that is optimised for 686.  Relatively recently through, those kernel optimisations have been made run-time and not comple-time settings.  So even if the generic kernel is built for 386, it will still have the 686 optimisations.

---

### Post by interzoneuk on 2007-04-30
Hi az.

Thank you for responding to my post

Ubuntu has always seemed slightly sluggish compared to fedora, gentoo, yoper, etc. 

I always thought that was down to the fact that most debs are compiled for i386.

I shall try recompiling the kernel for my processor (athlon-xp) and see if that make it faster.

Basically i have a new drive and i am going to reinstall my OS's, previously I was using gentoo but am looking for a system that requires less looking after.

I must say the simplicity of ubuntu (particularly the package management) is great, not so sure of the default themes (kubuntu is pig ugly by default).

Suse seems really nice but the package management is very bad (so slow!!).

If the kernel recompile doesn't speed things up enough i'm going to try arch linux (and probably end up in gentoo again!)

---

