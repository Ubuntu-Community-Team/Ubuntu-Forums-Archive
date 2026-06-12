---
title: "Gettting OpenOffice 2.0 Dictionaries to work"
date: 2005-05-11
forum: General Help
---

### Post by GTKpower on 2005-05-11
Hi everyone . . . . I've got a document (OO2.0) that has justified paragraphs.  Justified paragraphs require some level of hyphenation.  I've got hyphenation enabled, but it doesn't do anything.  

I checked in Tools > Options > Writing Aids, and it doesn't show any language modules.

I checked in the repositories (I've got Breezy listed, ubt only Hoary is installed), and I have myspell, OpenOfice-hyphenation, and the OO English dictionary installed (t least I think I have that.)

Am I missing something?  Doesn't OO2.0 automatically recognize dictionaries?  How come I have no language module?  

I'd appreciate any help, since I can't finish off this document without hyphenation.

---

### Post by GTKpower on 2005-05-11
The reason I'm posting this here and not in the official OO forums is because:

1.)  I like most of you ;-)

2.)  Since I'm using Ubuntu and downloaded OO 2.0 from the Hoary repos, my problem is also Ubuntu-specific.

Cheers.

---

### Post by GTKpower on 2005-05-11
Alright, I checked my OpenOffice2 usr/share directort, and it seems i have all the dictionaries insatlled, including thesaurus and hyphrnation.

I went to myspell, and saw all the dictinaries/thesauri/hyphenation dicts there, too.  

For some reason, nothing shows up in the language module list in Writing Aids, and, I can't get spellchecking to work.  It works, but doesn't do any spellchecking.  Hyphenation doesn't do any hyphenating, either.

---

### Post by GTKpower on 2005-05-11
My last post on this topic.

I seemed to have figured out the problem.  

I have no language modules that I can select.  I need to install language modules.

I need to run Autopilot (now called "wizards") to install language modules.

Wizards doesn't run.  It's a bug in the current Ubuntu version of OpenOffice 2.0, which is really 1.9.79.2.  The NEWEST version is 1.9.84 or something, in which Wizards DO work.

So until the Ubuntu dev team decides to update OpenOffice, I think we're stuck with no spellchecking, no thesaurus, and no hyphenation.

I guess I'm forced to go back to OO 1.1.3.

 ](*,)

---

