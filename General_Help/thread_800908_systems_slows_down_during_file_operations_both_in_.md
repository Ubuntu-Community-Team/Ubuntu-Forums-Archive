---
title: "systems slows down during file operations both in GNOME and KDE"
date: 2008-05-20
forum: General Help
---

### Post by Rajiv_Nair on 2008-05-20
I've noticed that my (k)ubuntu hardy installation gets really slow while performing a file operation like copying or moving. This happens both in KDE and GNOME. Opening a video player like Smplayer while a copy operation is being performed takes a LOT of time. Plus it seems Xv doesnt work with Smplayer and compiz now. My graphics chipset is Intel 945GM. I didnt have any of the above issues with gutsy and Im seriously reconsidering moving back to Gutsy. Any ideas??.

---

### Post by stefangr1 on 2008-05-20
> **Rajiv_Nair said:**
> I've noticed that my (k)ubuntu hardy installation gets really slow while performing a file operation like copying or moving. This happens both in KDE and GNOME. Opening a video player like Smplayer while a copy operation is being performed takes a LOT of time. Plus it seems Xv doesnt work with Smplayer and compiz now. My graphics chipset is Intel 945GM. I didnt have any of the above issues with gutsy and Im seriously reconsidering moving back to Gutsy. Any ideas??.

About the computer being slow when performing file operations: are you sure your computer wasn't slow doing this when using the older Ubuntu versions? I believe it's normal. I also have it, especially when moving a file from one partition to another partition on the same physical disk IF that is also the physical disk that contains the root filesystem.

---

### Post by Rajiv_Nair on 2008-05-20
Its not that the system got a tad slower. That i can bear with. Here the system totally freezes for couple of seconds before responding again. And this problem has survived multiple reinstalls with multiple installation media(an alternate disc and shipped live cd)

---

### Post by chrisccoulson on 2008-05-20
Are you using swap? What is the output of:
```
free -m
```
...when you get the freezes?

If you're swapping, then it will be competing for disk bandwidth with the file operation and could slow the machine down.

---

### Post by Rajiv_Nair on 2008-05-20
total     used     free
swap       1639        36     1602

This is normal right?

---

### Post by tamoneya on 2008-05-20
```
tamoneya@ubuntu0:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3941       2124       1817          0        174        846
-/+ buffers/cache:       1103       2838
Swap:        11546          0      11546

```
According to your free -m you have no RAM installed and you are just using swap space.

---

### Post by chrisccoulson on 2008-05-21
> **tamoneya said:**
> ```
tamoneya@ubuntu0:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3941       2124       1817          0        174        846
-/+ buffers/cache:       1103       2838
Swap:        11546          0      11546

```
According to your free -m you have no RAM installed and you are just using swap space.

No RAM is not possible.

Rajiv_Nair - If that is just the 'swap' line from free -m, then it looks fairly normal. How much RAM do you have? Could you post the whole output of free -m?

---

### Post by tamoneya on 2008-05-21
> **chrisccoulson said:**
> No RAM is not possible.

Rajiv_Nair - If that is just the 'swap' line from free -m, then it looks fairly normal. How much RAM do you have? Could you post the whole output of free -m?

I realize that it isnt possible but if that was the full free -m output that would be what it was saying.  I was subtley asking for a more complete free -m.  I guess I should have been a little bit more explict.  Sorry if it caused confusion.

---

