---
title: "Paragraph marker search"
date: 2008-05-23
forum: General Help
---

### Post by Kumera on 2008-05-23
From time to time I need to do a search through a large document (1Mb or so) for text patterns on either side of a paragraph marker.  IN MS Word I could use the ^p marker to do it without difficulty, but OpenOffice, in not recognising the paragraph marker as a character, is just useless.  Is there any other Linux-based software that can do it?

---

### Post by sdennie on 2008-05-23
Are you working with a pure text document?  If so it may be worth the effort to learn things like sed, perl and vim.  None of them are particularly easy to learn but, they are all incredibly powerful text processing tools.

---

### Post by Kumera on 2008-05-28
Yes, the documents are straight text.  I will look at those software devices,thanks, but it would be much easier if I could get an easy-to-use text processor that knew what a paragraph marker was.

---

### Post by Zill on 2008-05-28
A quick Google for "openoffice paragraph search" finds the following link:
[http://openoffice.blogs.com/openoffice/2005/12/finding_and_rep.html]("http://openoffice.blogs.com/openoffice/2005/12/finding_and_rep.html")
> In the Find and Replace window, enter the symbol for what you want to search for, in the Find field. Here's a quick reference to the symbols to enter for what you're looking for.

    * Regular carriage returns  are $
    * Soft returns inserted with a Shift Return, are \n
    * Just an empty paragraph, i.e. a carriage return but with no text on that line, is ^$
    * Tabs are \t
Don't forget to select the Regular Expressions checkbox. This will make the program look for what those codes represent, rather than literally those characters.

If you want to find a paragraph mark after particular text then use the format "\testtext$" in the Find box.  More info on these regular expressions can be found at:
[http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Regular_Expressions_in_Writer]("http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Regular_Expressions_in_Writer")

Hope this helps.

---

