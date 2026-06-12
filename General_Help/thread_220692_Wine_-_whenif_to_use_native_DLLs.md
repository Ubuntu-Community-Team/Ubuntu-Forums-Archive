---
title: "Wine - when/if to use native DLLs?"
date: 2006-07-21
forum: General Help
---

### Post by Burgresso on 2006-07-21
I was wondering if anyone could give some feedback on using native DLLs for wine - specifically, does anyone reccomend any specific native DLLs to try to boost performance? Also, when should, if at all, should native DLLs be used?

gracias

burgresso

---

### Post by 3rdalbum on 2006-07-22
If you have Windows installed already, it's probably just best to always use the native (Windows) DLLs.

If you open a program with WINE and you get an error messsage printed to the terminal which says that a particular DLL couldn't be found, that's when you should use native DLLs (or at least, the DLL that it says it can't find).

I'd just like to ask a question too on this very topic: Rather than copy the native ones to ~.wine/drive_c/Windows/system, is it alright to just symlink them from a read-only NTFS partition?

---

### Post by hollaburoo on 2006-07-22
If when running something from a terminal and you get a lot of fixme:nameofdll, then it might be a good idea to try a native dll.  Sometimes the builtin ones will do better though.

---

### Post by andrebrait on 2008-01-15
So,it's better to copy all my windows dlls to wine's folders and use them instead of wine's ones?

Would Steam and Counter-Strike Source finnaly run?

---

### Post by bodhi.zazen on 2008-01-15
Wine changes from version to version and I think you should use the native, wine dll if at all possible.

You should try the Windows dll if :

1. You are following a specific how-to that advises you to do so.

2. You have tried the native dll and are having problems.

---

