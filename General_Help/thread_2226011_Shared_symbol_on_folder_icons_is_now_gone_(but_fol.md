---
title: "Shared symbol on folder icons is now gone (but folders still showing in Network)"
date: 2014-05-24
forum: General Help
---

### Post by 777funk on 2014-05-24
They just disappeared on us a couple weeks ago. Also if I right click and go to sharing options these folders don't have a ticked box on "share this folder".

However, they're showing in the network under the Ubuntu machine. What's happening?

---

### Post by Morbius1 on 2014-05-24
Do they show as shared in the output of this command:
```
net usershare info --long
```
Oh, and by the way what version of Ubuntu are you using .

---

### Post by 777funk on 2014-05-24
Ha! Sorry! I should have put that down. I've got 12.04. 

And all the folders do show in the terminal.

---

### Post by Morbius1 on 2014-05-25
That is a very old bug - I'm talking years here.

Samba is the red haired stepchild of Linux so when it comes to something like this which is purely graphical there is little chance it will ever get fixed

I've taken a philosophical approach to this issue. When you create a Classic Samba share by defining it in smb.conf itself there is no share emblem on the folder either so I don't expect to see one when using nautilus-share.

---

