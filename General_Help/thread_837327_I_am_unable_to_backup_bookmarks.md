---
title: "I am unable to backup bookmarks"
date: 2008-06-22
forum: General Help
---

### Post by sofasurfer on 2008-06-22
I used to be able to backup my bookmarks under the "organize bookmarks" options.

Now I am not longer able to backup biikmarks. I can back them up to desktop but am unable to backup to anywhere in my home folder. I have enabled read/write permissions on directories and on enclosed files. What could be the problem?

---

### Post by jimbob on 2008-06-22
Can you not select the Import and Backup drop down menu instead of Organize:

---

### Post by sofasurfer on 2008-06-22
I found the problem. I guess I created some /home folders as sudo. Apparently this created them with the 'user' being 'root'. I had to change their ownership to 'daryl'.
So much for my little mind to keep track of. Sheesh!!

---

