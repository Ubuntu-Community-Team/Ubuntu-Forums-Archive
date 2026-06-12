---
title: "SuperUser can't delete some files"
date: 2008-05-03
forum: General Help
---

### Post by XavierV on 2008-05-03
Hello there.

I hope you'll have a few ideas that will fix the following problem... It's blocking my packages update needed for 8.04

In the folder /usr/share/control-center-2.0/capplets I have four files i have no control on. Every action ends with a permission denied. My problem is that I have to remove these files to remove my J2RE package. 

Acting as a SuperUser, if I perform a simple 'ls' on the folder i get each file listed with permission denied.
When doing 'ls -al' on the folder, i get the same four lines, and then i get each file listed again like it should be with the command but every information is replaced with question marks ! At the end of each line, the file name is written in red over a black background.

Any of you have an idea on how to remove thse files ?

---

### Post by bingoUV on 2008-05-03
Could you paste here the output of the commands you tried instead of describing it in words?

---

### Post by barneystroud on 2008-06-23
I have the same problem, I have file that just will not delete.

---

### Post by nick_h on 2008-06-23
Have you tried deleting it with:
```
sudo rm <filename>
```

Please post the output of:
```
sudo ls -al <filename>
```

---

