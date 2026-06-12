---
title: "reinstall packages after fresh install"
date: 2007-01-18
forum: General Help
---

### Post by vinboy on 2007-01-18
hi,
I'm wondering if there is a file list somewhere which record what we install.

When I do a fresh Ubuntu install next time, i can just ask apt-get to install everything in that list, instead of scanning over and over and over through the complete package list and try to remember which one to install.

](*,)

---

### Post by bodhi.zazen on 2007-01-18
Not exactly, but look here:

List of installed packages:
		[http://duggmirror.com/linux_unix/Ubuntu_tricks_how_to_create_a_list_software_and_use_it_to_restore_your_pc/](http://duggmirror.com/linux_unix/Ubuntu_tricks_how_to_create_a_list_software_and_use_it_to_restore_your_pc/)

```
dpkg --get-selections | grep -v deinstall > ubuntu-files
```

---

### Post by vinboy on 2007-01-18
thanks alot.
that's what I was looking for.

---

