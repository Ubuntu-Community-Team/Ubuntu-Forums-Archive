---
title: "SystemV vs Debian init scripts"
date: 2013-03-01
forum: General Help
---

### Post by terminator14 on 2013-03-01
I'm currently reading the "LPIC-1/CompTIA Linux+ Certification Exam Guide", and one of the paragraphs in it reads:

> **System V** Linux distributions that use System V init scripts store them in the /etc/rc.d directory. Within /etc/rc.d are a series of subdirectories named rc0.d through rc6.d. Each of these directories is associated with a particular runlevel. Within each of these subdirectories are symbolic links that point to the init scripts for your system daemons, which reside in /etc/rc.d/init.d. Red Hat Linux and Fedora use System V-type init scripts.

I use Debian, and according to this page from the official Debian wiki: 

[QUOTE=http://wiki.debian.org/Daemon]Debian makes use of System V-style init scripts for daemon management.[/QUOTE]

The thing is - there is no /etc/rc.d in Debian as the book describes. Scripts are stored in /etc/init.d/ and symbolic links to them are placed in /etc/rc{0,1,2,3,4,5,6,S}.d/.

Does this mean that the book is wrong, or does Debian simply deviate from System V-style init script conventions? I'm trying to figure out if the paragraph above (from the book) is worth remembering, or if it's wrong and I should just remember the way Debian does it.

---

