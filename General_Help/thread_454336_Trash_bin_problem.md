---
title: "Trash bin problem"
date: 2007-05-25
forum: General Help
---

### Post by hakimaki on 2007-05-25
Anytime I delete something from a different partition thats not my main, it goes into the .trash-user folder rather than my trashbin on my desktop.  Never had this problem with my edgy install.  Its become quite the nuisance, any ideas?

---

### Post by booljayj on 2007-05-26
I had this same problem, it is quite annoying.

I ended up just using the rm command to get rid of files. To get rid of a whole folder simply type

```
sudo rm -R path
```
where path is the path to the folder, make sure you type the mounted path (/media/...)

A little while ago I read about a small program that adds a 'delete' command to the right-click menu, which surpasses the trash bin. I don't know what happened with it, though.

---

