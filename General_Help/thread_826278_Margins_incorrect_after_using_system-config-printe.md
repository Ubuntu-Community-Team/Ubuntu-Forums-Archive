---
title: "Margins incorrect after using system-config-printer"
date: 2008-06-11
forum: General Help
---

### Post by Vetala on 2008-06-11
I am using Xubuntu Hardy (8.04) with system-config-printer-common and system-config-printer-gnome (both at version 0.7.81+svn1973-0ubuntu9), and a Samsung CLP-300 printer.

When the printer paper size is set using the CUPS web configuration interface, test pages print correctly both from the CUPS web configuration and from system-config-printer. However, as soon as any print settings are adjusted from system-config-printer (not limited to just the page size setting), the test pages (and any other printing) all get shifted up the page by about 11 millimeters, printing the top part right off the top of the page.

The paper size I am using is letter, the system-config-printer says it is letter paper, and /etc/papersize has (as far as I know) always contained "letter".

The incorrect margin problem occurs with both the included, automatically configured foomatic foo2zjs drivers (version 20071205-0ubuntu3) and a fresh build of the foomatic drivers from linuxprinting.org.

I suspect that this problem has been encountered by others, since there are at least two threads asking about print margin problems, where the eventual solution was to just configure with the CUPS web interface.

Just wondering if anyone knows a fix for this (other than just using the web interface).

Thanks

---

