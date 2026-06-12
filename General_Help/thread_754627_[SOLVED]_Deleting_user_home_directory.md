---
title: "[SOLVED] Deleting user home directory"
date: 2008-04-14
forum: General Help
---

### Post by tommyhakinen on 2008-04-14
I was having 2 users on my gutsy. Recently, I just deleted one of them from Systems > Administration > Users and Groups. After I successfully deleted it, I found that the deleted user's home directory still left behind. How do I delete this?

thank you.

best regards,

tommy

---

### Post by sekinto on 2008-04-14
rm -rf /home/<user>

If it says you don't have permissions put a sudo in front of that.

---

### Post by ayoli on 2008-04-14
```
sudo rm -rf /home/<deleted_username>
```
or 
```
gksudo nautilus
```
move to /home, then delete the folder.

---

### Post by aysiu on 2008-04-14
I would favor the *gksudo nautilus* method.

If you type *sudo rm -rf /home/username* and accidentally hit Enter too quickly, you might be deleting more than you'd originally intended.

---

### Post by sekinto on 2008-04-14
That's very true. I just suggested that method because it seems a lot simpler to just do it all from the command line.

---

### Post by tommyhakinen on 2008-04-14
Thank you so much for the quick reply. It works.

---

### Post by hyperair on 2008-04-14
@aysiu: How about this then:
```
cd /home && sudo rm -rf <username>
```

---

### Post by MrFSL on 2008-04-14
How about discounting the "force" option since it is really what makes the rm command dangerous anyways?

Personally I suggest:
```
sudo rm -ir /home/username
```

The "i" option forces interactive mode and can help from destroying things accidentally.

---

