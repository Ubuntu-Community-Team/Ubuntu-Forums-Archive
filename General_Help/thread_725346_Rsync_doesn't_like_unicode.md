---
title: "Rsync doesn't like unicode?"
date: 2008-03-15
forum: General Help
---

### Post by eku on 2008-03-15
I'm trying doing simple backup over samba using rsync. The other computer is running Vista. Vista's share is mounted using smbsf on Ubuntu.
Some of the folders I need to backup contains unicode characters. When rsync builds file list, it tells me that some files has vanished, and points to the folder. In this case the folder has character ä, which turns into a \#204, meaning mäki turns into a m\#204ki.

What's causing this, and how do I fix it?

L

---

