---
title: "ubuntu 14.04 trash won't empty."
date: 2014-09-20
forum: General Help
---

### Post by mj360 on 2014-09-20
i have 5 files in the trash dont wont delete. no matter how much times i empty it. when i put other files in it, they deletes. but it will takes a long time it empty. about 3 to 4 mins to empty. but the other 5 files are still there. do anyone knows how to fix this ? thanks.

update. it's files on my external hard drive ubuntu wont delete. when it's not plug in, the trash is empty. but when it's plug in. it comes back.

---

### Post by ibjsb4 on 2014-09-20
Maybe you are not the owner of those files.  Try ..

```
sudo rm -rf ~/.local/share/Trash
```

---

### Post by mj360 on 2014-09-20
i am the owner. so i did the sudo rm -rf ~/.local/share/Trash it ask for my password but it did nothing. what else do i do ?

---

### Post by ibjsb4 on 2014-09-21
```
gksudo nautilus
```
And try to remove them one at a time from ~/.local/share/Trash/files/
Also check root trash
/root/.Trash

---

### Post by mj360 on 2014-09-23
i tried it but it said this "Error removing file: Input/output error" but i find out it's my external hard drive. when it's not plug in, the trash goes away. but when it's plug in, it returns.

---

### Post by ibjsb4 on 2014-09-23
Look (search) for Trash folder(s) on the external HDD.

How is it partition, whats on it?  If its just partition ext4 and your using it for storage, there will be a '.Trash' folder.  Its a hidden folder.

---

### Post by mj360 on 2014-09-24
it partition is ntfs. and i uses it as a storage. how do i find the trash folder ?

---

### Post by ibjsb4 on 2014-09-24
I do not use ntfs, but I would think nautilus would be able to see a trash folder and remove it or at least move it for deletion.  Got windows installed?  Delete with windows.  Anyway, thats my best guess about ntfs.  Maybe let this thread die and start a new one showing ntfs as the problem.

---

