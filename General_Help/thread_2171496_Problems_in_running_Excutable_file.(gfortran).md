---
title: "Problems in running Excutable file.(gfortran)"
date: 2013-08-31
forum: General Help
---

### Post by Fukun_XU on 2013-08-31
Hi All, I'm a new user of Linux (OS version: Ubuntu 13.04). I encountered a problem when I tried to run EXCUTABLE document compiled by GFORTRAN. The commands are as follows:

$ gfortran test.f90 -o test
(there is no any error and warning response. So I think this step is OK)
$ chmod +x test
$ test
(No any response)
$ ./test
bash: ./test: Permission denied.
$ sudo ./test
sudo: ./test: command not found

*****************************
PS: the code of test.f90:
PROGRAM TEST
WRITE(*,*)'HELLO'
END

I finally failed to find solution about this. Anyone encountered the same problem before? Or any idea? 
Thanks for your attention.

---

### Post by sanderj on 2013-08-31
No problems here:

```
sander@HPtje:~$ cat test.f90 
PROGRAM TEST
WRITE(*,*)'HELLO'
END

sander@HPtje:~$ gfortran test.f90 -o test
sander@HPtje:~$ ll test
-rwxr-xr-x 1 sander sander 7648 aug 31 14:14 test*
sander@HPtje:~$ ./test 
 HELLO
sander@HPtje:~$
```

---

### Post by Fukun_XU on 2013-08-31
Hi Sanderj.
Thanks for your reply. Now it's OK. I encontered it because I run these command on an NTFS format disk. When I move the document to ```
/home
```. It's working ~~

---

