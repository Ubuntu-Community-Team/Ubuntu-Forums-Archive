---
title: "Strange Epiphany freezes"
date: 2007-01-18
forum: General Help
---

### Post by bapoumba on 2007-01-18
Hello everyone :)

Epiphany started to freeze today, forced to **killall epiphany** many times. I use regular Ubuntu repositories for edgy, not running beryl or anything. Here are the error messages :
```
(epiphany:5449): libgnomevfs-WARNING **: Failed to create service browser: Bad state
Applications can not close shared connections. Please fix this in your app. Ignoring close request and continuing.
```

Google was not of much help. I decided to file a bug report, as nothing like this was reported.
[https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/80424]("https://bugs.launchpad.net/ubuntu/+source/epiphany-browser/+bug/80424")

Here are my two questions :

1- after I blogged this, a friend of mine using epiphany just told me that he gets the same error messages, with no freezes or anything. How could I track down the problem then ?

2- the bug was rejected (fine with me) but I do not understand what "not a malone bug" means. So what is a "malone bug" ? Where should these kind of bugs (if they are) be reported to get informations and/or help ?
I'm sure you can provide me with useful links ;)

[QUOTE=Malone]Malone is a bug tracker designed from the ground up for the distributed nature of code on the internet.

Malone understands that a single bug can appear in many packagings of the same code - from upstream and in different distributions. Malone allows you to view and track the status of that bug in all these different places, facilitating bug squashing and resource sharing throughout the open source community.

The Malone bug system features distributed bug assignment (to upstream and within multiple distributions), version tracking (to tell precisely which versions of a product have a specific bug) and links to external bug tracking systems and resources.[/QUOTE]

---

### Post by Stemp on 2007-01-18
what about trying gdb for testing ?

```
$ gdb epiphany
GNU gdb 6.4.90-debian
Copyright (C) 2006 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "i486-linux-gnu"...(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

(gdb) run
```

---

