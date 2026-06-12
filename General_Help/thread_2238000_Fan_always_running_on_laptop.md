---
title: "Fan always running on laptop"
date: 2014-08-05
forum: General Help
---

### Post by Todd_Chilson on 2014-08-05
My fan is always running on my Sony Vaio Model# PCG-9RFL laptop. I have read what is now starting to feel like a ton of forum posts on this issue and none have solved my issue. I am running Ubuntu 12.04.4 LTS 3.2.0-67-generic with 512 MB RAM. The last attempt at solving this involved chaning the /etc/defautl/grub line to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=/"Linux/" " from the default line which used to look like GRUB_CMDLINE_LINUX_DEFAULT="quiet splash".

Thanks in advance.

---

### Post by mörgæs on 2014-08-05
Hi, welcome to the fora.
It's an old computer and Ubuntu might be too heavy for it. I suggest a fresh install of Lubuntu 14.04.1.

---

### Post by ajgreeny on 2014-08-05
I am amazed you got Ubuntu running at all with just 512MB ram.

I would also recommend Lubuntu 14.04.1.

Incidentally, I have never seen that kernel option written that way with the two forward slashes; it is normally shown without them as:-
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

It may not matter, but it seemed worth mentioning.

---

