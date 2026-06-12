---
title: "can't delete *.php file!!!"
date: 2008-06-12
forum: General Help
---

### Post by eerojms5 on 2008-06-12
I made index.php file on desktop and tried to copy it to another place! Then i got

cp: cannot stat `/index.php': No such file or directory

and afterward when i tried to delete it then it said exactly the same thing!
I just can't understand!
Hope you can help!

---

### Post by prince_niceguy on 2008-06-12
Login into the recovery mode and select root shell.


run the following command

```
sudo fsck /home
```

Hopefully that should resolve the issue.

---

