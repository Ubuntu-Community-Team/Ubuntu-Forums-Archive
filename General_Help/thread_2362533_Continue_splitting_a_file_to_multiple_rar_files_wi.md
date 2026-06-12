---
title: "Continue splitting a file to multiple rar files without overwrite problem"
date: 2017-05-30
forum: General Help
---

### Post by papampi on 2017-05-30
I need to split a big 100Gb video file into 2Gb rar files, 
but I have to do it in 10 part per session 
rar gives error and wont continue if the part exists

```
root@static:# ls -la
-rw-r--r-- 1 root root 100219669504 may    11 06:45 testfile
-rw-r--r-- 1 root root  2000000000 may    30 07:19 test.part01.rar
-rw-r--r-- 1 root root  2000000000 may    30 07:19 test.part02.rar

```

```
# rar a -m0 -v2000000 test testfile 
Creating archive test.rar
Adding    testfile                           
Calculating the control sum     
test.part01.rar already exists. Overwrite it ?
[Y]es, [N]o, [A]ll, n[E]ver, [R]ename, [Q]uit N
Cannot rename test.rar to test.part01.rar
No such file or directory
```

what am I doing wrong ?

---

