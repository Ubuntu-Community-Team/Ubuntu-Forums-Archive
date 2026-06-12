---
title: "Installing libraries: Should they go in /usr/lib?"
date: 2006-07-30
forum: General Help
---

### Post by tibbe on 2006-07-30
I want to manually install some files from the NekoVM library ([http://nekovm.org/doc/begin](http://nekovm.org/doc/begin)) since there's no package for it. The web site recommends putting the .so files and some other library files (in a format specific to the virtual machine) in /usr/lib/neko.

[LIST]
[*]Is /usr/lib the correct place to put .so files?
[*]Will sub directories of /usr/lib (i.e. /usr/lib/neko) be searched automatically when the system looks for libs?
[*]Should binaries go in /usr/bin?
[/LIST]

---

### Post by catlett on 2006-07-30
The default place for binaries is /usr/bin (bin being short for binaries) and the default for libraries is /usr/lib (lib being short for libraries)
There are other places that hold binaries but that is the basic place for them. There is a /bin but that is for system binaries like cat and pmount. There is a /usr/local/bin but tyhe application would have to know of that path specifically. So a straightforward place is /usr/bin but you can place them elsewhere buit you will need to make sure the application needing thatg bin can find it.
It's a little like windows C:\Program Files. Programs don't have to be stored there to run but it is the default. And if an application was looking for a progran it would search C:\ Program Files unless it was told to look elsewhere.

---

