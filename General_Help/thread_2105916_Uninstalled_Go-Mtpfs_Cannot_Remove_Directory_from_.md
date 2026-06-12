---
title: "Uninstalled Go-Mtpfs Cannot Remove Directory from /media"
date: 2013-01-17
forum: General Help
---

### Post by mamamia88 on 2013-01-17
It's really starting to annoy me.  I installed go-mtpfs and it created a directory called "MyAndroid" in /media.  And even running rm -R /media/MyAndroid as root fails to delete the folder.  Any help would be appreciated.

---

### Post by ajgreeny on 2013-01-17
It is probably a read-only folder.

Let's see the output of ```
ls -l /media
```

---

### Post by mamamia88 on 2013-01-17
> **ajgreeny said:**
> It is probably a read-only folder.

Let's see the output of ```
ls -l /media
```

it was read only but i used chmod -R +rwx /media/MyAndroid and then tried deleting to no avail

---

### Post by ajgreeny on 2013-01-17
Is there anything in the folder? If so remove that first and then you may be able to delete it.

---

### Post by mamamia88 on 2013-01-17
> **ajgreeny said:**
> Is there anything in the folder? If so remove that first and then you may be able to delete it.

There was nothing in the folder.   Oh well i just did a fresh install to get rid of it.  not a big deal since i have my own little script i wrote to install all my software for me and remove everything i don't want.   So all i really had to do was customize my panels again.

---

