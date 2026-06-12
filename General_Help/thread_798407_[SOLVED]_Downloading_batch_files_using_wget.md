---
title: "[SOLVED] Downloading batch files using wget"
date: 2008-05-18
forum: General Help
---

### Post by vishzilla on 2008-05-18
I want to download a batch of JPG files from a FTP website. How do I download all of them with wget if the path is [ftp://photo.domain.com/photo/](ftp://photo.domain.com/photo/)

---

### Post by roe_polak on 2008-05-18
The man page for wget suggests that you use
```
% wget -r
```
for recursive retrieving. I would try that.

The man file also says:
> 
You want to download all the GIFs from a directory on an HTTP
server.  You tried wget [http://www.server.com/dir/*.gif](http://www.server.com/dir/*.gif), but that
didn’t work because HTTP retrieval does not support globbing.  In
that case, use:

            wget -r -l1 --no-parent -A.gif [http://www.server.com/dir/](http://www.server.com/dir/)

More verbose, but the effect is the same.  -r -l1 means to retrieve
recursively, with maximum depth of 1.  --no-parent means that ref&#8208;
erences to the parent directory are ignored, and -A.gif means to
download only the GIF files.  -A "*.gif" would have worked too.


The command probably also applies to ftp-servers. I think it is something like this you are looking for.

---

### Post by vishzilla on 2008-05-18
Thanks anyway....while doing some Google search I came across this. For reference sake
```
 wget -nd -r -l1 --no-parent --ftp-user=USER --ftp-pass=PASS -A.JPG **URL**
```
including authentication

---

### Post by roe_polak on 2008-05-18
Oh, yeah. I completely forgot user information :oops:
Glad you figured it out yourself.

---

