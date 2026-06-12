---
title: "installing package problem"
date: 2007-09-30
forum: General Help
---

### Post by elidoperezmd on 2007-09-30
i have 3 packages on my desktop: Skype, VirtualBox, and Picasa, waiting to be installed: I downloaded them all this afternoon.
the problem is that whe i click on them and open the GDebi Package Installer,  it says that the file must me corrupted or i am not allowed to run the files, check the permissions.

i know for a fact that there is no way that the 3 files are corrupted.
Will it help open them grom the terminal? i don't know to do it from the terminal... Newbie here

how to install these files. i need help with this matter. Thanks for your time

---

### Post by chuckyp on 2007-09-30
In a terminal you would do something like:
```

sudo dpkg -i packagename.deb

```

Perhaps the user you are trying with is not an adminsitrator and just a default user?

---

### Post by elidoperezmd on 2007-10-01
tried... dont work, any ideas?

---

### Post by forestpixie on 2007-10-01
might be tied up with your other thread - I've posted there

---

