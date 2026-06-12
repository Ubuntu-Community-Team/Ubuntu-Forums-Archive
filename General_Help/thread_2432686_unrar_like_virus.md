---
title: "unrar like virus"
date: 2019-12-06
forum: General Help
---

### Post by creatxr on 2019-12-06
is here someone notice that unrar like virus?

sometime unrar runs automatics and occupy 10%~15% cpu.

so, usually i uninstall unrar after i dont need.

now, i 've a better choice that i use unrar-promise with nodejs.

unrar-promise ver2.0.1 has a problem, it throws exception while the file 's name includes space.

---

### Post by Holger_Gehrke on 2019-12-06
Nope, never saw anything that made me think unrar behaved like a virus. I did take a look at the source published at rarlabs (for a completely unrelated reason) and while a lot of it went straight over my head, I think I would have caught on to a reason for the kind of behaviour you're describing. There's probably something else running on your system that calls unrar in the background. Best candidates for that would be the indexer for some kind of desktop search indexing the content of archives or a thumbnail generator looking inside archives for images or videos to create thumbnail images for.

unrar-promise is just a wrapper around node-unrar-js, which is a reimplementation of libunrar in javascript based on the code from rarlabs.

Holger

---

