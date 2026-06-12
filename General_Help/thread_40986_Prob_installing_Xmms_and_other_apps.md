---
title: "Prob installing Xmms and other apps"
date: 2005-06-11
forum: General Help
---

### Post by osorensen on 2005-06-11
Ive just installed Ubuntu and i have some problems getting some apps too work, like Xmms, Valknut etc

the problem is that when im building the apps ( configure) there is always something missing, heres an example : 

```

The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

```

when looking at the SPM its already installed  :roll: 

i guess i need to add some lines to the configure file but i have no idea were, anybody have an example ?

btw im loving this distro, one of the best ive seen :)


EDIT : Posted this at wrong spot, was gonna post in hoary section

---

### Post by az on 2005-06-11
I moved it.

Why are you compiling xmms.  Ther eis already a prebuilt versino in the universe repository.


Also, to compile stuff, you need the developmental headers.  Loog for glib-dev or xlibs-dev or whatever library thepackage needs to build, install the correspongin packages that end in a "-dev" name.

---

### Post by osorensen on 2005-06-11
oooops just enabled universe repository, didnt know what it was :D

so much easier hehe

---

