---
title: "Epson Printer Problem under Ubuntu 7.04"
date: 2007-04-24
forum: General Help
---

### Post by rollinc on 2007-04-24
hi 

i've installt ubuntu last weekend and i really like it, BUT i am not able to install my printer!

The printer is a Epson 6100l.

I've installed epsonepl ([http://sourceforge.net/projects/epsonepl/](http://sourceforge.net/projects/epsonepl/)) driver via rpm and tar.gz but i am not able to find the printer in the ubuntus "add printer" list. Is there anything i forgot?

greets
christian

---

### Post by phidia on 2007-04-24
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-6100L](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-EPL-6100L)

If your printer is the EPL-6100L then maybe the above link will help get it working.

---

### Post by rollinc on 2007-04-24
Thanks.

I've already visited this page. But it could not help me.

Some minutes ago i tried to install it again via *.deb package. 

[I]christian@cp3000:~/Desktop$ sudo dpkg -i epsoneplijs_0.4.0-2_i386.deb
Choosing  deselected package epsoneplijs.
(reading database ... 106846 Dateien und Verzeichnisse sind derzeit installiert.)
extracting epsoneplijs (from epsoneplijs_0.4.0-2_i386.deb) ...
setting epsoneplijs up (0.4.0-2) ...
Attempting to remove older installs in /usr/local/bin.
Done.

Please check /usr/doc/epsoneplijs-0.4.0 for tips on CUPS, foomatic, etc.
Happy printing! Bye for now.
[/I]

(I translated it form german to english)

My Problem is that i was unable to select my driver via CUPS (even i restarted the pc) and the directory " /usr/doc/epsoneplijs-0.4.0" is not set up.

Any idea?
Or another way to install it?

christian

---

