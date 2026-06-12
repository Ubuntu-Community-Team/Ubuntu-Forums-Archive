---
title: "xapian indexing"
date: 2021-03-07
forum: General Help
---

### Post by cmcanulty on 2021-03-07
I have made an alias to run xapian indexing when I want to. However I can't find a way to disable xapian indexing running automatically and yet still have it available to run manually. It really slows my old desktop. I am running xubuntu 20.04

---

### Post by norobro on 2021-03-07
I don't know much about xapian, but I experimented with the C++ and Python API some time ago, so maybe I can help.

From the xapian website:> Xapian is an Open Source Search Engine Library, released under the GPL v2+. It's written in C++, with bindings to allow use from Perl, Python 2, Python 3, PHP 5, PHP 7, Java, Tcl, C#, Ruby, Lua, Erlang, Node.js and R (so far!)How are you interfacing with the library?

Please post your alias.

---

### Post by dragonfly41 on 2021-03-08
Recoll is a GUI frontend to xapiandb and can be configured with index scheduling.
I monitor recoll indexing process through Stacer - another GUI.
Sometimes starts fans going.

---

