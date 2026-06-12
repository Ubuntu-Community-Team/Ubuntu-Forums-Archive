---
title: "installing TiLP2- Gutsy Gibbon"
date: 2008-05-12
forum: General Help
---

### Post by grossaffe on 2008-05-12
I couldn't compile this program for my life!  here's where i'm at.  i have libticables2 compiled and installed.  that's not a problem.  I have libticonv compiled and installed, also not a problem.

problems:
1) libticalcs2 will not configure because
2) libtifiles2 will not compile due to a multitude of errors including:
a) error: storage class specified for parameter 'int_fast32_t'
b) error: expected declaration specifiers before '__extension__'
c) error: expected specifier-qualifier-list before 'FileClass'
d) error: declaration for parameter 'fwrite_long' but no such parameter
e) error: expected '{' at end of input

most of these errors were repeated a dozen or so times.  so... any ideas on how i can get a working libtifiles2 version 1.1.0 or later so i can compile libticalcs2 so i can compile TiLP2?

---

### Post by zenwalker on 2008-05-12
The code errors can occur due to the:

1) Mismatch in the vers of libs it needs or the gcc.
2) Bugs in the code.

---

### Post by grossaffe on 2008-05-12
> **zenwalker said:**
> The code errors can occur due to the:

1) Mismatch in the vers of libs it needs or the gcc.
2) Bugs in the code.

i'm thinking its coding errors since i've already experienced a multitude of version number errors and seen the results of those.  all i need is any version of libtifiles2 1.1.0 or greater that will compile correctly.  i already looked in the synaptic, but the latest version they have is 1.0.3, or something along those lines.

---

