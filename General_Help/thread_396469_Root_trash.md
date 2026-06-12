---
title: "Root trash"
date: 2007-03-29
forum: General Help
---

### Post by Mateo on 2007-03-29
what's the best way to delete the root trash?  For some reason you can't even cd to /root/.Trash (says permission denied.  nor can you sudo cd there either.  You can delete some files in nautilus but not all will delete.

---

### Post by Mateo on 2007-03-29
Never mind I figured it out.  But for future reference for people, do this:

```
sudo -i
```

then it will ask for your password and you'll **be** root.  then you can simple:

```
cd .Trash
rm *
```

and that should do it.

---

### Post by aysiu on 2007-03-29
Alt-F2 ```
gksudo nautilus
``` is the best (and *safest*) way to do it.

---

### Post by Mateo on 2007-03-29
that way won't delete some files though.

---

### Post by aysiu on 2007-03-29
> **Mateo said:**
> that way won't delete some files though.
It won't?

---

### Post by Mateo on 2007-03-29
That's right.  Certainly files that have an X looking icon over them won't delete in nautilus. that's why I originally posted this topic.  but if you do 'sudo -i' you can cd into the directory and delete everything.

---

### Post by cookfromfrozen on 2007-03-29
> **aysiu said:**
> It won't?
No, it won't, but adding -rf to rm will.

---

### Post by aysiu on 2007-03-29
But ```
gksudo nautilus
``` launches Nautilus *as* root. How can there be files you can't remove? I don't understand...

---

### Post by Mateo on 2007-03-29
me neither.  i'll look later, but they are special files of some type.  i already deleted them, but I believe one was an old symlink, maybe they all were? you can't delete them from root nautilus but can from root terminal.

---

