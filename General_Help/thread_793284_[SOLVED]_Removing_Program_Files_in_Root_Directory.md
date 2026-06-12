---
title: "[SOLVED] Removing Program Files in Root Directory"
date: 2008-05-13
forum: General Help
---

### Post by Patrick793 on 2008-05-13
Well, I used to use Avast! AntiVirus. I know that Linux doesn't have viruses, and I was only using it to protect all of my friends, because they use Windows. Anyway, I decided to let them learn how to defend themselves, and removed avast. But, there was a time I ran avast with the sudo command. Now that avast is removed, there was an un-needed program folder in /home/patrick called .avast. Deleted it, like I do with all of the un-needed ones. But, since I ran avast with the sudo command one time, there is an un-needed program folder in /root/ named .avast.

How can I remove this?

Thanks

---

### Post by koenn on 2008-05-13
```
 sudo rm -r /root/.avast 
```

---

### Post by Patrick793 on 2008-05-13
Thanks!

---

### Post by koenn on 2008-05-13
welcome

---

