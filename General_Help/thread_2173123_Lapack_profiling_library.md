---
title: "Lapack profiling library"
date: 2013-09-08
forum: General Help
---

### Post by tor2 on 2013-09-08
Hello!

In hope of a lot of fellow lapack users I post my question here.

I want to use gprof to quickly profile my fortran program. Everything
works fine except that I can't get a profile of the lapack-routines.

Searching the web for days all I find is:

[COLOR=#000000]Q: How can I profile a code, using gprof or xprofiler, and include the calls to LAPACK?[/COLOR]
[COLOR=#000000]A: You'll need to include the profile-enabled version of LAPACK, namely -llapack_profile which resides in /usr/local/lib[/COLOR]

but I don't have this library. I have tried both to download it using synaptic manager (upgraded repo to ubuntu saucy)
and creating it using the makefiles provided in the tar-file when you download the package from netlib.

All in all, I am beaten.

Is there anyone who has experience in using gprof with lapack routines? All help is appreciated!

---

