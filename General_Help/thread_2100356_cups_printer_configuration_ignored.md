---
title: "cups printer configuration ignored"
date: 2013-01-01
forum: General Help
---

### Post by r.stiltskin on 2013-01-01
This problem is probably due to the fact that I originally installed Kubuntu 12.04, then installed and used Gnome briefly, and then finally installed Unity (which I'm learning to like :o ).

In System settings/Printing my Brother printer's Duplex option is set to "none", i.e., single-side printing, and this agrees with the Cups localhost:631 settings for this printer.  But whenever I go to print a .odt document in LibreOffice, or a .txt document in Gedit, or a .pdf document in Evince, the printer is pre-set to print double-sided unless I specifically change that setting each time.

On the other hand, if I open the same .txt or .pdf documents in Kate or Acroread or Okular, the printer is set to print single-sided (as it should be).

I tried setting up a new user account, and for that user the default printer settings are correct in all applications, but I'd rather not delete my main user account if I can avoid it.

There must be an erroneous local configuration file someplace in my main user's home directory that I can edit or delete to fix this.  Any ideas?

---

### Post by simple simon on 2013-06-17
bump

I have this too.  Defaults in CUPS say one thing.  Evince/LibreOffice say another.  I'm waisting a lot of paper.

Simple

---

### Post by pdc on 2013-06-20
for LibreOffice;

does the command

> [COLOR="#FF0000"]/usr/lib/libreoffice/program/spadmin[/COLOR]

open up a settings page for LibreOffice? Does making changes in that help you? If so, you can create a launcher, with the command as above

---

