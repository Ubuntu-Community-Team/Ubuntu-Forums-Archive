---
title: "Firefox xml parsing errors"
date: 2005-05-28
forum: General Help
---

### Post by kenux on 2005-05-28
I am new to using linux and am running into some problems.

I am trying to update my firefox and also and the emacs editor and whenever i click on a link to download i get an XML Parsing error. I also get the same thing when i try to change preferences in firefox. How can i fix this problem so i can download and update things.

This is the Full error when i try to upgrade firefox:
XML Parsing Error: not well-formed
Locations: chrome://mozapps/content/downloads/unknownContentType.xul
Line Number 1 Column 13:

_DS.Unassert(mimeSource, ValueProperty, mimeLiteral, true);

This is the Full error when i try to change the preferences in firefox:
XML Parsing Error: syntax error
Location: chrome://browser/content/pref/pref.xul
Line Number 1, Column 7:

(6 spaces) then root.disabled = "true";

Those are my errors loet me know what to do.

I have also tried:
 sudo apt-get install mozilla-firefox

But it says that i am up to date but under help->about moziila firefox   it says that i have version 1.02

Thanks 
Ken

---

### Post by sciolizer on 2005-06-30
Hi I was having the same problem with firefox.  (The XML parse error.)  I fixed it by opening up symantic, marking mozilla-firefox for reinstallation, and applying the change.  The next time I started firefox, it did not give me those problems.

I have not used apt-get very much, but I would guess that

 sudo apt-get reinstall mozilla-firefox

would work just as well.  (Note reinstall instead of install.)

---

