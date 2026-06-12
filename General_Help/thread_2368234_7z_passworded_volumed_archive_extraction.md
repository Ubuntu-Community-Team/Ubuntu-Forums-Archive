---
title: "7z passworded volumed archive extraction"
date: 2017-08-08
forum: General Help
---

### Post by jlparsons on 2017-08-08
Hi folks, having a real headache trying to extract a passworded 7z archive that's split into volumes.  All the volumes are archive.7z.001 numbered and are all in the same folder.

Running the command;

```
me@pc$  7z -Pmypassword x ./archive.7z.001
```

Creates an archive called archive.7z in the same folder.  This archive can't then be opened.  Help!

I've archived them with the command;

```
7z a -pmypassword -v25m -mhe /destination /source/*
```

---

