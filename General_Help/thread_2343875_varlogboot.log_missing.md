---
title: "/var/log/boot.log missing?"
date: 2016-11-20
forum: General Help
---

### Post by titanic1955 on 2016-11-20
Hi everyone,

I just noticed on this PC **boot.log** is missing? :o

I thought it was in **/var/log/boot.log **?

How can one correct this?

Thanks in advance

---

### Post by slickymaster on 2016-11-20
See this: [No more boot logging since 16.04?]("http://askubuntu.com/questions/763638/no-more-boot-logging-since-16-04")

---

### Post by titanic1955 on 2016-11-20
> **slickymaster said:**
> See this: [No more boot logging since 16.04?]("http://askubuntu.com/questions/763638/no-more-boot-logging-since-16-04")  [COLOR=#111111][FONT=Ubuntu]I investigated the boot logging behavior on two different machines. On a computer with an UEFI based BIOS the [/FONT][/COLOR]boot.log[COLOR=#111111][FONT=Ubuntu] file exists - but on a computer with legacy based BIOS it seems to not exist at all. So in case the system is installed in legacy BIOS (MBR/msdos) mode, this could be the explanation why your [/FONT][/COLOR]boot.log[COLOR=#111111][FONT=Ubuntu] file is dated from 2016-04-22, it's a leftover from Ubuntu 15.10.[/FONT][/COLOR]   

Oh, that was interesting.

Yeah, on this one machine by me with [COLOR=#111111][FONT=Ubuntu]**legacy based BIOS** it is _not_ there,

but the other one with [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]**UEFI based BIOS **has it. [/FONT][/COLOR]#-o

---

