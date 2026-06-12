---
title: "rar in ubuntu?"
date: 2008-05-20
forum: General Help
---

### Post by oktob3r on 2008-05-20
i'm completely new to ubuntu and i'm just trying to figure out how to open rar files in linux... unfortunately i can't figure out what the instructions are trying to tell me. so any step by step instructions would be great. thanks in advance.

---

### Post by tamoneya on 2008-05-20
you just need to install the rar package then it will be automatically recognized by the archive manager ( you can double click on it to open it).  Enter the following commands in terminal (applications -> accessories -> terminal)```
sudo apt-get update
sudo apt-get install rar
```

---

### Post by mali2297 on 2008-05-20
Open the package manager Synaptics. Go to **Settings -> Repositories** and check that you have the *multiverse* repository enabled. Then use the search function to find the package **unrar**. Install it.

After this, you should be able to extract rar archives with the default archive manager.

---

