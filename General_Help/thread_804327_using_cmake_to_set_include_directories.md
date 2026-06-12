---
title: "using cmake to set include directories"
date: 2008-05-23
forum: General Help
---

### Post by fontenot_1031 on 2008-05-23
I posted here awhile ago with some questions about a csound front-end called AlgoScore.  I'm now rebuilding it since the last build was insisting that I was on a macintosh :/

So here's what make_build is saying when I try and build the program.
```
root@laptopish:/usr/local/share/AlgoScore/src# ./make_build
-- checking for PCRE
--   not found.
-- checking for Csound
--   not found. CSOUND SUPPORT DISABLED!
-- checking jack midi API: not supported
CMake Error: This project requires some variables to be set,
and cmake can not find them.
Please set the following variables:
CSOUND_INCLUDE_DIR

```

I have installed csound through apt-get install csound.  Going to install PCRE after this post.
Does anyone know how I could tell cmake where my csound include directory is?

---

