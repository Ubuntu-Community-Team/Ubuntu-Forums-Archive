---
title: "Lost access to my partition (after moving a few files by mistake)"
date: 2013-12-23
forum: General Help
---

### Post by salixliu on 2013-12-23
Hi everybody,

I moved a few files from the "boot" folder, by mistake, and then I was no longer able to access my Lubuntu. No files were deleted, just moved.
I can now surf the Internet with my Ubuntu CD, and I still can see my partition, but I'm unable to access it.
Does anybody know how I could access it again?

Thank you anybody

---

### Post by steeldriver on 2013-12-23
Hello and welcome to the forums

Once you are booted using the CD, you should be able to move the files back using the file manager provided you give it administrator (super user) privileges - open a terminal window (Ctrl-Alt-t or search for 'Terminal' in the dash), then type

```
gksu nautilus
```

---

