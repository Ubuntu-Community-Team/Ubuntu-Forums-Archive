---
title: "Hidden Files"
date: 2014-06-13
forum: General Help
---

### Post by borgward on 2014-06-13
Command line to find hidden files in /home?

---

### Post by SuperFreak on 2014-06-13
Not sure of the command line but if you press CTL H while in your directory(in Nautilus or whatever file viewer you use) it will reveal all the hidden folders and files. I think there is also a setting in Nautilus which will keep it that way

---

### Post by deadflowr on 2014-06-13
```
ls -a
```
will list **all** files, and folders in home, if that is where you are when you run it.
otherwise 
```
ls-a /home/user
```

---

