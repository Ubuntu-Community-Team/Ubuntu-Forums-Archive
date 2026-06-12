---
title: "Gcc Compiler"
date: 2008-06-21
forum: General Help
---

### Post by bimmax on 2008-06-21
Hae. Somebody please help me out. Am trying to compile c/c++ filesbut am getting an error,"compiler cannot create executables" why this error.

Thanks
Max

---

### Post by geo909 on 2008-06-21
Did you do 
```
gcc myfile.c
```
and it doesn't work?

Can you post exactly what you do?

Also, see if you have the package "build-essentials" installed

---

### Post by mali2297 on 2008-06-21
Have you installed the **build-essential** meta package?

---

### Post by natgiot on 2008-06-23
Hallo, I have the same problem, I tried the 
sudo apt-get install build-essential
coomand in my X11 ( i am on MACOSX) and after requiring the password , it says 'apt-get: command not found' !
This id part of a more general problem that I need to share in case anybody can help: 
I am trying to compile diffutils and it seems I need to have a make which i do not know how to choose-downoad from the various mirrors with a list of different .tar.gz versions.. So i thought from the forums that thi sudo command would be an alternative, no? (I am a begginer obviously!)
 The other problem is, I had to specify the path to my gcc for the compiler of diffutils, but I am not sure if I gave him the right path. With a 
find . -name "*gcc" I found a /usr/share/zsh/4.3.4/functions/_gcc with DENIED permission. is this my gcc? i had previously installed another compiler in /usr/local/i386-mingw32-3.4.5/bin/ i386-mingw32-gcc, but then I realized that I must have already one so I abandonned this option. 
Please if anyone can explain me some basic things here (even yhe directories in which I have to execute the commands) it would be great help!
Thanks,
Nat

---

### Post by mali2297 on 2008-06-23
> **natgiot said:**
> Hallo, I have the same problem, I tried the 
sudo apt-get install build-essential
coomand in my X11 ( i am on MACOSX) and after requiring the password , it says 'apt-get: command not found' !

**apt-get** is a package manager for Debian/Ubuntu Linux. It won't work on Mac OSX.

> 
This id part of a more general problem that I need to share in case anybody can help: 
I am trying to compile diffutils and it seems I need to have a make which i do not know how to choose-downoad from the various mirrors with a list of different .tar.gz versions.. So i thought from the forums that thi sudo command would be an alternative, no? (I am a begginer obviously!)

**sudo** lets you execute commands as an administrator, useful if you want to install something system-wide (e.g., sudo make install).

> 
 The other problem is, I had to specify the path to my gcc for the compiler of diffutils, but I am not sure if I gave him the right path. With a 
find . -name "*gcc" I found a /usr/share/zsh/4.3.4/functions/_gcc with DENIED permission. is this my gcc? i had previously installed another compiler in /usr/local/i386-mingw32-3.4.5/bin/ i386-mingw32-gcc, but then I realized that I must have already one so I abandonned this option. 

Try entering
```

which gcc

```
in the terminal.

Note that this is a Linux forum. If you have a question about Mac OSX, you can try posting it in the [Other OS talk]("http://ubuntuforums.org/forumdisplay.php?f=165") section, but you should probably look for a forum for Mac users.

---

### Post by natgiot on 2008-06-23
Thanks Martin
I ve already tried which gcc, nothing comes out. I will try a MACOS forum.
Natassa

---

