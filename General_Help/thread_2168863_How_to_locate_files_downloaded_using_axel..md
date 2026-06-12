---
title: "How to locate files downloaded using axel."
date: 2013-08-19
forum: General Help
---

### Post by rkarulkar94 on 2013-08-19
I just tried to download an iso image using axel, but I cannot see the file even though I can see it eating up the space. How can I locate the file? Usually the files show up in the home folder, but there's nothing there right now. I tried searching for the file, but I still could not find it. I am using ubuntu 13.04

---

### Post by Cheesemill on 2013-08-19
What directory where you in when you used axel?

Unless you tell it otherwise it downloads files into the current working directory.


Edit - You can find all the iso files in your home directory with the following command...
```
find ~ -name *.iso
```

---

