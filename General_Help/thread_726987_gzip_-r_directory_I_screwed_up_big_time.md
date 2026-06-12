---
title: "gzip -r /directory I screwed up big time"
date: 2008-03-17
forum: General Help
---

### Post by dwessell on 2008-03-17
Well. I'm a retard.

I was wanting to zip a directory and all subdirs into a single file.. So I did gzip -r directory.. Well, now all of the files are zipped, individually.. 

Can someone help me out of this quagmire? Or do I have to individually unzip each file?

Thanks
David

---

### Post by lloyd_b on 2008-03-17
> **dwessell said:**
> Well. I'm a retard.

I was wanting to zip a directory and all subdirs into a single file.. So I did gzip -r directory.. Well, now all of the files are zipped, individually.. 

Can someone help me out of this quagmire? Or do I have to individually unzip each file?

Thanks
David

I just did a quick test - it looks like 
```
gunzip -r directory
```
will undo the damage.  But I suggest making a backup copy before doing this, just in case.

Lloyd B.

P.S. "tar -zcvf outfile.tgz directory" is probably what you wanted...

---

