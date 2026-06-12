---
title: "Printing and file browsing broken since upgrade"
date: 2008-07-03
forum: General Help
---

### Post by clanmackay on 2008-07-03
Since my distro upgrade to Hardy, there have been two dramatic problems that have sunk my productivity.

Firstly, printing works incredibly inconsistently.  Printing works in Adobe Acrobat Reader, Firefox, and gv, but not in OpenOffice.org, lpr, or most other programs (I use a HP Color Laserjet 1600 with the foo2hp driver.)  I might guess a lpr mis-configuration, but doesn't gv just cat the ps file to lpr?  When I try that directly, it fails (it shows up in the queue momentarily, then disappears.)  Nothing else changed since the upgrade, and printing previously worked form everywhere, including the command line.  A workaround is to print to a file, open in gv, and print it.  Needless to say, this is frustrating.

Secondly, and more importantly, is that the (Gnome?) file browser thingy (I don't really know how it's architected -- shared library?  applet?) takes ten to thirty seconds to load when running an "Open" or "Save As" command in every application I've tried.  This. is. driving me. insane.  It went from about a quarter second in Gutsy to almost 100 times that now.  Again, nothing has changed.  To be safe, I made sure there were no optical discs in the drives and I unplugged all USB storage devices -- though they didn't interfere before the upgrade, I tried anyway, and this attempted fix does nothing.

I don't truly understand what is happening where -- what's at kernel lever, driver level, X level, Gnome level, application level, whatever -- but I can give you the response of any queries you instruct me to type, if you will be patient with me.

Thanks in advance.

---

