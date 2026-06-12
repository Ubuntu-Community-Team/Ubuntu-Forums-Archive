---
title: "Aim!!!"
date: 2007-02-04
forum: General Help
---

### Post by DougieFresh4U on 2007-02-04
trying to open AOL's AIM I get this::dougie@DougiesToyBox:~$ aim
aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
dougie@DougiesToyBox:~$ 

now I know these files are there because I just had updates for them, so what is the problem please?:mad: :mad: :mad: :mad: :mad:

---

### Post by phossal on 2007-02-04
Just out of curiosity, why AIM instead of GAIM?

---

### Post by taurus on 2007-02-04
Where did you install that library and have you logged out and back in again?  Perhaps try to reboot if you wish.

---

### Post by DougieFresh4U on 2007-02-04
> **phossal said:**
> Just out of curiosity, why AIM instead of GAIM?

A lot of friends and family have AIM and gaim smileys etc. don't show up on there AIM. If I message them using gaim, as i mentioned thing don't all show up on Aim as wll as sounds. Also personal preference.:lolflag:

---

### Post by DougieFresh4U on 2007-02-04
> **taurus said:**
> Where did you install that library and have you logged out and back in again?  Perhaps try to reboot if you wish.

I'm freeeeeeeezing buddy):P  I don't know where those files are but I had updates today and they all went in some where's. how do I find them?

---

