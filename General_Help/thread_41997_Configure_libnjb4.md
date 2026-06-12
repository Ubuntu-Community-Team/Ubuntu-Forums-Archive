---
title: "Configure libnjb4?"
date: 2005-06-15
forum: General Help
---

### Post by vtechstu on 2005-06-15
I can't get gnomad2 installed.  I need this lib file first, but i dont know how to configure it.  Thanks if you can help.

chase@ubuntu:~$ sudo dpkg -i gnomad2_2.6.3-1_i386.deb
(Reading database ... 74189 files and directories currently installed.)
Preparing to replace gnomad2 2.6.3-1 (using gnomad2_2.6.3-1_i386.deb) ...
Unpacking replacement gnomad2 ...
dpkg: dependency problems prevent configuration of gnomad2:
 gnomad2 depends on libnjb4; however:
  Package libnjb4 is not configured yet.
dpkg: error processing gnomad2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnomad2
chase@ubuntu:~$

---

### Post by tristan on 2005-06-15
You need to install libnjb. There are instructions on the gnomad2 page where to get it from.

There's actually a later release of gnomad2 - 2.7, which works better and is a lot faster at file transfers. Download rpms of Gnomad2_2.7 and libjb2.1.2, convert them to debs using alien, and sudo dpkg -i those debs.

One last thing - you'll need to run gnomad2 as root (eg use gksudo gnomad2).

---

### Post by vtechstu on 2005-06-15
Alright thanks, it's installed , just got tar it.  What is this "Alien" program you're talking about?  Thanks.

---

