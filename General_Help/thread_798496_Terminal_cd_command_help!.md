---
title: "Terminal cd command help!"
date: 2008-05-18
forum: General Help
---

### Post by abyrne10 on 2008-05-18
Is it possible to use the cd command in the terminal when the folder you wish to navigate to has spaces in it?

e.g. cd /home/user/untitled folder/untitled folder

Every time I try this, I get the following:

bash: cd: /home/user/untitled: No such file or directory

Thanks!

---

### Post by cdtech on 2008-05-18
Yes, you have to encapsulate the directory with " " quotes.

cd /home/user/"untitled folder"

---

### Post by mali2297 on 2008-05-18
Either use backslash+space like this:
```

cd /home/user/untitled\ folder/untitled\ folder

```
or wrap it in quotes:
```

cd "/home/user/untitled folder/untitled folder"

```

---

### Post by abyrne10 on 2008-05-18
Thanks! :)

---

### Post by cdtech on 2008-05-18
welcome.......

---

