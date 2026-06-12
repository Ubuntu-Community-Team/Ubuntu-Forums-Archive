---
title: "How do you permanently delete files?"
date: 2007-08-18
forum: General Help
---

### Post by Duffy on 2007-08-18
How can you permanently delete files in Ubuntu so that they can never be recovered? I know Windoz has some third party programs that will overwrite the unused portions of the disk so that any recoverable files can never recovered using file recovery utilities, but is there anything for Ubuntu?

---

### Post by jakev383 on 2007-08-18
I have never seen a program to do so, but then again I have never seen a program to recover files either.

---

### Post by Thingymebob on 2007-08-18
in the universe repository secure-delete

---

### Post by ajgreeny on 2007-08-18
Have a look at shred, which does exactly that.  **man shred** in terminal tells you more, though it is of limited value in ext3 filesystems.

---

