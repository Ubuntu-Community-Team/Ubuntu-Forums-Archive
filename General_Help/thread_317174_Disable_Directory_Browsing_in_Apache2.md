---
title: "Disable Directory Browsing in Apache2"
date: 2006-12-12
forum: General Help
---

### Post by textguru on 2006-12-12
I have seen that Apache by default allows directory browsing on all subfolder. Is there a way tat we can disable its feature just for security purpose. I have seen one CMS created in PHP that it needs to have an index.php file per folder which is very tasky. Is there an easy way of handling this?

---

### Post by atoponce on 2006-12-12
Change the permissions on the directories.  This could be one option, depending on your needs (where 'dir' is the name of the directory):

```
sudo chmod 770 dir/
```

---

### Post by textguru on 2006-12-12
Is this the best option? what is the other option? Can we set it thru apache?

---

