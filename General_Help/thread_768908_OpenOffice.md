---
title: "OpenOffice"
date: 2008-04-26
forum: General Help
---

### Post by Thedjatclubrock on 2008-04-26
I just did an apt-get update, apt-get upgrade. Everything worked except openoffice. It tells me to do an apt-get -f install and I get:

Selecting previously deselected package openoffice.org-style-human.
(Reading database ... 130850 files and directories currently installed.)
Unpacking openoffice.org-style-human (from .../openoffice.org-style-human_1%3a2.4.0-3ubuntu6_all.deb) ...
Selecting previously deselected package openoffice.org-common.
Unpacking openoffice.org-common (from .../openoffice.org-common_1%3a2.4.0-3ubuntu6_all.deb) ...
Unpacking openoffice.org-core (from .../openoffice.org-core_1%3a2.4.0-3ubuntu6_i386.deb) ...
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_1%3a2.4.0-3ubuntu6_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libpsp680li.so')
Selecting previously deselected package python-uno.
Preparing to replace python-uno 1:2.4.0-3ubuntu6 (using .../python-uno_1%3a2.4.0-3ubuntu6_i386.deb) ...
Unpacking replacement python-uno ...
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-core_1%3a2.4.0-3ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)




This is on Kubuntu 8.04 x86

---

### Post by Thedjatclubrock on 2008-04-26
Is this a Repository error? Any Ideas?

---

### Post by deja on 2008-05-04
I'm also getting this problem.

---

