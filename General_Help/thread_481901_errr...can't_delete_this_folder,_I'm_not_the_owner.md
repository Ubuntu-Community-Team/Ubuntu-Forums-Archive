---
title: "errr...can't delete this folder, I'm *not* the owner..."
date: 2007-06-23
forum: General Help
---

### Post by tsav87 on 2007-06-23
I need to delete this folder but it's locked to root and I don't know how to delete it.  How do I do it?

Here are some screen shots...

---

### Post by Ng Oon-Ee on 2007-06-23
You could either use

sudo rmdir

in the terminal (this is easiest if your folder is empty), or

sudo chown *your username* *insert folder path/name here*

then proceed to delete.

---

### Post by tsav87 on 2007-06-23
You da man!  Thanks!

---

### Post by Ng Oon-Ee on 2007-06-23
You're welcome =).

I'm new too, and had to learn up permissions pretty quick. Have fun!

---

