---
title: "How do i build a database?"
date: 2013-07-17
forum: General Help
---

### Post by pstrbrc on 2013-07-17
In the process of writing a series of books, I find myself organizing and cross-referencing a significant body of texts, not only for my benefit, but also for those who will read my books. The body of texts is a collection of sermons, which are positively riddled with Bible references, so I've formatted the sermons with html so that they can be read in a browser, and so I can link to the scripture references, which open in a side frame. Along with this, I can write (sometimes lengthy) explanatory notes, which i link to open in a lower frame, footnote style. Along with this, each sermon paragraph has its own anchor, so I can make reference from one sermon to another. It would seem that these anchors would also be a good way to reference where these links originate. 
So, here's the question:
How do i build an accessible database of all these cross-references without manually logging each link I insert? I would want the ability to track a link by noting both its location and destination.  Can I use a lightweight program such as SQLite? Do I sound like I even remotely know what I want? 
:D
As a sidenote, my grasp of the workings in Ubuntu (especially at the command line level) are almost entirely at an intuitive level, and I'm not sure I ever remember exactly what I did to make something work! This is not to say that I'm reluctant to do so, but that there's massive holes in my own internal reference catalog of Linux minutia. So if you break it down into small jumps, I'll be much more likely to figure it out!

---

### Post by theDaveTheRave on 2013-07-18
pstrbrc,

you may want to check out [jabref]("http://jabref.sourceforge.net/screenshots.php"), it uses the standard linux / tex bibref file format, so it stores your reference info in a flat file form. Although I have a memory of being able to connect it to a actual DB, is used mysql at the time.
Otherwise the bibtex file format is essentially an xml format, so it should be possible to convert the data into an external or embeded db, but I don't see this info in the docs.

David

---

