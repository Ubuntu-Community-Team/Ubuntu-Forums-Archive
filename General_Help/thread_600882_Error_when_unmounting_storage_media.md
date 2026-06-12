---
title: "Error when unmounting storage media"
date: 2007-11-02
forum: General Help
---

### Post by Mr. Picklesworth on 2007-11-02
Whenever I unmount an external storage media, I get an error that it can not be unmounted (this is actually incorrect; it is), with the reason being that it cannot remove "the directory". It is then followed by another empty dialog with the error icon. Rather annoying.

This is probably the directory in /media that it is talking about, and I can see that it has read / write permissions for root, but only read permissions for other users and the root group.
Presumably, there is a permissions issue, and probably not a common bug. (Maybe related to upgrading, though... should be looked into, along with that incoherent error message).

Hopefully all I must do is change the permissions for /media. Can anyone tell me what that *should* be set to?

---

### Post by Pumalite on 2007-11-02
You could give permission to everyone if OK. with you:
sudo chmod 777 /media/blah, blah, blah

---

### Post by Mr. Picklesworth on 2007-11-02
Yep, that is how I have set it, but I do like having things configured the official way.

Unfortunately, it actually didn't work :(
Still get the same error. The directory in /media is indeed removed, however.

---

### Post by Pumalite on 2007-11-02
You might want to try this:

Open a terminal and
Code:

sudo chown yourusername /whereveritismounted

---

