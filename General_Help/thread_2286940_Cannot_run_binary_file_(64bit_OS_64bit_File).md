---
title: "Cannot run binary file (64bit OS 64bit File)"
date: 2015-07-15
forum: General Help
---

### Post by 1keith1 on 2015-07-15
I've got a file that I cannot get to run, 

Check out my console commands below for more info, i'm on a 64bit os running a 64bit binary and I can't run it with either sudo ./ , sudo bash ./ . or sudo sh ./

```

root@keith-VirtualBox:~/Downloads# ls -lap
total 924676
drwxr-xr-x  2 keith keith      4096 Jul 15 15:43 ./
drwxr-xr-x 18 keith keith      4096 Jul 15 10:47 ../
**-rwxrwxr-x  1 keith keith  49602885 Jul 14 10:00 install.linux64**
-rw-rw-r--  1 keith keith 307587286 Jul 14 10:20 questasim-base.mis
-rw-rw-r--  1 keith keith  56411375 Jul 14 10:20 questasim-docs.mis
-rw-rw-r--  1 keith keith 127761376 Jul 14 10:20 questasim-gcc-linux_x86_64.mis
-rw-rw-r--  1 keith keith 305321390 Jul 14 10:06 questasim-linux_x86_64.mis
-rw-rw-r--  1 keith keith 100157438 Jul 14 10:20 regassistuvm_4.6_ixl.mis
root@keith-VirtualBox:~/Downloads# uname -m
**x86_64**
root@keith-VirtualBox:~/Downloads# file install.linux64 
**install.linux64: ELF 64-bit LSB  executable**, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, not stripped
root@keith-VirtualBox:~/Downloads# **sudo sh ./install.linux64**
./install.linux64: 2: ./install.linux64: Syntax error: ")" unexpected
root@keith-VirtualBox:~/Downloads# **sudo bash ./install.linux64 **
./install.linux64: ./install.linux64: cannot execute binary file
root@keith-VirtualBox:~/Downloads# **sudo ./install.linux64**
Unable to access TEMP folder at path /usr/tmproot@keith-VirtualBox:~/Downloads# 

```

---

### Post by monkeybrain20122 on 2015-07-15
Try either (after cd into the directory where the script is)
```
sudo install.linux64
```

or if install in $HOME, just

```
./install.linux64
```

Why are you logging in as root??!! Just run sudo as your user, it is insecure to login as root.
The  point of sudo is to grant root privilege to users in sudoer file on a per command basis so they don't have to be root.

---

### Post by 1keith1 on 2015-07-15
I tried your first cmd:
```

root@keith-VirtualBox:~/Downloads# sudo install.linux64
sudo: install.linux64: command not found



```

---

### Post by nerdtron on 2015-07-15
From your command here:
```
 root@keith-VirtualBox:~/Downloads# **sudo ./install.linux64**
Unable to access TEMP folder at path /usr/tmproot@keith-VirtualBox:~/Downloads#
```
The installer ran. This one is correct. But it can't find the directory needed to continue. Try to create that directory and then run the installer again.

---

### Post by 1keith1 on 2015-07-16
That solved the problem, I had to create /usr/tmp and /usr/tmp/TEMP, which required root privileges.

Weird that the installer could not create these directories even though it had root.

---

