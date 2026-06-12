---
title: "How do you take own of a file?"
date: 2008-05-07
forum: General Help
---

### Post by Moonfrost on 2008-05-07
Hey guys, I'm having problems with permissions and I know I can just log in as root and do whatever I want with X file but I don't want to do that every time I need to do something with X file that's out of my normals account's reach. How do I "own" a file so I can change its permissions?

---

### Post by davidpbrown on 2008-05-07
sudo chown username /path/to/file

will give you ownership but if you don't have access to the parent directories you might have difficulty seeing it.

You can also do multiple files /path/to/dir/*

---

### Post by panda726 on 2008-05-07
I believe sudo chmod x7x /path/to/file will work if you are in the group.  Depends on the file, who owns it and the group.  If it is a system file, it may need to be owned by root for things to work properly.

Tor

---

### Post by Moonfrost on 2008-05-07
> **panda726 said:**
> I believe sudo chmod x7x /path/to/file will work if you are in the group.  Depends on the file, who owns it and the group.  If it is a system file, it may need to be owned by root for things to work properly.

Tor

No, it's not a system file fortunately...I got it on the Desktop, pretty much every file now get owned by root on Hardy it seems.............Vista?

---

