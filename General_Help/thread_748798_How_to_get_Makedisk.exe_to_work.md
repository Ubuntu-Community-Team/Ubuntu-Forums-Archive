---
title: "How to get Makedisk.exe to work"
date: 2008-04-07
forum: General Help
---

### Post by elyksirrom on 2008-04-07
I need to make a floppy driver disk. WINE refuses to let makedisk.exe work. Does anyone have any suggestions?

I need to make a SATA driver disk for a asus a8v promise378.

Thanks

---

### Post by trippinnik on 2008-04-07
there's a floppy disk creator for linux as well.  Do you have the disk img? you can use dd utility to make floppy's from an image in linux.  I don't think you'll have the image though, so you may need to try using the cabextract utility to get the files out of your .exe file.

---

### Post by SOULRiDER on 2008-04-07
> **elyksirrom said:**
> I need to make a floppy driver disk. WINE refuses to let makedisk.exe work. Does anyone have any suggestions?

I need to make a SATA driver disk for a asus a8v promise378.

Thanks

I had to create a floppy like that too with no luck. I had to use an actual windows installation, WINE couldnt create it.

---

### Post by chunchengch on 2008-04-07
I don't have floppy, so I am not sure if it works or not, maybe you could try mono to run .exe file, good luck!

$ sudo apt-get install mono
$ mono makedisk.exe



[COLOR="Blue"]Mono is a platform for running and developing applications based on the
ECMA/ISO Standards. Mono is an open source effort led by Novell.
Mono provides a complete CLR (Common Language Runtime) including compiler and
runtime, which can produce and execute CIL (Common Intermediate Language)
bytecode (aka assemblies), and a class library.

mono is a metapackage containing dependencies for the runtime of Mono.
If you do not need all of them (or try to work around X11
dependencies), install the core packages manually: mono-jit, mono-mcs or
mono-utils.[/COLOR]

---

### Post by SOULRiDER on 2008-04-08
Mono wont work for two reasons:

1) The program has to be written in .NET
2) AFAIK unless you compile the source in Linux, it wont run.

---

### Post by elyksirrom on 2008-04-08
Nothing I tried worked. I just had to find all the files the driver needed and manually do it. Thanks for the effort though.

---

