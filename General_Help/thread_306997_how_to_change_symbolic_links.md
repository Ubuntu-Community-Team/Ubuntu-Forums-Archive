---
title: "how to change symbolic links?"
date: 2006-11-25
forum: General Help
---

### Post by jaind on 2006-11-25
Hi,

I earlier installed an older version of gcc(gcc-3.3) and created a symbolic link from gcc-3.3 to gcc as:

cd /usr/bin
sudo ln -s gcc-3.3 gcc

However, i now installed "gcc-2.95" and  have to create a symbolic link between "gcc-2.95" and "gcc" when i do: 

cd /usr/bin
sudo ln -s gcc-3.3 gcc

--im unable to link and i get the following message:
ln: creating symbolic link `gcc' to `gcc-2.95': File exists

-- i probably have to delete the old symbolic link but i dont know how to find it and delete it.

Thanks!

PS: my apologies to "taurus" for sort-of-repeating this post. I need to sort this out quick. hence.

---

### Post by moshuptrail on 2006-11-25
just cd back to the directory and then do a ls -l
the symlinks will show in teal with an arrow and it will show what they point to. 

yes.  you must rm (delete) them and then re-create

---

### Post by highneko on 2006-11-25
sudo rm 'gcc-2.95' #in the path it's located, then try to make it.

---

### Post by fritz_monroe on 2006-11-25
Yep, you need to break the first symbolic link before creating the other.  As for finding the original link, have you tried doing a which?

```
which gcc
```

It should tell you the path.

---

### Post by jaind on 2006-11-25
I was able to solve my problem. Thanks!!

I found that i can also do:
sudo -ln -s gcc-2.95 gcc --force

:)

---

