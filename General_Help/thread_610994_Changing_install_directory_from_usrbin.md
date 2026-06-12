---
title: "Changing install directory from /usr/bin?"
date: 2007-11-12
forum: General Help
---

### Post by hochiha on 2007-11-12
Okey, I'm quite new to linux, and I was just wondering if the directory synaptic installs to could be changed. I usually keep my programs on another partition than the system, and I'm trying to get it to work with Xubuntu (Feisty) too. 

This far I've just tried to symlink /usr/bin to my other folder, but that messed things up quite a bit :) Any ideas how to get it to work?

Thanks in advance!

---

### Post by scorp123 on 2007-11-12
> **hochiha said:**
>   usually keep my programs on another partition than the system, and I'm trying to get it to work with Xubuntu (Feisty) too.  You should have partitioned properly when you installed your system, e.g. put /usr on its own partition:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

As for the rest ..... Don't do it if you don't know what you are doing! You're only going to mess up your system. :lolflag:

---

### Post by hochiha on 2007-11-12
> **scorp123 said:**
> You should have partitioned properly when you installed your system, e.g. put /usr on its own partition:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

As for the rest ..... Don't do it if you don't know what you are doing! You're only going to mess up your system. :lolflag:

Oh yeah, should have figured that out.

That's why I put all my documents on another harddrive, managed to fix the symlink thingy quite easy too :)

Seems I'm off to reinstall then, thanks a lot!

---

