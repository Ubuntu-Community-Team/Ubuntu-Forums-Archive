---
title: "gvfs-rm for directories?"
date: 2008-06-06
forum: General Help
---

### Post by raskolnik on 2008-06-06
Hi,

Is there a way to delete non-empty directories from the command line through gvfs?

I'd like to write a script to delete all files/directories from the trash after x days, but gvfs-rm only seems to work on files and empty directories. For instance, to delete a directory named "test" from the trash, I would try:

```
gvfs-rm Trash:/_test
```

...which works fine. Unless "test" is not empty, in which case gvfs-rm throws the error:

```
Error deleting file: Error removing file: Directory not empty
```

There doesn't seem to be a switch for recursion, or another command which can simulate it. Am I missing something? I would like to avoid using something like "find /home/user/.local/share/Trash" (etc) if possible, since I have multiple mount points and multiple trash locations. Any help would be greatly appreciated.

---

