---
title: "Can't delete a file"
date: 2007-01-16
forum: General Help
---

### Post by Linux-Musician on 2007-01-16
ugh linux must hate me

I recently installed tremulous. But now I need to delete the old file in /usr/local/games so that I can install a completely new one.  The problem is whenever I try to delete it tells me there is restricted access to the **TRASH BIN**

I've CHMOD'd the entire file.  I've tried CHMOD'd the trash. this is driving me into a whole new level of pissed off.

help please.

---

### Post by taurus on 2007-01-16
Use the sudo command.

```
sudo rm **filename**
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Linux-Musician on 2007-01-16
musician@musician-desktop:~$ sudo rm /usr/local/games/nottremulous
Password:
rm: cannot remove `/usr/local/games/nottremulous': Is a directory

---

### Post by taurus on 2007-01-16
```
sudo rm -rf /usr/local/games/nottremulous
```

---

### Post by Linux-Musician on 2007-01-16
> **taurus said:**
> ```
sudo rm -rf /usr/local/games/nottremulous
```

<3

---

