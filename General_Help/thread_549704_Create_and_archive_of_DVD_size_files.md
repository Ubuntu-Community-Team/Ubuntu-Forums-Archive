---
title: "Create and archive of DVD size files"
date: 2007-09-12
forum: General Help
---

### Post by kpictjl on 2007-09-12
I have several thousand files totaling about 30GB.  I know how to create 1 big archive file.    How do I archive the 30GB into DVD size files (4.7 GB)?   I want to burn them to dvd and put them away somewhere safe.

Thanks,
Tod

---

### Post by vjones777 on 2007-09-12
This may be overkill for this, but Mondo is a backup tool that will split up into whatever size you want.  If the archive may change in the future, Mondo can also save just the changes.  There are other, command line, based options which I'm sure others will mention (e.g TAR, RAR GZIP).

---

### Post by kpictjl on 2007-09-12
I've read about Mondo and I was thinking of trying that for a total backup solution, but it's definitely overkill for this case.  I'm just looking for a 1 time thing.  I've never heard of RAR, I'll check that out.

---

### Post by kpictjl on 2007-09-12
Is this right?  I'm a little fuzzy on why there are some dashes and wether or not I need a slash after my directory names...

Arhive
```

tar cvpzf - /home/mydir | split -a 2 -b 4700m - /home/mydir.tgz

```
I think this moves everything in /home/mydir (include "mydir") to a bunch of 4.7 GB files in /home called mydir.tgz*.  Right?

Restore
```

gzcat /home/mydir.tgz* | tar xvpfz - -C /home

```
This would concatenate all those 4.7GB files together and then unpack them in /home...including adding a directory name of mydir.

credit to this post...
[http://ubuntuforums.org/showthread.php?p=2587977&highlight=split#post2587977](http://ubuntuforums.org/showthread.php?p=2587977&highlight=split#post2587977)

---

