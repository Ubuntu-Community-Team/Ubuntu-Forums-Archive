---
title: "OpenOffice not starting. Locales missing?"
date: 2007-01-23
forum: General Help
---

### Post by KPingus on 2007-01-23
Howdy,

I am using Kubuntu 6.06 LTS with a 2.6.15-27-686 kernel and I recently upgraded OpenOffice to version 2.02-2ubuntu12.2. Whenever I start ooffice or any OOo application (oowriter, oocalc, ...) from the command line I get the message

```

terminate called after throwing an instance of 'com::sun::star::configuration::InvalidBootstrapFileException'
terminate called recursively
/usr/lib/openoffice/program/soffice: line 233: 16758 Aborted                 "$sd_prog/$sd_binary" "$@"

```

Using strace to try to find the source of the problem I see messages such as:

```

open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)

```

Indeed that file does not exist. Instead the directory contains clisplow.mo and clisp.mo.

Are the locales missing? Certainly, OOo was working before the upgrade. Any suggestion would be greatly appreciated.

Thanks in advance.

---

### Post by partsdale on 2007-01-23
I had a software update in the last day or so.... 
the file was called locales...
I'm not sure if that is helpful info or not.

---

### Post by KPingus on 2007-01-23
That package is up to date on my system. I tried using apt-file (through Kpackage) to find which package contains a file called libc.mo, but it didn't find anything.

---

