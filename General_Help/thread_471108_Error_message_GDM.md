---
title: "Error message: GDM?"
date: 2007-06-11
forum: General Help
---

### Post by hombrecito on 2007-06-11
Hi everyone!

When I try to login i get this a error message that says:

"GDM could not write to your authorization file. This could mean that
you are out of disk space or that your home directory could not be opened
for writing. Please contact system administrator"

Im running an old version Hoary Hedgehog.. and I thinkt the cause of this is that my disk is full..
Tried to login in failsafe mode but It didnt work.

How do I solve this?

---

### Post by Ek0nomik on 2007-06-11
If your disk is full you can try to delete some files.

While Ubuntu is loading, try hitting Control+Alt+F1.  Hopefully you will get to a command line prompt.

Now you can delete some files to clear up space (although I don't think you will need to delete much data at all)

```
rmdir *directory.name*
rm *file.name*
```

I would also suggest using an newer version of Ubuntu, as your version is no longer supported.

---

