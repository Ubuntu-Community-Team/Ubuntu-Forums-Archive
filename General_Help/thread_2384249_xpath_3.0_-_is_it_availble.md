---
title: "xpath 3.0 - is it availble?"
date: 2018-02-04
forum: General Help
---

### Post by kazakore on 2018-02-04
I need to do some serialisation within xml parsing and from my research the feature only got added to xpath and realted programs (eg xlst) in version 3.0. Is this available as a library for any of the common higher level languages? Checking the packages shows that most seem to have their own library but give no clear indication of the version of xpath contained within it! Unfortunately I'm going to have to teach myself the bit of whichever language I use to do the job so Bash, PHP, Perl, Python, Java, whatever seems to have the best support or you can confirm will work will do for me :)

---

### Post by dragonfly41 on 2018-02-04
You could start with eXist-db .. and its demos ..

[http://exist-db.org/exist/apps/demo/examples/basic/xquery3.html](http://exist-db.org/exist/apps/demo/examples/basic/xquery3.html)

Explore the Shakespeare collection demos .. **Run full text search on Shakespeare and group results by speaker**


[http://exist-db.org/exist/apps/demo/examples/basic/groupby.html](http://exist-db.org/exist/apps/demo/examples/basic/groupby.html)

---

### Post by kazakore on 2018-02-04
Thanks I'll try and have a look tomorrow. The feature I want I thought would be rather basic, to select an entire element (or rather broken selection of multiple elemets) including all contents whether attributes, other elements or text() strings etc (and then sort by it, even if via copying to another file.) I could only find ways to highlight either the opening tag or the text() context using xpath in Sublime but I think that's version 1.0 and a thread on stackoverflow said it can only be done from version 3.0....

---

### Post by dragonfly41 on 2018-02-05
I suggested that you look at eXist-db to get some examples.

If you prefer to write your own parsing scripts in python look here ...

[https://docs.python.org/3/library/xml.etree.elementtree.html](https://docs.python.org/3/library/xml.etree.elementtree.html)

---

