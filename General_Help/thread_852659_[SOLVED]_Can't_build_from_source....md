---
title: "[SOLVED] Can't build from source..."
date: 2008-07-07
forum: General Help
---

### Post by L337_K3y5 on 2008-07-07
I'm trying to build pygame from source (I know its in the repo, just making a statement) and I do everything like normal...I untar it using tar zxf browse into the directory on the desktop, then when I try using ./configure it gives me this error message*:  
I think something has gone wrong, cause I used to be able to do this.  Also, just for a question, my update manager where it says at the top how long ago it has been updated is wrong, how do I "refresh" the update manager?
Also, sorry for the bad picture, don't know how the top of the window blurred in like that.  I uploaded another, but its still the same

*Attached

---

### Post by aroch1 on 2008-07-07
I don't see an attachment...

Oops, right after I posted that it loaded...sorry.

---

### Post by aroch1 on 2008-07-07
Is there a configure script in the pygame-1.8.0release directory?  Does it have the correct permissions?  Take a look at/post the output of

```
ls -l
```

in that directory.

---

### Post by tamoneya on 2008-07-07
first of all make sure the file is there by running ```
ls -l
``` Typically however the problem when you get this error is that the file doesnt have executable permissions```
sudo chmod +x configure
```

---

### Post by L337_K3y5 on 2008-07-07
This is what I get from doing the code:
```
andrew@andrew-laptop:~$ cd /home/andrew/Desktop/pygame-1.8.0release
andrew@andrew-laptop:~/Desktop/pygame-1.8.0release$ ls -l
total 216
-rw-r--r-- 1 andrew admin   934 2006-07-20 19:06 bdist_mpkg_support.py
-rw-r--r-- 1 andrew admin  1979 2008-03-28 17:45 bundle_docs.py
-rw-r--r-- 1 andrew admin  4057 2008-03-28 17:45 config_darwin.py
-rwxr-xr-x 1 andrew admin  9417 2008-02-11 02:39 config_msys.py
-rw-r--r-- 1 andrew admin  4620 2008-02-11 02:39 config.py
-rw-r--r-- 1 andrew admin  6360 2008-01-19 21:26 config_unix.py
-rw-r--r-- 1 andrew admin  6827 2008-02-11 02:39 config_win.py
-rw-r--r-- 1 andrew admin  1799 2006-06-08 03:13 distutils_mods.py
-rw-r--r-- 1 andrew admin  2433 2008-02-11 02:39 dll.py
drwxr-xr-x 5 andrew admin  4096 2008-03-28 18:36 docs
drwxr-xr-x 4 andrew admin  4096 2008-03-28 18:36 examples
-rw-r--r-- 1 andrew admin  7932 2008-03-28 17:45 install.html
drwxr-xr-x 3 andrew admin  4096 2008-03-28 18:36 lib
-rwxr-xr-x 1 andrew admin  9520 2008-03-28 17:45 makeref.py
-rw-r--r-- 1 andrew admin  4944 2008-02-11 02:39 mingw32ccompiler.py
-rw-r--r-- 1 andrew admin  1423 2008-03-03 05:06 mingw32distutils.py
-rw-r--r-- 1 andrew admin   484 2008-02-11 02:39 mingwcfg.py
-rw-r--r-- 1 andrew admin 24491 2008-02-11 02:39 msys_build_deps.py
-rw-r--r-- 1 andrew admin  1030 2008-02-11 02:39 msysio.py
-rw-r--r-- 1 andrew admin  9916 2008-02-11 02:39 msys.py
-rw-r--r-- 1 andrew admin   535 2008-03-28 18:36 PKG-INFO
-rw-r--r-- 1 andrew admin  5889 2008-03-28 17:58 readme.txt
-rwxr-xr-x 1 andrew admin   756 2008-01-19 21:26 run_tests.py
-rw-r--r-- 1 andrew admin  3042 2008-02-03 17:20 Setup.in
-rwxr-xr-x 1 andrew admin  8611 2008-03-28 17:58 setup.py
drwxr-xr-x 2 andrew admin  4096 2008-03-28 18:36 src
drwxr-xr-x 2 andrew admin  4096 2008-03-28 18:36 test
-rw-r--r-- 1 andrew admin 31102 2008-03-28 17:45 WHATSNEW
andrew@andrew-laptop:~/Desktop/pygame-1.8.0release$ 

```
Here is Pastebin if you prefer:  [http://pastebin.com/m2774329f]("http://pastebin.com/m2774329f")

---

### Post by L337_K3y5 on 2008-07-07
> **tamoneya said:**
> Typically however the problem when you get this error is that the file doesnt have executable permissions```
sudo chmod +x configure
```
This is what I get:
```
chmod: cannot access `configure': No such file or directory
```

---

### Post by tamoneya on 2008-07-07
it appears that this is compiled in python like this:```
python config.py
``` 
If that still doesnt work take a look in the install.html file.  It appears that this is compiled different that most programs.

---

### Post by L337_K3y5 on 2008-07-07
> **tamoneya said:**
> it appears that this is compiled in python like this:```
python config.py
```
I get this:  ```
andrew@andrew-laptop:~/Desktop/pygame-1.8.0release$ python config.py
Using UNIX configuration...


Hunting dependencies...
SDL     : found 1.2.12
FONT    : found
IMAGE   : found
MIXER   : found
SMPEG   : found 0.4.5
PNG     : found
JPEG    : found
SCRAP   : found

If you get compiler errors during install, doublecheck
the compiler flags in the "Setup" file.

andrew@andrew-laptop:~/Desktop/pygame-1.8.0release$

```
Also, whoah, thats some wierd crap, never used the setup before and in terminal it brought me up to Image Majick or somthing.

---

