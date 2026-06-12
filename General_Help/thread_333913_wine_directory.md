---
title: "wine directory"
date: 2007-01-08
forum: General Help
---

### Post by Ubuntuud on 2007-01-08
Hi,

I need to change something in a dll file from wine somewhere in /wine/dlls, but I'm unable to locate the directory. Could you help me out? Thanks in advance!

---

### Post by kj1h234lkj1234 on 2007-01-08
Do you mean ~/.wine ?

When in your home folder (Places->Home Folder), press Control-H to show hidden folders. You should have a folder called ".wine" there.

Any folder beginning with a . is automatically hidden. To show them, use Control-H as stated from above, or "ls -al" from the command-line.

You could also try:

```
find ~ -name dlls
``` to locate the folder.

Good luck

---

### Post by Ubuntuud on 2007-01-09
That second action should do it, thanks!

---

