---
title: "Ubuntu 17.10 Trash always empty"
date: 2018-02-15
forum: General Help
---

### Post by rainer.uwe on 2018-02-15
When I move items to the trash, either by right-clicking on them or by hitting the delete-button, the items item don't appear in the Trash bin. The trash is always empty and I am unable to recover any deleted files. 

My Ubuntu version is 17.10. The problem did not occur right after the update, but started only recently. 

Anybody has an idea why this is happening and what I can do to solve the issue? 

Rainer

---

### Post by cruzer001 on 2018-02-15
Those are Nautilus settings.  Look there and make sure you have it set to move to trash.  I don't have Nautilus installed, so I can't tell you the exact place to look.

---

### Post by Frogs Hair on 2018-02-15
It would be under preferences > behavior.

---

### Post by rainer.uwe on 2018-02-15
Had to set trash as root. Got it figured out here: [https://askubuntu.com/questions/288513/cant-move-files-to-the-trash](https://askubuntu.com/questions/288513/cant-move-files-to-the-trash)  ...

---

### Post by rainer.uwe on 2018-02-18
Thanks to everybody for looking into this.

---

### Post by cruzer001 on 2018-02-18
> **rainer.uwe said:**
> Had to set trash as root.
I guess if your happy with that solution you should go ahead and mark your thread "solved".

But thats not the way trash is suppose to be set.  _Everything_ in your Home directory is meant to be owned by you.  Root access (sudo) is required for everything else, the Home directory is the only exception.

---

