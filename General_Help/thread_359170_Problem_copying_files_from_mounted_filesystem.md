---
title: "Problem copying files from mounted filesystem"
date: 2007-02-11
forum: General Help
---

### Post by jenigmat429 on 2007-02-11
After messing up a dist-upgrade, I'm using a live CD to see if I can recover some of my files. Some files I can copy from the mounted hard drive, but others I don't have the permissions  for. Is there any way I can save those files?

---

### Post by dexter on 2007-02-11
Try right clicking those files, properties and then permission, make sure you have read access.

---

### Post by jenigmat429 on 2007-02-11
What if I don't?

---

### Post by Rui Pais on 2007-02-11
> **jenigmat429 said:**
> What if I don't?

you can copy in a terminal with the sudo cp command (in a livecd you won't need to type a password)

---

### Post by dexter on 2007-02-11
> **jenigmat429 said:**
> What if I don't?

Check them so that you will get reading rights. It's possible you'll need yourself owner of the files first

(sudo) chown yourusername yourfile(s)

---

