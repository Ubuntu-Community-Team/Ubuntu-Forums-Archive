---
title: "problem with hardy startup"
date: 2008-05-03
forum: General Help
---

### Post by zay2 on 2008-05-03
ive installed hardy on 3 computers, my eeepc (works amazingly well), brothers hp laptop (worked extremely well too) and mothers p c - hangs on startup.

when i run it on live cd it starts up just fine, but when i install it in her comp it wont get to log in screen. 

i wont get log in screen after # Running local boot scripts (/etc/rc.local) -- file is empty anyway.

she has some somputer with intel all in one motherboard, via graphics chips 512mb memory.. all i can tell by  heart.

i tried both amd64 and i386 hardy heron kde 3.5.9. live cd's. exactly same results with both of them. even tried different filesystems: reiserfs and ext3.

Can anyone help me out?

Alan

---

### Post by ghost_ryder35 on 2008-05-03
> **zay2 said:**
> ive installed hardy on 3 computers, my eeepc (works amazingly well), brothers hp laptop (worked extremely well too) and mothers p c - hangs on startup.
 
when i run it on live cd it starts up just fine, but when i install it in her comp it wont get to log in screen. 
 
i wont get log in screen after # Running local boot scripts (/etc/rc.local) -- file is empty anyway.
 
she has some somputer with intel all in one motherboard, via graphics chips 512mb memory.. all i can tell by heart.
 
i tried both amd64 and i386 hardy heron kde 3.5.9. live cd's. exactly same results with both of them. even tried different filesystems: reiserfs and ext3.
 
Can anyone help me out?
 
Alan
are you saying you get booted into a console session with no gui interface?  try hitting enter and see if you are prompted to login.  if so login and type 
```

startx

```

---

### Post by zay2 on 2008-05-03
the running boot scripts is on the window that opens with ctr alt f8. the screen where kdm runs (f7) .  there is just blinking cursor. yeah i can switch screens and log in and do startx, but that gives me error:

Fatal server error:
no screens found

waiting for X server to begin accepting connections
giving up

and then 2 errno's 104 and 3 by xinit


thats it

---

### Post by comandrei on 2008-05-03
```
 sudo dpkg-reconfigure -phigh xserver-xorg
``` in a recovery mode console should do the trick. Try the Fix X option in recovery mode afterwards if this dosen't work

---

### Post by zay2 on 2008-05-03
thanks. i tried both, but neither of them worked

edit1:what puzzles me is why it works with live cd, but not when i run it from hd

edit2: replaced xorg.conf on hd with the xorg conf live cd uses - no change. guess the problem is not i xorg?

edit3: foud [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

downloaded drivers and installed them. it works fine now

---

