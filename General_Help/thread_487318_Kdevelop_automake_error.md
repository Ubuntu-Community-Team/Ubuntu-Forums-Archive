---
title: "Kdevelop automake error"
date: 2007-06-28
forum: General Help
---

### Post by lightnb on 2007-06-28
I created a basic C++ project in Kdevelop, and ran 'automake and friends'.

The output gives the following error:

```

./admin/cvs.sh: 651: --version: not found
*** AUTOCONF NOT FOUND!.
*** KDE requires autoconf 2.53 or newer
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

```

I've installed automake with 'sudo apt-get install automake' and also install the recommended packages apt-get listed. Alsi installed: 'sudo apt-get install libtool libtool-doc g77  gcj libltdl3-dev'

Am I missing something?

---

### Post by lightnb on 2007-06-29
I'd like to add a clarification:

The 'hello world' command line default project works fine. It's only the kde based projects that fail with that error...

---

