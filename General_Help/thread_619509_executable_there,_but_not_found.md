---
title: "executable there, but not found"
date: 2007-11-21
forum: General Help
---

### Post by Jasper84 on 2007-11-21
I have downloaded Urbanterror installer and it seems to have installed as it should. However, now i am trying to run it, but it can not.
```
jasper@jasper-desktop:~/Games/UrbanTerror4$ ./ioUrbanTerror.i386
bash: ./ioUrbanTerror.i386: No such file or directory
jasper@jasper-desktop:~/Games/UrbanTerror4$ ls -l ioUrbanTerror.i386
-rwxr-xr-x 1 jasper jasper 1614532 2007-04-02 04:14 ioUrbanTerror.i386
jasper@jasper-desktop:~/Games/UrbanTerror4$[/quote]
It looks like it is there yet it is not? :confused: I tried copying it but problem persists. Same for formido and alien arena
[code]jasper@jasper-desktop:~/Games/formido-1.0$ ls -l formido
-rwxr-xr-x 1 jasper jasper 97172 2007-05-03 02:03 formido
jasper@jasper-desktop:~/Games/formido-1.0$ ./formido
bash: ./formido: No such file or directory
jasper@jasper-desktop:~/Games/formido-1.0$ ls -l formido
-rwxr-xr-x 1 jasper jasper 97172 2007-05-03 02:03 formido
jasper@jasper-desktop:~/Games/formido-1.0$ ./formido
bash: ./formido: No such file or directory
jasper@jasper-desktop:~/Games/formido-1.0$ cd ../alien*
jasper@jasper-desktop:~/Games/alienarena2007$ ls -l ./crx
-rwxr-xr-x 1 jasper jasper 641056 2007-10-11 18:29 ./crx
jasper@jasper-desktop:~/Games/alienarena2007$ ./crx
bash: ./crx: No such file or directory

```
Similar executables of warsow do work, and have the same permission.
```

-rwxr-xr-x 1 jasper jasper   97172 2007-05-03 02:03 ../formido-1.0/formido
-rwxr-xr-x 1 jasper jasper 1614532 2007-04-02 04:14 ../UrbanTerror4/ioUrbanTerror.i386
-rwxr-xr-x 1 jasper jasper    1077 2007-08-26 14:36 warsow
-rwxr-xr-x 1 jasper jasper 1528772 2007-08-26 14:36 warsow.i386
-rwxr-xr-x 1 jasper jasper 1722325 2007-08-26 14:36 warsow.x86_64
```
I tried to search, but i cant find the answer to this. What could be the problem?

---

### Post by mali2297 on 2007-11-21
Do you have the 32-bit version of ubuntu?

If you're not sure, type 
```

uname -m

```
in the terminal. (i686=32-bit whereas x86_64=64-bit.)

---

### Post by Jasper84 on 2007-11-21
I have 64 bit. I thought that it wouldnt be a problem. (well i didnt think about it) How do i get around it? do i the 64 bit executables? If so, i guess the error messages could improve :).

---

### Post by mali2297 on 2007-11-22
When you have a binary file like warsow.x86_64, then you should try that.

Otherwise, if there are no binaries compiled for 64-bit, you can compile it yourself. This should be possible for all open-source software.  See for example
[http://www.psychocats.net/ubuntu/installingsoftware#source](http://www.psychocats.net/ubuntu/installingsoftware#source)

If you need a closed-source application that is only available in 32-bit, then it might be able to run in a 64-bit environment if you get some extra libraries. I don't know much about it, you should check the [x86 64-bit forum]("http://ubuntuforums.org/forumdisplay.php?f=134").

---

### Post by Jasper84 on 2007-11-22
Thanks a lot! It could have been ages before i thought of that. ./warsow actually did work. (And indeed it does have 64bit.) 
I have found the 64-bit binary file for Urbanterror [in the forum](http://forums.urbanterror.net/index.php/topic,8769.0.html). And it works! :) (Be sure to get both dedicated and client files.) Now to find the others, if i have them i will post them here.(Or if someone else happens to find them, it would be nice to post aswel :))

---

