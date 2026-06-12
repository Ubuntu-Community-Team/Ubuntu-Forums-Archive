---
title: "Change permission on a file"
date: 2014-01-19
forum: General Help
---

### Post by sammiev on 2014-01-19
Hi good folks,

I used chmod to change permission of a file to work on. Now I want to change it back but I do seem to be having problems.

rwxr-xr-x was the file

I used chmod 751 to change it back but get rwxr-r-x

Thanks

---

### Post by codemaniac on 2014-01-19
do you want to change it back to rwxr-xr-x ?
i think you should use 755 instead of 751.

```
fego@production:~$ touch test.dat
fego@production:~$ ll test.dat
-rw-r--r-- 1 fego fego 0 Jan 19 23:58 test.dat
fego@production:~$ chmod 755 test.dat
fego@production:~$ ll test.dat 
-rwxr-xr-x 1 fego fego 0 Jan 19 23:58 test.dat*

```

---

### Post by TheFu on 2014-01-19
Something doesn't look correct.
Please copy/paste the output of **ls -l {file}** before and after changing the permissions. Also include the exact, copy/pasted, commands used.

---

### Post by sammiev on 2014-01-19
Thanks folks it was 755 instead of 751. 
I will mark this as solved.

---

