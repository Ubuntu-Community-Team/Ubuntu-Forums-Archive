---
title: "Ubuntu will not login anymore."
date: 2008-05-17
forum: General Help
---

### Post by blah569 on 2008-05-17
Okay, so I ran this command:

```

sudo sh wubi-add-virtual-disk /home 2000

```

I wished to add two GBs to my Ubuntu that I installed from Wubi on Windows.  Now, whenever I attempt to login to Ubuntu, Ubuntu tells me that "User's $HOME/.dmrc is being ingnored."  Windows still boots fine.  Also, one thing I noticed, is that it looks like my Windows disk space increased two GBs.  Any help to fix my Ubuntu that was installed from Wubi?

Edit1:  I just thought that I would say that I can login with failsafe ternimal.

---

### Post by ago on 2008-05-18
You can revert the changes by unmounting /home, removing the /home line in /etc/fstab and renaming /home.bu to /home

---

