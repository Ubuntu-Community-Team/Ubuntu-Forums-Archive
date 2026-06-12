---
title: "ext3 checking"
date: 2005-06-06
forum: General Help
---

### Post by lgl on 2005-06-06
I have an ext3 file system on my machine and I have noticed that it is checked every thirty times the system is booted. As ext3 is journalled does the system really need to do this and if not can I turn it off.

Im sorry I think this is in the wrong area.

---

### Post by Mez on 2005-06-06
It may be a journalled file system, but it can still become corrupt ... prblems physically on the disk, some spurious program writing to disk when it shouldnt.

It's always best to have it check, you could risk corrupting/losing your data if you dont

---

### Post by SNo0py on 2005-06-06
The other option would be to use reiserfs - in my personal experience it works fine and there are no checks...

---

### Post by az on 2005-06-06
man tune2fs

---

