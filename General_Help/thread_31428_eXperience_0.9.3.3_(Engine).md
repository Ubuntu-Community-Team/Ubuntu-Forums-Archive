---
title: "eXperience 0.9.3.3 (Engine)"
date: 2005-05-03
forum: General Help
---

### Post by MemoryDump on 2005-05-03
Has anybody been able to get this new release working? It was released on May 1,2005 on: [http://freshmeat.net/projects/experience/?branch_id=53574&release_id=193778](http://freshmeat.net/projects/experience/?branch_id=53574&release_id=193778)

I've had no luck whatsoever so far :(

Here's what I've tried and what I got:

When I tried adding the deb package it gave me dependency errors.
When I tried to run configure it kept on complaining about libc6 being outdated.
I even tried adding your server to my apt sources and it didn't like that neither.

======================================================
in ./configure I get:
./configure: line 19566: gdk-pixbuf-2.0: command not found

however when I run: locate gdk-pixbuf-2.0
I get: /usr/lib/pkgconfig/gdk-pixbuf-2.0.pc

If I type set my path is: PKG_CONFIG_PATH=/usr/lib/pkgconfig:/usr/lib/share:/usr/lib
so this should be working no?
======================================================
when I do:
sudo dpkg -i gtk2-engines-experience_0.9.4_i386.deb

I get:
Selecting previously deselected package gtk2-engines-experience.
(Reading database ... 88221 files and directories currently installed.)
Unpacking gtk2-engines-experience (from gtk2-engines-experience_0.9.4_i386.deb) ...
dpkg: dependency problems prevent configuration of gtk2-engines-experience:
 gtk2-engines-experience depends on libc6 (>= 2.3.5-1); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu13.
dpkg: error processing gtk2-engines-experience (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gtk2-engines-experience

I tried installing libc6 from [http://packages.debian.org/experimental/base/libc6](http://packages.debian.org/experimental/base/libc6) with no luck. :(
=====================================================
when I add: deb [http://benjamin.sipsolutions.net/debian/](http://benjamin.sipsolutions.net/debian/) unstable/ to my sources list then run apt-get update I get:                                                                                      
Reading package lists... Done
W: GPG error: [http://benjamin.sipsolutions.net](http://benjamin.sipsolutions.net) unstable/ Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems

?? README is here: ttp://benjamin.sipsolutions.net/debian/README
====================================================

Any ideas/suggestiong/help? I'm stomped!
This is WEEK1 for me using Ubuntu and I've never used Debian before neither. So far I've been pretty impressed. I have a few other issues which I will post in other threads. ;)

Thanks

-MD :p

---

