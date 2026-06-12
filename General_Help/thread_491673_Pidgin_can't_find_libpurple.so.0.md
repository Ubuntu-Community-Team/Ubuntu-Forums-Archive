---
title: "Pidgin can't find libpurple.so.0"
date: 2007-07-03
forum: General Help
---

### Post by duelle on 2007-07-03
I've compiled Pidgin 2.0.1 and 2.0.2 from source as root and as a normal user and whenever I try to start the program nothing happens. Trying to start it from the command line I get: "pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory". Does anyone know why this is happening and how I can fix it? I had Pidgin 2.0.1 installed a few days ago and it worked fine, but then I had to reinstall Xubuntu because I screwed around a little too much and now this is happening.

Edit: Forgot to mention that I have found libpurple.so.0 in /usr/local/lib/ which is where I think it should be. It does exist, Pidgin just can't find it.

---

### Post by NeoLithium on 2007-07-03
Hmmm, depending on how you compiled it, Pidgin may be looking in the wrong spots.  However, Pidgin is available as a debian file that works fine (I'm running 2.02 as well) from GetDeb.net [http://www.getdeb.net/release.php?id=1045](http://www.getdeb.net/release.php?id=1045)

---

### Post by rlgc79 on 2007-09-18
A little late, but here  is one possible solution:

cd /usr/lib
sudo ln -s /usr/local/lib/libpurple.so.0 .

(don't forget the period at the end of the above line)

The problem is that pidgin cannot find the libraries located at /usr/local/lib, even though  I have this folder listed on /etc/ld.so.conf . If anyone knows the reason, please enlighten us :)

---

### Post by kevdog on 2007-09-24
If you ever had pidgin installed from a deb file, the default tree begins at /usr.  When you compile from source, ./configure wants to make the default tree beginning at /usr/local.  Hence what you are do is making a symbolic link from /usr/local/lib back to the /usr/lib directory.

If you recompile pidgin again, but with the following option:
./configure --prefix=/usr

Im fairly certain everything will be fixed since you are specifying you want the default tree to begin in /usr rather than in /usr/local

---

### Post by rlgc79 on 2007-09-24
Dear kevdog,

> **kevdog said:**
> If you ever had pidgin installed from a deb file, the default tree begins at /usr.  When you compile from source, ./configure wants to make the default tree beginning at /usr/local. 

Thanks for this piece of information!

> **kevdog said:**
>   Hence what you are do is making a symbolic link from /usr/local/lib back to the /usr/lib directory. 
That was my idea :)

But do you know why listing the /etc/local/lib folder in the file ld.so.conf does not work? I believe it should be enough, and the above symbolic link would not be necessary...

Many thanks

---

### Post by Charlatat on 2007-09-24
sudo nano /etc/ld.so.conf
     add /usr/local/lib 
sudo ldconfig

That should help

---

### Post by coolnezz on 2008-01-21
> **rlgc79 said:**
> A little late, but here  is one possible solution:

cd /usr/lib
sudo ln -s /usr/local/lib/libpurple.so.0 .

(don't forget the period at the end of the above line)

The problem is that pidgin cannot find the libraries located at /usr/local/lib, even though  I have this folder listed on /etc/ld.so.conf . If anyone knows the reason, please enlighten us :)

this worked for me, thanks a lot :)

---

