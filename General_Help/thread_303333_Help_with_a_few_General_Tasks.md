---
title: "Help with a few General Tasks"
date: 2006-11-20
forum: General Help
---

### Post by sbjaved on 2006-11-20
Some questions...I'd appreciate if anyone would help.

1. How do I change other user's files (as a root account) overriding their permissions?

2. How do I get out of a 'manual' in terminal?

3. How do I schedule a 'fsck' (Filesystem Check) at start and how do I tell it to fix system errors automatically?

Thanks.

---

### Post by apsivam on 2006-11-20
> **sbjaved said:**
> Some questions...I'd appreciate if anyone would help.

1. How do I change other user's files (as a root account) overriding their permissions?

$ sudo chmod (new_mode) files
> 
2. How do I get out of a 'manual' in terminal?

type q
> 
3. How do I schedule a 'fsck' (Filesystem Check) at start and how do I tell it to fix system errors automatically?

I think you don't need to this manually if your file system is not clean (improper shutdown etc.) it will be checked and fixed automatically.

---

### Post by jazzgossen on 2006-11-20
If you want to, you can create a file /forcefsck (it can be empty, it just has to be there), and then fsck will run on the next boot. "man fsck" to see how to set fsck parameters.

---

### Post by sbjaved on 2006-11-21
Is there a graphical way to do this "chmod (new_mode) files" thing?

---

### Post by jazzgossen on 2006-11-21
I believe you can start a nautilus instance as root, and then change the permissions graphically (right-click, properties) from there. Do "gksudo nautilus".

---

