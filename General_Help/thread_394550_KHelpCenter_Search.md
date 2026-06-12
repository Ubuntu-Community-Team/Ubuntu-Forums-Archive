---
title: "KHelpCenter Search"
date: 2007-03-27
forum: General Help
---

### Post by Tookelso on 2007-03-27
Hello,

I'm running GNOME as my dekstop, but have many KDE apps installed.  For some KDE apps, the help information is brought up by KHelpCenter, which is fine.

However, the Search feature only searches the UNIX man pages, which is the only entry under the "Search Options" tab.  Obviously, the KHelpCenter *should* be able to search whatever help file I'm looking at, but it can't.  I have a screenshot here:
[http://notesmine.com/_media/screenshot-the_kturtle_handbook_-_kde_help_center.png?cache=cache](http://notesmine.com/_media/screenshot-the_kturtle_handbook_-_kde_help_center.png?cache=cache)

I've tried going to "Settings"..."Build Search Index", but in the "Build Search Index" dialog, I see "Application Manuals" under the Search Scope, and "Missing" under the status.   If I click "Build Index", I get the following message.  Any hints?

> X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Global symbol "$kdekdehtmldir" requires explicit package name at /usr/bin/khc_docbookdig.pl line 94.
Execution of /usr/bin/khc_docbookdig.pl aborted due to compilation errors.

Should I create an environment variable $kdekdehtmldir, and if so, what do I set it to?

Thanks,
--Took

---

