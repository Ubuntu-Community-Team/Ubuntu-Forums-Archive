---
title: "recompile kernel and remaster install CD"
date: 2006-11-17
forum: General Help
---

### Post by renzokuken on 2006-11-17
im having a problem installing linux ( i use the broad term linux cos i mean NO distro has worked yet) on my Evesham laptop (turns out its a Clevo M665JE clone)

it always hangs just after (uncompressing linux kernel)

well anyway, after digging around for ages i found a useful tip on the gentoo forums and would like to change ONE option in the ubuntu kernel on the install/desktop CD and see if it helps me

namely, disabling the option under [b]"processor type and features"
< > Local APIC support on uniprocessors[/b]  ............(laptop is a dual core Turion)

i know you can remaster the CD, but is it possible to recompile the kernel on the CD to change this option so i may have some luck installing ubuntu?

if so, how would i do it?

i have dapper running happily on my desktop (windoze free for a couple of years now) and want the same for my shiny new laptop.

thanks

---

### Post by az on 2006-11-17
I think you will be successful by passing the nolapic option when you boot the cd.  See the F-keys help menu options just after you boot the cd.

There should not be the need to recompile the kernel and remaster the cd.  Perhaps file a bug report, though.

---

### Post by renzokuken on 2006-11-17
I think i have passed that option before, although i tried so many of the acpi/apic (too many similar abreviations!!) options that i cant remember exactly which ones.

If i did, then it didnt work. I'll give it another go tonight and see what happens.

Changing the kernel option is kind of a last ditch effort for me.

---

### Post by renzokuken on 2006-11-18
ok, so tried **nolapic** with edgy i386 and 64bit as well as openSUSE 10.2 and the same is still happenening, hangs at black screen at the "uncompressing linux kernel" stage

any more suggestions cos otherwise im gonna try the kernel compilation and see what happens........which i will need some advice/pointers for

---

