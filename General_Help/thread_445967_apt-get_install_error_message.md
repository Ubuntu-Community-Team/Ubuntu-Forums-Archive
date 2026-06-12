---
title: "apt-get install error message"
date: 2007-05-16
forum: General Help
---

### Post by zach12 on 2007-05-16
hello
 i just tryed to install tuxracer useing apt-get install and i got a error message here it is > zach@zach-laptop:~$ sudo apt-get install tuxracer
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
zach@zach-laptop:~$ dpkg
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
zach@zach-laptop:~$


 i am new at linux 
thank you

---

### Post by taurus on 2007-05-16
```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
sudo apt-get install tuxracer
```

---

### Post by zach12 on 2007-05-19
hello i tryed that but it did not work

---

### Post by taurus on 2007-05-19
Got the same error as before?

---

### Post by zach12 on 2007-06-06
yes

---

### Post by taurus on 2007-06-06
Can you post the output of these two commands from a terminal?

```
sudo dpkg --configure -a
sudo apt-get update
```

---

