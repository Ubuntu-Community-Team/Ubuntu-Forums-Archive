---
title: "prblem installing app"
date: 2022-05-07
forum: General Help
---

### Post by cmcanulty on 2022-05-07
One of my most used applications has an error after upgrading to Xubuntu 22.04. Here are the details. On one computer I did a clean install and now my chess program won't install at all. On another computer I upgraded to 22.04 and it runs fine. Here is the error output.

```
cmcanulty@DellInspiron-660s:~/scidb-code-r1531-trunk$ ./configure
configure: Makefile configuration program for Scidb
    Tcl/Tk version: 8.6
    Your operating system is: Linux 5.15.0-27-generic
                 Distributor: Ubuntu
                    Revision: 22.04
                     Version: 22.04 LTS (Jammy Jellyfish)
    Checking if your system has gcc installed: yes,
    but existing gcc version 11.2 is too old.

    The required version is 3.4 and higher.
cmcanulty@DellInspiron-660s:~/scidb-code-r1531-trunk$ 
```

now that is weird because my gcc is 11 and they require 3.4 and higher. The other detail is on the upgraded computer here is a screenshot of my gcc apps

[ATTACH=CONFIG]290411[/ATTACH]

Now the weirder part. Here is a screenshot of the installed gcc apps on the computer where it won't install and they are exactly the same!

[ATTACH=CONFIG]290412[/ATTACH]

---

### Post by Impavidus on 2022-05-07
Are you trying exactly the same version of the configure script on both systems?

If the configure script needs gcc 3.4 and claims gcc 11.2 is too old, there's a bug in the script. It thinks 11 is less than 3, which is only the case when comparing strings, not numbers. But it makes me think. Maybe your upgraded system also has an older version of gcc installed, like gcc 9. The script might recognise that as later than 3.4. Multiple versions of gcc can be installed at the same time, as they are in separate packages.

It might be good to have a look at the configure script.

---

### Post by cmcanulty on 2022-05-08
it won't let me put it here even with code tags and it won't let me attach it I could email it to you if you tell me your email thanks

---

### Post by cmcanulty on 2022-05-08
I have gotten ./configure to run by 
using this web site to install and older gcc. The oldest one that worked for scidb ./configure was gcc 9
[https://www.linuxcapable.com/how-to-install-gcc-compiler-build-essential-on-ubuntu-22-04-lts/](https://www.linuxcapable.com/how-to-install-gcc-compiler-build-essential-on-ubuntu-22-04-lts/)
so I did the  code:

```

sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 60 --slave /usr/bin/g++ g++ /usr/bin/g++-9 --slave /usr/bin/gcov gcov /usr/bin/gcov-9

```  then I fixed the next error with

then I did tcl fix as follows
sudo apt install tcl-dev

 then I ran make and now I get an error I have no idea how to fix: 
sys_info.cpp:30:11: fatal error: sys/sysctl.h: No such file or directory

---

### Post by Impavidus on 2022-05-09
> **cmcanulty said:**
> it won't let me put it here even with code tags and it won't let me attach it I could email it to you if you tell me your email thanksIt's supposed to be plain text. Is the script so large? Maybe you can [pastebin](https://paste.ubuntu.com/) it, but if it's so large, I won't analyse all of it. I've got other things to do as well.

> **cmcanulty said:**
> I have gotten ./configure to run by 
using this web site to install and older gcc. The oldest one that worked for scidb ./configure was gcc 9So the configure script believes that 9 is greater than 3.4, but 11.2 is less than 3.4. Interesting arithmetic...
> then I ran make and now I get an error I have no idea how to fix: 
sys_info.cpp:30:11: fatal error: sys/sysctl.h: No such file or directory
sys/sysctl.h used to be in libc6-dev, but it no longer is. Searching on [https://packages.ubuntu.com](https://packages.ubuntu.com) reveals several packages containing a sysctl.h on 22.04, but I don't know which one you need.

Looks like the configure script of this package wasn't really prepared for 22.04 and only worked on the upgraded system because it had retained some cruft from earlier releases. Maybe you can get it working, but this software needs some maintenance.

---

### Post by cmcanulty on 2022-05-09
thanks so much I will keep trying

---

### Post by cmcanulty on 2022-05-09
OK maybe this helps . I did a locate search  for sysctl.h on both computers so I see the differences but don't have a clue how to fix it. I did search for the pkg sysctl.h and it doesn't appear to be available for 22.04.

On the system that works I get this:  
```

cmcanulty@HPPavilion23:~$ locate sysctl.h
/usr/include/linux/sysctl.h
/usr/share/python3-pycparser/fake_libc_include/sys/sysctl.h
/usr/src/linux-headers-5.15.0-27/include/linux/sysctl.h
/usr/src/linux-headers-5.15.0-27/include/linux/sched/sysctl.h
/usr/src/linux-headers-5.15.0-27/include/soc/canaan/k210-sysctl.h
/usr/src/linux-headers-5.15.0-27/include/uapi/linux/sysctl.h
cmcanulty@HPPavilion23:~$ 
```

on the system that doesn't work I get this:

```
cmcanulty@DellInspiron-660s:~$ locate sysctl.h
/usr/include/linux/sysctl.h
/usr/share/python3-pycparser/fake_libc_include/sys/sysctl.h
/usr/src/linux-headers-5.15.0-25/include/linux/sysctl.h
/usr/src/linux-headers-5.15.0-25/include/linux/sched/sysctl.h
/usr/src/linux-headers-5.15.0-25/include/soc/canaan/k210-sysctl.h
/usr/src/linux-headers-5.15.0-25/include/uapi/linux/sysctl.h
/usr/src/linux-headers-5.15.0-27/include/linux/sysctl.h
/usr/src/linux-headers-5.15.0-27/include/linux/sched/sysctl.h
/usr/src/linux-headers-5.15.0-27/include/soc/canaan/k210-sysctl.h
/usr/src/linux-headers-5.15.0-27/include/uapi/linux/sysctl.h
cmcanulty@DellInspiron-660s:~$

```

---

