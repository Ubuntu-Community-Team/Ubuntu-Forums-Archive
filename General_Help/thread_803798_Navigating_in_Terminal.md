---
title: "Navigating in Terminal"
date: 2008-05-22
forum: General Help
---

### Post by sumone on 2008-05-22
Hi

I need to get to /dev in the terminal to chown a particular file. Terminal opens with my home folder and I do not seem to able to cd -- up to the file system. I can click on it but not navigate to it.

Thanks in advance

---

### Post by y-lee on 2008-05-22
**cd /dev** doesn't work?

---

### Post by SOULRiDER on 2008-05-22
To go up one level use 
```
cd ..
```**mind the space between d and .**

You can also use cd to go to a directory. ls to list files and directories and cd ~ to go to your home.

---

### Post by rxtx on 2008-05-22
Or just chown the file directly.

```
sudo chown <user> /dev/<name of file>
```

---

