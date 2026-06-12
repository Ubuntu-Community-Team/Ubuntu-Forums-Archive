---
title: "Firefox bookmark errors"
date: 2005-03-25
forum: General Help
---

### Post by Novack on 2005-03-25
Hello,

I apt-get updated my system today, and Firefox (updated to 1.0.2) gives me XML errors every time I try to add or edit my bookmarks.

Selecting Bookmarks -> Add to Bookmarks gives me this error:

```
XML Parsing Error: not well-formed
Location chrome://browser/content/bookmarks/addBookmark2.xul
Line Number 1, Column 9:

operties="rdf:http://www.w3.org/1999/02/22-rdf-syntax-ns#type rdf:http://home.netscape.com/NC-rfd#loading rdf:http://home.netscape.com/WEB-rdf#status">
--------^

```

And Bookmarks -> Manage Bookmarks gives me this error:

```
XML Parsing Error: not well-formed
Location chrome://browser/content/bookmarks/addBookmarksManager.xul
Line Number 1, Column 21:

umen.getElementById("endHourRange");
-------------------^

```
And View -> Sidebar -> Bookmarks gives this error:

```
XML Parsing Error: not well-formed
Location chrome://browser/content/bookmarks/addBookmarksPanel.xul
Line Number 1, Column 5:

cted(aEvent)
----^

```

---

### Post by vassalle on 2005-04-01
[QUOTE=Novack]Hello,

I apt-get updated my system today, and Firefox (updated to 1.0.2) gives me XML errors every time I try to add or edit my bookmarks.

Selecting Bookmarks -> Add to Bookmarks gives me this error:

```
XML Parsing Error: not well-formed
Location chrome://browser/content/bookmarks/addBookmark2.xul
Line Number 1, Column 9:

operties="rdf:http://www.w3.org/1999/02/22-rdf-syntax-ns#type rdf:http://home.netscape.com/NC-rfd#loading rdf:http://home.netscape.com/WEB-rdf#status">
--------^

```

And Bookmarks -> Manage Bookmarks gives me this error:

```
XML Parsing Error: not well-formed
Location chrome://browser/content/bookmarks/addBookmarksManager.xul
Line Number 1, Column 21:

umen.getElementById("endHourRange");
-------------------^

```
And View -> Sidebar -> Bookmarks gives this error:

```
XML Parsing Error: not well-formed
Location chrome://browser/content/bookmarks/addBookmarksPanel.xul
Line Number 1, Column 5:

cted(aEvent)
----^

```[/QUOTE]
 im having the same problem too! is there a solution for this ?

---

### Post by Pjukern on 2006-04-25
Me to, working just fine untill i updatet everything...
Get the xml parsing error when i try to add bookmarks, or save pages in firefox.. Is there a way to uninstall, and roll back to previous version?

---

### Post by TheRoot on 2006-05-15
Hi there I am having the same error !!!
Isnt there any solution guys ??

---

### Post by amccausl on 2006-07-06
You should close your firefox and remove ~/.mozilla/firefox/*/XUL.mfasl and restart firefox.  I had the same problem and this fix worked dandy for me O:) .

---

### Post by Hemmer on 2007-10-24
I had trouble with a recent apt-get update method, which corrupted the xpi install window with a similar message.

This works a charm to solve this as well, thank you! :D

---

### Post by sj314 on 2007-10-31
~/.mozilla-thuderbird/*/XUL.mfasl


Solve for me similar problem with Thunderbird!!!

Thanks
:guitar:

---

### Post by Erik. on 2007-12-16
Sorry for the stupid question but how can i navigate to that file or delete it?
When i go to file explorer i can nog find anything...

Hope someone can help me

---

