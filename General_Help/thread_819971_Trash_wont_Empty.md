---
title: "Trash wont Empty"
date: 2008-06-05
forum: General Help
---

### Post by Zidoud on 2008-06-05
Hello i am having a problem with my trash bin. There are two things in my trash bin that no matter what i do i cant get it to remove them. what can i do to get rid of them? thank you!

---

### Post by Lord Xeb on 2008-06-05
What version of Ubuntu are you using and do you get any errors when trying to delete the items?

---

### Post by iaculallad on 2008-06-05
Open up your terminal:

For Hardy:
```
rm -rf ~/.local/share/Trash/files/*
```

Or if you're using Gutsy:

```
sudo rm -rf ~/.Trash/*
```

---

### Post by Zidoud on 2008-06-08
I use version 8.04 and when you right click on the trash icon and click empty trash it goes trough the process of actually emptying it but when you open the folder it is still there. Then when you try and delete the file(and only this file) it tells me that i dont have the permission to delete the file but under permissions i have complete access.

---