### Post by phossal on 2007-02-04
The file is typically here: usr/lib/*
You'll probably need to include a symbolic link somewhere in the AIM folders so it can use it.

You can search for it like this:
```
sudo slocate -u
slocate libstdc*
```

---

### Post by DougieFresh4U on 2007-02-04
> **phossal said:**
> The file is typically here: usr/lib/libstdc++-3-libc6.2-2-2.10.0.so 
You'll probably need to include a symbolic link somewhere in the AIM folders so it can use it.

You can search for it like this:
```
sudo slocate -u
slocate libstdc++-3-libc6.2-2-2.10.0.so
```

thank you for your reply. i tried that code and get this::dougie@DougiesToyBox:~$ sudo slocate -u
dougie@DougiesToyBox:~$ slocate libstdc++-3-libc6.2-2-2.10.0.so
dougie@DougiesToyBox:~$

---

### Post by phossal on 2007-02-04
```
sudo apt-get install libstdc++2.10-dbg
```

---

### Post by DougieFresh4U on 2007-02-04
> **phossal said:**
> ```
sudo apt-get install libstdc++2.10-dbg
```

I'm trying the best I can::dougie@DougiesToyBox:~$ sudo apt-get install libstdc++2.10-dbg
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cpp-2.95 g++-2.95 gcc-2.95 libstdc++2.10-dev libstdc++2.10-glibc2.2
Suggested packages:
  gcc-2.95-doc task-devel-common stl-manual
The following NEW packages will be installed:
  cpp-2.95 g++-2.95 gcc-2.95 libstdc++2.10-dbg libstdc++2.10-dev
  libstdc++2.10-glibc2.2
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 3012kB of archives.
After unpacking 9892kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe cpp-2.95 1:2.95.4-24 [116kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe gcc-2.95 1:2.95.4-24 [949kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe libstdc++2.10-glibc2.2 1:2.95.4-24 [329kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe libstdc++2.10-dev 1:2.95.4-24 [297kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe g++-2.95 1:2.95.4-24 [1029kB]  
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe libstdc++2.10-dbg 1:2.95.4-24 [292kB]
Fetched 3012kB in 36s (83.3kB/s)                                               
Selecting previously deselected package cpp-2.95.
(Reading database ... 149536 files and directories currently installed.)
Unpacking cpp-2.95 (from .../cpp-2.95_1%3a2.95.4-24_i386.deb) ...
Selecting previously deselected package gcc-2.95.
Unpacking gcc-2.95 (from .../gcc-2.95_1%3a2.95.4-24_i386.deb) ...
Selecting previously deselected package libstdc++2.10-glibc2.2.
Unpacking libstdc++2.10-glibc2.2 (from .../libstdc++2.10-glibc2.2_1%3a2.95.4-24_i386.deb) ...
Selecting previously deselected package libstdc++2.10-dev.
Unpacking libstdc++2.10-dev (from .../libstdc++2.10-dev_1%3a2.95.4-24_i386.deb) ...
Selecting previously deselected package g++-2.95.
Unpacking g++-2.95 (from .../g++-2.95_1%3a2.95.4-24_i386.deb) ...
Selecting previously deselected package libstdc++2.10-dbg.
Unpacking libstdc++2.10-dbg (from .../libstdc++2.10-dbg_1%3a2.95.4-24_i386.deb) ...
Setting up cpp-2.95 (2.95.4-24) ...

Setting up gcc-2.95 (2.95.4-24) ...

Setting up libstdc++2.10-glibc2.2 (2.95.4-24) ...

Setting up libstdc++2.10-dev (2.95.4-24) ...

Setting up libstdc++2.10-dbg (2.95.4-24) ...

Setting up g++-2.95 (2.95.4-24) .                                                                            dougie@DougiesToyBox:~$ aim
aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
dougie@DougiesToyBox:~$

---

### Post by phossal on 2007-02-04
***I'm an idiot.*** Hang on just a second.

---

### Post by battleroyalex on 2007-02-04
can you actually wine aim and get direct connect working with access to files on the linux drive? That would be great considering linux has no direct connect support with any of their third party aims

---

### Post by DougieFresh4U on 2007-02-04
> **phossal said:**
> ***I'm an idiot.*** Hang on just a second.

dougie@DougiesToyBox:~$ sudo slocate -u
dougie@DougiesToyBox:~$ slocate libstdc++-3-libc6.2-2-2.10.0.so
/usr/lib/libstdc++-3-libc6.2-2-2.10.0.so
/usr/lib/debug/libstdc++-3-libc6.2-2-2.10.0.so
dougie@DougiesToyBox:~$       Thank you, now forgive my stupidity but how do I make symbolic link?

---

### Post by phossal on 2007-02-04
It's typically *here*: /usr/lib/libstdc++-libc6.1-1.so.2  (I had the wrong .so previously, sorry) You can cd into /usr/lib and then use *ls libstdc++-libc6.1-1.so.2* to confirm it's there. I think it's actually a part of build-essential?
```
sudo apt-get install build-essential
```
That would sort of make sense. Some updates *wreck* the build-essential install.

---

### Post by igknighted on 2007-02-04
> **battleroyalex said:**
> can you actually wine aim and get direct connect working with access to files on the linux drive? That would be great considering linux has no direct connect support with any of their third party aims

This would be nice.

To the OP, have you actually used AIM for linux?  It is an ancient program that hasn't been updated in years.  All these things that you want from it may or may not work, especially with the new AIM clients everyone else is using.  Also, the libraries it wants might not be available anymore.  I think I saw somewhere that you need to create a symlink to whatever newer version the library is, because it doesn't accept the newer one by name (or something along these lines at least... would be nice if they released the source for this so it could (a) be fixed or (b) let developers improve support in Gaim/kopete).

---

### Post by DougieFresh4U on 2007-02-04
> **phossal said:**
> It's typically *here*: /usr/lib/libstdc++-libc6.1-1.so.2  (I had the wrong .so previously, sorry) You can cd into /usr/lib and then use *ls libstdc++-libc6.1-1.so.2* to confirm it's there. I think it's actually a part of build-essential?
```
sudo apt-get install build-essential
```
That would sort of make sense. Some updates *wreck* the build-essential install.
sorry I am still a little bit lost. I am not sure how to cd or whatever, although I should learn how to do these things myself!! 8i am grateful for your help though):P

---

### Post by phossal on 2007-02-04
```
bash 3.1:**pwd** **[COLOR="Blue"]#1[/COLOR]**
**/home/phossal** **[COLOR="Blue"]#2[/COLOR]**
bash 3.1:**ls** **[COLOR="Blue"]#3[/COLOR]**
**backgrounds  Desktop  mp3  workspace** **[COLOR="Blue"]#4[/COLOR]**
bash 3.1:
```

First of all you use the terminal window to issue commands. And the "program" that the terminal runs is bash. If you're serious about Ubuntu, or linux in general, you want a decent book on bash. If you start to program, either in Python or Perl, you'll need to know a bit about bash to really get rolling, and they sort of go together.

Let's get started:
**[COLOR="Blue"]#1[/COLOR]**: pwd is a command to "Print Working Directory". In other words, it prints the directory "you're in". Using the command line is sort of like browsing in Windows. You move from directory to directory using various commands. pwd prints the path (or directory) you're currently "in". As you can see in line [COLOR="Blue"]**#2**[/COLOR], when you open a terminal window, you start in /home/<USERNAME>.

**[COLOR="Blue"]#3[/COLOR]**: ls  (ELL-ESS) is a command to list everything in your current directory. You can see the files that are in your /home/user path displayed in line **[COLOR="Blue"]#4[/COLOR]**.

To change directories you use the cd command. There are lots of options it takes. There are lots of shortcuts and ways to get around. Plus, if you know bash, you can customize it even further. Let's not get ahead of ourselves though. You need to get to find the missing file, and that's in *this* directory: /usr/lib

Here is how you change directories:
```
cd /usr/lib
```

---

### Post by DougieFresh4U on 2007-02-04
dougie@DougiesToyBox:~$ cd /usr/lib
dougie@DougiesToyBox:/usr/lib$ ls libstdc++-libc6.1-1.so.2 
ls: libstdc++-libc6.1-1.so.2: No such file or directory
dougie@DougiesToyBox:/usr/lib$

---

### Post by phossal on 2007-02-04
You probably need this, mate:
```
sudo apt-get install build-essential
```

I think the .so file that AIM is trying to find is part of the compiler collection.

---

### Post by DougieFresh4U on 2007-02-04
> **phossal said:**
> You probably need this, mate:
```
sudo apt-get install build-essential
```

I think the .so file that AIM is trying to find is part of the compiler collection.

im totally lost now::dougie@DougiesToyBox:/usr/lib$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dougie@DougiesToyBox:/usr/lib$ ls libstdc++-libc6.1-1.so.2
ls: libstdc++-libc6.1-1.so.2: No such file or directory
dougie@DougiesToyBox:/usr/lib$

---

### Post by phossal on 2007-02-04
I thought the .so file was part of the build-essential package. Give me a minute and I'll find it for you.

---

### Post by DougieFresh4U on 2007-02-04
> **phossal said:**
> I thought the .so file was part of the build-essential package. Give me a minute and I'll find it for you.

your doing great, I'm the dummy:lolflag: :lolflag:

---

### Post by phossal on 2007-02-04
Let's try the shotgun approach. lol 
```
sudo apt-get install libstdc++6-4.1-dbg libstdc++6 libstdc++2.10-dbg
```

---

### Post by DougieFresh4U on 2007-02-04
> **phossal said:**
> Let's try the shotgun approach. lol 
```
sudo apt-get install libstdc++6-4.1-dbg libstdc++6 libstdc++2.10-dbg
```

ok now what sir:lolflag:   dougie@DougiesToyBox:~$ sudo apt-get install libstdc++6-4.1-dbg libstdc++6 libstdc++2.10-dbg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libstdc++6-4.1-dbg is already the newest version.
libstdc++6 is already the newest version.
libstdc++2.10-dbg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dougie@DougiesToyBox:~$

---

### Post by phossal on 2007-02-04
```
sudo ln -s /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so libstdc++-libc6.1-1.so.2
```

---

### Post by DougieFresh4U on 2007-02-04
> **phossal said:**
> ```
sudo ln -s /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so libstdc++-libc6.1-1.so.2
```

I do something wrong/   sudo ln -s /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so libstdc++-libc6.1-1.so.2

---

### Post by phossal on 2007-02-04
> **DougieFresh4U said:**
> I do something wrong/   sudo ln -s /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so libstdc++-libc6.1-1.so.2

What?

---

### Post by DougieFresh4U on 2007-02-04
> **phossal said:**
> What?

forgot this::dougie@DougiesToyBox:~$ sudo ln -s /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so libstdc++-libc6.1-1.so.2
dougie@DougiesToyBox:~$ aim
aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
dougie@DougiesToyBox:~$

---

### Post by phossal on 2007-02-04
Try this one:```

sudo ln -s /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so /usr/lib/libstdc++-libc6.1-1.so.2
```

---

### Post by DougieFresh4U on 2007-02-04
> **phossal said:**
> Try this one:```

sudo ln -s /usr/lib/libstdc++-3-libc6.2-2-2.10.0.so /usr/lib/libstdc++-libc6.1-1.so.2
```

Perfect, u r the man!!!!):P ):P ):P ):P ):P ):P . I have been trying for months to get this and it is working now. one last thing, how can i get launcher as when I closed terminal it also shut AIM down? Thank you so much:lolflag:

---

### Post by phossal on 2007-02-04
I don't know how it launches. I cannot help you in the menu because I do not know the mechanism. Is it a script? Is it an executable? How does it launch?

In the meantime, you can do this:
```
aim &
```
This will let you close the terminal.

---

