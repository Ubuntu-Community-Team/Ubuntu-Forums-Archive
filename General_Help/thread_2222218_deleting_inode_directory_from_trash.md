---
title: "deleting inode directory from trash"
date: 2014-05-05
forum: General Help
---

### Post by RISHIKESHGAWADE on 2014-05-05
Hi,
I have this problem where I deleted an inode directory from 'home'. Now the directory sits in Trash and i am not able to remove it from there. I tried to remove it by inode number but no success.
Although i doesn't consume space, my computer freezes whenever i try to access Trash.
Any help is appreciated...

---

### Post by ajgreeny on 2014-05-05
See if you can empty trash in command line with ```
rm .local/share/Trash/files/*
```

---

### Post by RISHIKESHGAWADE on 2014-05-06
I tried to empty trash from terminal but doesn't help. As said earlier, it is an inode directory and I tried to remove it by its inode number but that also didn't help. by the way, the directory shows 0 bytes. I don't care if it stays there but my problem is the system freezes when i access trash...

---

