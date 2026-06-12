---
title: "How to install programs"
date: 2012-12-24
forum: General Help
---

### Post by alkal0id on 2012-12-24
I've been using linux for years now but I never learned how to install programs which is ridiculous since its just an essential thing to be able to do. I always try running apt-get install program first and if its not in there, I'll look for a .deb file on the site, if theres no deb installer, I'll look for the next best thing, one of those installers that I just have to point to with the command line. I hate finding out that theres only a .tar.gz file available because half the time I don't know what to do with it. 

So I'll give an example, I just downloaded proguard (I later found out its in the repositories so I installed it but I want to learn how to install things for myself once and for all). So I extracted the .tar.gz file and heres the contents of the directory:
```
box@box:~/Desktop/test/proguard4.8$ ls
bin  build  docs  examples  lib  README  src

```Unfortunately I don't know what to do with all that. Am I supposed to transfer it to a specific folder or something? I know that /usr/bin contains a load of apps but theres no directories in there, I know thats now where installed applications go. In Windows when you install a program, it goes into C:/Program Files or sometimes just C:/. I don't know what the situation is with linux. I wanna test this proguard program out but I need to point to the file in its install directory and since I don't know where Ubuntu put that directory when it installed it, I have to just search "proguard" with nautilus and that takes ages.

---

### Post by fdrake on 2012-12-24
README file means "README" we don't call like that for not reason, we could have called it do_not_read.txt.

when installing a program from source there are to 2 things to look for :
1-readme.txt (instruction/hel txt file)

2-source code file/folder  (src in your case)

post the output of list of files into src folder and attach here the readme.txt of put a link of the archive.

none said that building from source was easy but it's the best way to get a program running an larger variety of hardware

edit:

read this :
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

---

### Post by agillator on 2012-12-24
fdrake is correct. The first thing to do is to read the README file and/or the INSTALL file if there is one. In one of those should be instructions. What happens depends upon what you are dealing with. Is it a set of source files to be compiled? Is it already compiled and simply needs to be put somewhere and make executable? Does it need to be configured before being run? These are all things you need to find out. The answers should be provided in the two files. It is a matter of RTFI (Read Those Fine Instructions).

---

### Post by rnerwein on 2012-12-24
> **alkal0id said:**
> I've been using linux for years now but I never learned how to install programs which is ridiculous since its just an essential thing to be able to do. I always try running apt-get install program first and if its not in there, I'll look for a .deb file on the site, if theres no deb installer, I'll look for the next best thing, one of those installers that I just have to point to with the command line. I hate finding out that theres only a .tar.gz file available because half the time I don't know what to do with it. 

So I'll give an example, I just downloaded proguard (I later found out its in the repositories so I installed it but I want to learn how to install things for myself once and for all). So I extracted the .tar.gz file and heres the contents of the directory:
```
box@box:~/Desktop/test/proguard4.8$ ls
bin  build  docs  examples  lib  README  src

```Unfortunately I don't know what to do with all that. Am I supposed to transfer it to a specific folder or something? I know that /usr/bin contains a load of apps but theres no directories in there, I know thats now where installed applications go. In Windows when you install a program, it goes into C:/Program Files or sometimes just C:/. I don't know what the situation is with linux. I wanna test this proguard program out but I need to point to the file in its install directory and since I don't know where Ubuntu put that directory when it installed it, I have to just search "proguard" with nautilus and that takes ages.
hi
how alligator said --> mostely it is enough to read the file INSTALL.
and every time the same procedure (mostely).
./configure
make
sudo make install

the install binaries should be found in /usr/local/bin .../include ..
apend your PATH to PATH=$PATH:/usr/local/bin if this directory isn't in your PATH
cears

---

### Post by Impavidus on 2012-12-24
> **rnerwein said:**
> hi
how alligator said --> mostely it is enough to read the file INSTALL.
and every time the same procedure (mostely).
./configure
make
sudo make install
If it is a well-formed archive. If you're really unlucky it may not be. Furthermore, be prepared to install extra libraries and headers. If you get complaints in your terminal you may need to install some libfoobar-dev packages and the like.
> **rnerwein said:**
> 
the install binaries should be found in /usr/local/bin .../include ..
apend your PATH to PATH=$PATH:/usr/local/bin if this directory isn't in your PATH
cears
 /usr/local/bin is in your PATH by default.

---

