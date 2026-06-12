---
title: "Deja-dup cache file"
date: 2014-11-20
forum: General Help
---

### Post by Robbyx on 2014-11-20
I have set up deja-dup to save its backups to an external HD. I have just had a system message warning me that my home directory is low in available space. Deja-dup cache may be a culprit:

There are these types of files in there:

-tempdir
duplicity-full-signatures.XXXX.sigtar.gz
Ditto. manifest

_Deja-dup cache is taking up 5.8gb. How do I prune it without loss of backup data?_

[U]The wine in .config is taking up 2.9gb. Is there anything to prune in the wine directory in .config?
[/U]

R

---

### Post by bashiergui on 2014-11-22
How big is your home directory?

---

### Post by Robbyx on 2014-11-22
My home directory is in a seperate partition that is 33gb, and there is 6.9gb free.

---

### Post by bashiergui on 2014-11-23
I don't know about the deja-dup files without experimenting with it. I'd be tempted to delete the files you have questions about, then just reinstall deja-dup if it breaks. Not the most careful way to approach it though.

That is a tiny partition. If space is a constant issue you might consider a lighter distro like lubuntu. If they still maintain Damn Small Linux that's a good one. Or offload most of the data you don't immediately need onto the external drive.

---

