---
title: "I'm not ALL MAN (yet)"
date: 2007-03-30
forum: General Help
---

### Post by Lutherian on 2007-03-30
I always used to think that man pages were a little too short on information, until I found out that typing man <command> is only part of the available information.
If I read man (5) on the man page - it means there are 5 pages or section related to that command.

I would be grateful if someone could explain to me how I access these pages.
(I did try man -a <command> but it didn't seem to work)

Thanks for helping me become ALL man :P

---

### Post by lloyd_b on 2007-03-30
"man (5)" means that this particular entry is in section 5.  There may or may not be comparable entries in other sections.  To read an entry from a particular section, type "man {section} {command}"

For example, type "man stat", and you'll get stat(1), which is the command line program of that name.  If you type "man 2 stat", however, you'll get the documentation for the stat() system call (for programmers, and only if you have the "manpages-dev" package installed).

Section 1 is (I think) terminal commands.  Section 2 is programming documentation for system calls.  Section 5 is where you find info on configuration files.  I have no clue what the other sections represent.

"man -a {command}" will display the appropriate pages from all sections, assuming that {command} is found in more than one section.

Lloyd B.

---

### Post by gepatino on 2007-03-30
If you have a gnome desktop available, go to system/help/System docs (i'm guessing the name since i' m working in a spanish gnome)

There you have a section for the manpages, and you'll see all the sections (seven in my system)

---

### Post by Lutherian on 2007-04-02
Thanks lloyd_b and gepatino.
Both your infos. were useful in different ways.
Learning Linux is for people who *read* so I'm trying to get familiar with all the documentation.

---

