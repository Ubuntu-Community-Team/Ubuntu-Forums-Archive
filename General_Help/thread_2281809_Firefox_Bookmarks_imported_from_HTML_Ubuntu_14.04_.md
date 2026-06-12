---
title: "Firefox Bookmarks imported from HTML Ubuntu 14.04 LTS Trusty Tahr"
date: 2015-06-09
forum: General Help
---

### Post by mdavis1231 on 2015-06-09
During a recent reinstallation, I imported my Firefox bookmarks from Internet Explorer HTML bookmarks.  All of my bookmarks are showing up with .URL appended to them.  Is there any way to do a blanket removal of the .URL following each bookmark?  Or do I have to go through one by one and delete it?

---

### Post by SeijiSensei on 2015-06-09
```
sed 's/\.URL$//g' < /path/to/bookmarks.html > newbookmarks.html
```
That uses the sed command line editor to delete the string ".URL" at the end of each line.  Because sed uses "[regular expressions]("http://www.regular-expressions.info/")" for pattern matching both the dot and the dollar sign have special meanings.  The dollar sign represents the end of the line.  The dot matches any character unless you tell sed to treat it literally by "escaping" it with a backslash.

Sed will read (the "<" character) the file /path/to/bookmarks.html and write (">") the edited version to newbookmarks.html in the current directory.

---

