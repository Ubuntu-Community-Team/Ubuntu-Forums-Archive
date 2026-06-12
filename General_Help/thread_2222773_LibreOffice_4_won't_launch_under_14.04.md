---
title: "LibreOffice 4 won't launch under 14.04"
date: 2014-05-08
forum: General Help
---

### Post by valveirs on 2014-05-08
Weirdly, I installed a libre writer extension (altsearch.oxt) and on launching writer, I found the cursor spins for a bit and then .. well nothing happens.
This is a new install of Ubuntu 14.04 (the upgrade from 13.10 had crashed and I had to do a complete install from DVD).

I have removed and reinstalled Libre Office and removed the ./config/libreoffice folder in my home directory.

The reinstalled programs still don't launch (writer, impress, calc etc.)

I wonder if anyone has run into this bug and perhaps has found a work-around.

Val

---

### Post by sotiris2 on 2014-05-08
Does it output any errors if ran from the terminal?

---

### Post by valveirs on 2014-05-09
When I run writer from the command line, there is a very short splash screen and then this report:

soffice -writer
javaldx: Could not find a Java Runtime Environment!
Warning: failed to read path from javaldx
/usr/lib/libreoffice/program/soffice.bin: error while loading shared libraries: libmythes-1.2.so.0: cannot open shared object file: No such file or directory


It seems something is wrong with Java.  I guess I will start over and re-install UBUNTU and then all my software.

Thank you for the command line suggestion.

Val

---

### Post by caver12 on 2014-05-09
Go to Sysnaptic and see if java-common and openjdk-7-jre areinstalled. If not instal them and try again.

---

