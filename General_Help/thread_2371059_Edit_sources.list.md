---
title: "Edit sources.list"
date: 2017-09-10
forum: General Help
---

### Post by Crimple on 2017-09-10
Hi.

I was trying to edit the sources.list from the terminal using 
```
sudo nano /etc/apt/sources.list
```

but I made a mess.
 I closed the terminal and when I went to *sudo nano* again I got this:
[ATTACH=CONFIG]276679[/ATTACH]

I rebooted and the same.
I went to /etc/apt/ and found a sources.list.save1 with my messed up edit (besides a sources.list.save untouched). I deleted it and rebooted but when *sudo nano* I got the same as the above attachment.

Any ideas?
Thanks.

---

### Post by oldos2er on 2017-09-10
If you want to regenerate a new sources.list, see [https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/)

If you want to restore sources.list.save, try ```
sudo cp /etc/apt/sources.list.save /etc/apt/sources.list
```

---

### Post by deadflowr on 2017-09-10
If you still have the one .save version, then just move it back, (or copy)
```
sudo mv /etc/apt/sources.list.save /etc/apt/sources.list
or
sudo cp /etc/apt/sources.list.save /etc/apt/sources.list
```
In these circumstances copy maybe better as it will preserve the .save version in case things go awry.
Move moves the whole thing and you lose the preserved .save version.

ninja'd

---

### Post by Crimple on 2017-09-10
Restoring .save didn't help but I found where the problem was, I left the terminal just by closing it and not by using nano's tools (exit, save etc.)
Thanks a lot for your answers :p

---

