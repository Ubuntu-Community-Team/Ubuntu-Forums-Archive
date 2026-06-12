---
title: "remove the symlink?"
date: 2020-02-04
forum: General Help
---

### Post by maclenin on 2020-02-04
Essentially, I am trying to remove the symlink.

**a**, **b** and **c** are directories

**test** is a file

1. symlink creation: ```
sudo ln -sfr a/test b/c
```
2. symlink removal: ```
rm b/c
```
2.a. yields:```
rm: cannot remove 'b/c': Is a directory
```

Thanks for any guidance!

---

### Post by TheFu on 2020-02-04
Sorry - why use **sudo** to make the link?  If so, sudo is needed to remove it.

Works here:
```
 cd /tmp
/tmp$ mkdir foo
/tmp$ cd foo/ 
/tmp/foo$ mkdir a b
/tmp/foo$ touch a/test
/tmp/foo$  ln -sfr a/test b/c
/tmp/foo$ ls -RF
.:
a/  b/

./a:
test

./b:
**c@**
/tmp/foo$ rm b/c
/tmp/foo$ 

```

---

### Post by SeijiSensei on 2020-02-04
To remove a directory use "rm -rf directoryname".  Make sure there's nothing in the directory you wish to save.

---

### Post by maclenin on 2020-02-04
Thanks for the quick replies, folks!

Here's the "live" example (while trouble-shooting scanner set up):

**libsane-epkowa*** is a file
**sane** is a directory

1. created the symlink:
```
sudo ln -sfr /usr/lib/sane/**libsane-epkowa*** /usr/lib/x86_64-linux-gnu/**sane**
```

2. would now like to remove the symlink:
```
sudo rm /usr/lib/x86_64-linux-gnu/**sane** 
```

However, **sane** is a directory containing many files other than the target (**libsane-epkowa***) and I don't want to "chuck the baby with the bathwater".

Thanks for the help!

---

### Post by deadflowr on 2020-02-04
use unlink.

---

### Post by maclenin on 2020-02-04
In this way?

```
sudo unlink /usr/lib/x86_64-linux-gnu/sane
```

Cheers!

---

### Post by deadflowr on 2020-02-04
Did it remove the symlink?

---

### Post by maclenin on 2020-02-04
Negative. I get the same error for both "rm" and "unlink":
```
*: cannot * 'b/c': Is a directory
```
However (with reference to my op), an **ls -l** in directory c yields (the symlink I am trying to rm/unlink):
```

b/c$ ls -l
total 0
lrwxrwxrwx 1 root root 12 Feb  4 16:28 test -> ../../a/test
```
Perhaps, a clue?

---

### Post by deadflowr on 2020-02-04
Then just unlink test
Assuming b/c is the current the working directory
```
unlink test
```

if b/c is not the current working directory
```
unlink b/c/test
```

---

### Post by maclenin on 2020-02-04
That did it. Thanks.

Perhaps, a couple of create / remove / unlink symlink scenarios (where a, b and c are in the current working directory):

symlink to **directory**
```
ln -sfr a/test b/**c**
rm b/c/test
unlink b/c/test
```

symlink to **file**
```
ln -sfr a/test b/c/**target**
rm b/c/target
unlink b/c/target
```

Thanks, again, for the guidance!

---

