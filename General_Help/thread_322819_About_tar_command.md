---
title: "About tar command"
date: 2006-12-21
forum: General Help
---

### Post by satimis on 2006-12-21
Hi folks,

I have been looking around on man tar and can't resolve what option shall be up on running;

tar jcpf tarball.tar.bz2 /path/to/tar/

to exclude the directories '/path' and '/to' on the compressed tarball only retaining '/tar' directory.

Please advise.  TIA


B.R.
satimis

---

### Post by po0f on 2006-12-21
satimis,

```
[FONT="Courier New"]$ cd /path/to
$ tar jcpf tarball.tar.bz2 tar/[/FONT]
```
?

---

### Post by satimis on 2006-12-21
Hi po0f,

Tks for your advice.

> 
```
[FONT="Courier New"]$ cd /path/to
$ tar jcpf tarball.tar.bz2 tar/[/FONT]
```

Is there any way avoiding cd to /tar directory?

Tks.


B.R.
satimis

---

### Post by po0f on 2006-12-21
satimis,

Maybe this?
```
[FONT="Courier New"]$ tar jcpf tarball.tar.bz2  -C /path/to tar/[/FONT]
```
tar's -C option changes to the directory specified.

---

### Post by satimis on 2006-12-21
Hi po0f,

> 
Maybe this?
```
[FONT="Courier New"]$ tar jcpf tarball.tar.bz2  -C /path/to tar/[/FONT]
```
tar's -C option changes to the directory specified.
That is what I'm running daily to decompress tarballs.  I did not know it also work on compression.  Tks.


B.R.
satimis

---

