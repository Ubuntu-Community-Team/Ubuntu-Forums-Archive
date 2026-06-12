---
title: "Corrupted HDD name"
date: 2007-04-12
forum: General Help
---

### Post by dnz on 2007-04-12
A week ago my hda1 disk's name became something like this:

[img]http://server2.uploadit.org/files/Zeratu1-corrupted.jpg[/img]

I can still use it without any errors (/media/hda1) but it makes me sick :D 

How can I fix this?

---

### Post by ajgreeny on 2007-04-12
What should it read, hda?  I don't think you can change the name by right clicking on the icon, but it's worth a try.  I imagine it will need to be changed as root, but how you actually find where the icon is named in your filing system, I'm not sure, but assume that if you do a search for the name you think it should be you may get lucky.

---

### Post by mac.ryan on 2007-04-12
Amongst others, it could be a problem with locale settings... did you change those anytime lately?

Also, what does it reads in basic/name if you right-click on the desktop icon? (The proper name or the corrupted one?)

---

### Post by dnz on 2007-04-12
It happened before i updated my ubuntu from 6.06 to 6.10.
Actually i dont know whether i change any local settings or not

In properties it seems like : ~d=_
but when i open it, it writes: hda1 (normal name) at the title.
In /dev/disk/by-label directory it writes: __d_=______

I cant rename it as a root too.

---

### Post by RJARRRPCGP on 2007-04-12
Getting a corrupted HDD name usually is because of a bad IDE cable connection. But then you usually can't access it without an error if that was the case.

---

### Post by dnz on 2007-04-12
I dont think there is a connection problem with PC. It works quite normal. Also i installed ubuntu to its second partition.

I dont know its a useful information but Im using Asus A6Q00VC laptop

---

### Post by mac.ryan on 2007-04-12
> **dnz said:**
>  In /dev/disk/by-label directory it writes: __d_=______
I cant rename it as a root too.

Does it mean you already tried

```
sudo e2label /dev/hda1 *FancyNameOfYourChoice*
```(assuming it is an ext2/3 partition)?

To me it looks like your box mounts the HD trough UUID, but then display a label, that for some reason went weird... Just guessing, though. I may well be wrong.

---

