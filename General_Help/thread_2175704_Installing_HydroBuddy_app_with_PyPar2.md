---
title: "Installing HydroBuddy app with PyPar2"
date: 2013-09-20
forum: General Help
---

### Post by ozark_hillbilly on 2013-09-20
I am attempting to install a hydroponics nutrient calculator app called HydroBuddy.  [[http://scienceinhydroponics.com/]](http://scienceinhydroponics.com/])

After downloading the executable Linux install file [HydroBuddy-1.50-Linux-x86-Install] I attempted installation whereupon the system said it did not currently have an application available to perform the install and I chose the "search online" function to locate an app. It came back with PyPar2 which I subsequently downloaded and used to open the HydroBuddy Linux install file.

The install seems to have worked OK with no errors.

When I try to open the newly created par2 files I get an error message: No applications available to open HydroBuddy-1.50-Linux-x86-Install.par2.
When I select "Find applications online" another message informs me that:

Nautilus requires to install software to open files of following type:

Parchive archive:

Parchive archive is not supported.



Screenshots attached show error messages and install text.

Any help certainly appreciated,

Ed

---

### Post by ozark_hillbilly on 2013-09-23
bump

---

### Post by The Cog on 2013-09-28
HydroBuddy-1.50-Linux-x86-Install would appear to be a 32-bit executable. Specifically:
```
steve@StevePC:~/Desktop$ file HydroBuddy-1.50-Linux-x86-Install 
HydroBuddy-1.50-Linux-x86-Install: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), not stripped
```

If you trust the code, you should probably just mark it executable, and execute it with two commands like this:
```
chmod +x HydroBuddy-1.50-Linux-x86-Install
./HydroBuddy-1.50-Linux-x86-Install
```
I think it will then ask what directory to install it into.

---

### Post by ozark_hillbilly on 2013-09-29
To: The Cog

From: Ed

THANK YOU!!! 
Program was installed without any gotchas using your command sequence.

I appreciate the help.

---

