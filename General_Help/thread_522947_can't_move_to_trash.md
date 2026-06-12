---
title: "can't move to trash"
date: 2007-08-11
forum: General Help
---

### Post by tubunu on 2007-08-11
Whenever I want to delete a file I get an error message:

```
Could not write to file /home/user/.local/share/Trash/info/file.trashinfo.
```

How can I fix that? Thank you.

---

### Post by yorkie on 2007-08-11
If you go to top panel click on places then on home folder file browser opens click on veiw then show hidden files scroll down .trash directory listed 
you will need to edit path to this dir

---

### Post by tubunu on 2007-08-13
Thanks, but ummm I don't see .trash directory there.. :confused:

---

### Post by tubunu on 2007-08-14
hey there all you *buntu geeks, help out a fellow *buntu user... :)

---

### Post by tubunu on 2007-08-18
:confused:

---

### Post by qqzhenyi on 2007-08-22
Well this may sound stupid but maybe you can try

```
sudo chmod a+w /home/user/.local/share/Trash/info/file.trashinfo
```

---

### Post by tubunu on 2007-08-30
Thanks, that solved it! :D

---

