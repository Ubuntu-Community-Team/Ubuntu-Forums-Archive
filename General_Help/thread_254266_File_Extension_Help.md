---
title: "File Extension Help"
date: 2006-09-09
forum: General Help
---

### Post by groog on 2006-09-09
I just converted from windows and it was going well for a while until I hit a little snag. It seems ubuntu can't run .exe files. I think I've been told there's somthing online I can download, but unfortunatly the only way I can get online is with a wireless connection, to download it I have to run "setup**.exe**". Sence none of the computers in my house can write cd's I can't get online and get this thing.

1. Is there a way I can get around this?

2. What is the name of the program that will allow me to change .exe to... What ever ubuntu runs.

---

### Post by scxtt on 2006-09-09
you cannot run *.exe files natively in ubuntu - so give up on that idea ... wine [[http://www.winehq.org/]](http://www.winehq.org/]) would possibly work for you, i'd research that first ...

---

### Post by Najand on 2006-09-09
Well, an easy way is to install "wine" using the command:
```
$ sudo apt-get install wine
```
And then you would be able to use MS-WINDOWS EXE files (for  example YOURFILE.exe) in linux by using:
```
$ wine YOURFILE.exe
```
However, It does ***NOT*** work all the time, because Linux is completely a different system with different structure and it is not very recommended.

---

### Post by CatKiller on 2006-09-09
As you've already found out, Wine is what you'd need to use if you wanted to run a .exe file in a pretend Windows environment.

However, you almost certainly **don't** need to run any .exe file to get wireless networking going. Networking under Linux seems really good to me, although I've never used wireless. Search these forums for how to configure wireless under Linux (it won't be with an .exe file), or post details of your wireless setup and someone who knows about wireless may be able to point you in the right direction.

Welcome to the forum!

---

### Post by scxtt on 2006-09-10
FWIW - i've had success w/ 6.06 and and ra* based wireless card ... all i had to do w/ make sure the router used WEP encryption ...

---

