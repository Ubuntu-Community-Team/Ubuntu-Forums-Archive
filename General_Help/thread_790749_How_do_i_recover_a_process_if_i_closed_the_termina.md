---
title: "How do i recover a process if i closed the terminal?"
date: 2008-05-11
forum: General Help
---

### Post by linuxd00 on 2008-05-11
hi,

This is a general linux question i think.
i wanted to install some software and ran on console:
 apt-get install LG3D

so it was downloading like 200MB

then by mistake i closed the window. Now aptget seems to keep running and the system monitor also says its still downloading at full speed.. but how do i recover the ouput it generates?
id like to know for example how long it will still take, how far it is downloading etc...
thanks for inputs...

---

### Post by madsmeg on 2008-05-11
Have you tried retyping into console? it will skip anything downloaded and get straight to where it left off...

---

### Post by linuxd00 on 2008-05-11
i "ended" it after a while. i had to delete all lock files.
and the packages were only partially downloaded thus corrupt.

so i did
sudo apt-get clean

and redownloadded the whole.

still i wonder if i could have regained it

---

### Post by madsmeg on 2008-05-11
Sorry i could not help :(

---

