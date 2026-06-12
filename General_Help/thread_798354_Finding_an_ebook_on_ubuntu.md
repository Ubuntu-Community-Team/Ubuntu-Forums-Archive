---
title: "Finding an ebook on ubuntu"
date: 2008-05-18
forum: General Help
---

### Post by Bucephalus01 on 2008-05-18
If I install this book thought this site, 

[http://linuxappfinder.com/package/ebook-dev-alp](http://linuxappfinder.com/package/ebook-dev-alp)

How do then find the book on my ubuntu box?
I have been trying find and slocate, but to no success.

slocate spits out this error:

bucephalus@Magnus:/usr/include$ sudo slocate "linux"
slocate: fatal error: Could not find user database '/var/lib/slocate/slocate.db':  No such file or directory

Anyway, what is the best method to find the book? 
And, is that slocate problem easily fixed?
I tried sudo updatedb, but that didn't fix it.

cheers.

---

### Post by Bucephalus01 on 2008-05-18
Ok, I found it in this directory.

bucephalus@Magnus:/usr/share/doc/ebook-dev-alp$ ls
advanced-linux-programming.pdf.gz  changelog.Debian.gz  copyright  listings

I thought it would have been accessible already, I mean not in .gz form.
Could the pdf be extracted to somewhere else?

---

### Post by zvacet on 2008-05-18
[Here]("http://www.advancedlinuxprogramming.com/downloads.html")

---

### Post by Bucephalus01 on 2008-05-18
Thanks for your help.
cheers
I gunzipped it also.

---

