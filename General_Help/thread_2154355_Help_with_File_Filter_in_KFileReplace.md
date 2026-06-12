---
title: "Help with File Filter in KFileReplace"
date: 2013-06-14
forum: General Help
---

### Post by SillySod on 2013-06-14
Hello - I use either "regexxer" or "kfilereplace" to do batch find-and-replace operations on all the HTML pages on my website.

I need to apply a change to all the pages on the site which I have designated as "index" pages, ie. these pages contain links to other pages on the same topic.

The only way to identify these pages is by the filename, which does not end with a number.  So an index page would be "Thistopic.html" and the other pages would be "Thistopic1.html", "Thistopic2.html" etc.

How can I specify in the "filter" in kfilereplace (or the "pattern" in regexxer) to only search for files where the character before the ".html" suffix is not numeric?

---

### Post by SillySod on 2013-06-22
With a bit of playing about, I've found that the filter/pattern string I need is

*[A-Za-z].html

If I use that, it finds all the files I want.

The next challenge is to do the search and replace bit.  Some of the pages already have the code that I want to include on all pages, so I don't want it to be inserted if it already exists.

How can I get kfilereplace to skip files which already contain the code?

---

