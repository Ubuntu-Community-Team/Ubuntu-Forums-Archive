---
title: "gnomeburner nautlas Not working Don't know where to start"
date: 2005-10-04
forum: General Help
---

### Post by grimmson on 2005-10-04
Hello all. I've read about this problem and don't know where to begin.
tried scanbus

grimmson@ubuntu:~$ cdrecord -scanbus
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilli ng
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian. org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI dr iver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
grimmson@ubuntu:~$

I don't think this is good. gnomebaker says my drive is cdr burnable. I don't know what to do. Any help is appriciated. 
p.s. search turned up 11 pages of stuff (most unrelated.) I'd love a good (narrow)search term.

---

### Post by brentoboy on 2005-10-04
[QUOTE=grimmson]For possible targets try 'cdrecord -scanbus'. Make sure you are root.[/QUOTE]

Have you used sudo to run this?
Just a thought, I dont know if it will help or not.

---

### Post by grimmson on 2005-10-04
Hey thanks for the quick thought. Nope I've read about kernal 2.5 and over causing problems. It will start prepair to burn and the system almost locks. Don't think sudo would help but I can be wrong.

---

### Post by grimmson on 2005-10-04
just testing the signiture

---

### Post by grimmson on 2005-10-05
Replaced Cyberdrive cw068d cdrw with nec nd-3540-a and baker works first try at 16x. [COLOR="Red"]Is this a Bug?[/COLOR] Should I report this or just keep my head down and be happy?

---

