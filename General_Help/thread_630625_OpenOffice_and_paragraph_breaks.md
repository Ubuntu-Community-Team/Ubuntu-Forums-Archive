---
title: "OpenOffice and paragraph breaks"
date: 2007-12-03
forum: General Help
---

### Post by uPilot on 2007-12-03
I've recently become a user of Ubuntu after deciding to dual boot it with my existing Gentoo install.

The problem I am having is that both these distros have OpenOffice version 2.3.0 installed, and the version on Ubuntu creates paragraph breaks when you hit 'enter' rather than create a new line.  This means I have to use 'shift+enter' rather than just 'enter'.  Its not a major pain too too much... but the problem is that all my existing documents are getting affected by this.  I open up documents I've written elsewhere and whenever I had pressed 'enter', it creates a paragraph break.

This makes the entire document look as if it was written in double spaced lines.  A document of 10 pages now takes 18.  I really cannot continue to use Ubuntu as I am a student and major problem is preventing me from continuing my work.

Any help would be greatly appreciated.

---

### Post by uPilot on 2007-12-03
*bump*

---

### Post by FuturePilot on 2007-12-03
Possibly try creating a new profile?
```
mv .openoffice.org2 .openoffice.org2_old
```

---

### Post by metalheart on 2007-12-04
IIRC pressing enter should start new paragraph. If you do not want 'double space lines', use different style for text or make new one that is similar to the one used in old documents.

---

### Post by uPilot on 2007-12-05
I have tried creating the new profile, as well as confirming key orders in current.xml

The problem is that even existing .doc or .odt documents are getting affected by this change.  For instance, right now Im working on a formal report for an English class as an end-of-year project.  It's due on Friday.  I've worked on this document (saved in .doc format) on both my desktop running XP+OpenOffice as well as on my laptop in Gentoo+OpenOffice (I dual boot this laptop Gentoo/Ubuntu).  All has been well.  When I've tried to open the same document in OpenOffice on Ubuntu however, the document goes into this weird what looks like paragraph breaks rather than page breaks.

My report goes from 22 pages to 29 pages.  My title page is 2 pages rather than the one.  The ToC is two rather than one.  So for the moment, I have to boot back into Gentoo to get any actual work done, or use my XP desktop.

---

