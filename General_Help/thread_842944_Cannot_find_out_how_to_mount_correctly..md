---
title: "Cannot find out how to mount correctly."
date: 2008-06-27
forum: General Help
---

### Post by !@!@! on 2008-06-27
OK-
Here is the problem I am having.
I am using Wubi, and I want my steam files to show up the same in Linux.
I thought there was a way I could do a sort of redirection.
This is the general idea of what I want done-
```
sudo mount --bind /host/Program Files/Steam/steamapps/common /home/tanner/.wine/drive_c/Program Files/Steam/steamapps/common
```
that did not work at all though.

So just to sum up-
i want files in a different location to show up in the dir I specify.

---

### Post by x1a4 on 2008-06-27
Either enclose the paths in quotes 
```
sudo mount --bind '/host/Program Files/Steam/steamapps/common' '/home/tanner/.wine/drive_c/Program Files/Steam/steamapps/common'
```

or escape the spaces.  
```
sudo mount --bind /host/Program\ Files/Steam/steamapps/common /home/tanner/.wine/drive_c/Program\ Files/Steam/steamapps/common
```

---

### Post by !@!@! on 2008-06-28
> **x1a4 said:**
> Either enclose the paths in quotes 
```
sudo mount --bind '/host/Program Files/Steam/steamapps/common' '/home/tanner/.wine/drive_c/Program Files/Steam/steamapps/common'
```

or escape the spaces.  
```
sudo mount --bind /host/Program\ Files/Steam/steamapps/common /home/tanner/.wine/drive_c/Program\ Files/Steam/steamapps/common
```

thanks dude! :D

---

### Post by sisco311 on 2008-06-28
If you want to do this automatically at boot time add this line:
```
/host/Program**\040**Files/Steam/steamapps/common       home/tanner/.wine/drive_c/Program**\040**Files/Steam/steamapps/common       none       bind
```to the /etc/fstab

---

### Post by x1a4 on 2008-06-29
> **!@!@! said:**
> thanks dude! :D

No problem.  Make sure you click the 'Thank you' icon--the medal on the right side of the post you're thanking for next to the 'quick reply' icon.  ;)  Also, whenever your issue is solved, mark the thread as solved.  Click 'Thread Tools' > 'Mark thread as solved' at the top of the thread.

---

