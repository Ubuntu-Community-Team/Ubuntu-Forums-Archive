---
title: "best editor for recognizing paragraph vs. line feeds in txt files"
date: 2007-05-21
forum: General Help
---

### Post by xdevnull on 2007-05-21
There was a great windows program called ultraedit that I used to use for editing e-books.  Basically, it could convert line feeds to wrap and back again.  It also would recognize two hard returns after one another as a paragraph delimiter.  I was wondering if there was anything out there in linux that had the same capability.  Basically to convert a .pdf, html or even many .txt book files, something needs to be able to un-hardcode the carriage returns intelligently.  Ultraedit did it very intelligently, and I was hoping something in linux could do the same.

Thanks

---

### Post by kidders on 2007-05-22
Hi there,

Depending on what kind of conversion you want to do, any half-decent text editor (ie one with support for regular expression searches) should do the job. If you wanted to do something simple (like strip out explicit line breaks without losing the space between paragraphs, for instance), it would probably be easier to just use **sed**, **awk**, or something similar ... especially if you had lots and lots of files to tweak.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

