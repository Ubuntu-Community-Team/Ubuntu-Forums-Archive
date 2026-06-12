---
title: "mkdir cannot create directory : not a directory"
date: 2013-02-02
forum: General Help
---

### Post by Randwulff on 2013-02-02
I'm trying to install pygobject-3.0.4 from source (installing from source is new to me) and make install appears to be exiting with error:

/bin/mkdir: cannot create directory `/usr/bin/python': Not a directory

/usr/bin/python is the symbolic link to my python installation, so I don't know why pygobject wants to make a directory there, if that is indeed what's going on.

I've been looking around in the source directory for whichever shell script is trying to mkdir there, but can't find it? A little lost here and grateful for any help :confused:

---

### Post by serpantman on 2013-02-03
Manually creating the directory can work in these situations. Sometimes it's is a permissions issue. Can you give me more information? The documentation you are using, what part you are at. More text from your shell.

---

### Post by monkeybrain2012 on 2013-02-03
Try "sudo make install"

---

### Post by sanderj on 2013-02-03
> **Randwulff said:**
> I'm trying to install pygobject-3.0.4 from source (installing from source is new to me) and make install appears to be exiting with error:

/bin/mkdir: cannot create directory `/usr/bin/python': Not a directory

/usr/bin/python is the symbolic link to my python installation, so I don't know why pygobject wants to make a directory there, if that is indeed what's going on.

I've been looking around in the source directory for whichever shell script is trying to mkdir there, but can't find it? A little lost here and grateful for any help :confused:


Technical explanation: If the file exists, you can't make a directory with the same name:

```
sander@R540:~$ touch blabla
sander@R540:~$ mkdir blabla
mkdir: cannot create directory `blabla': File exists
sander@R540:~$ 
```

But why is pygobject trying to make that directory?

What is the ./configure you use? Did you just run "./configure", or did you add parameters or settings?

---

### Post by rnerwein on 2013-02-03
> **Randwulff said:**
> I'm trying to install pygobject-3.0.4 from source (installing from source is new to me) and make install appears to be exiting with error:

/bin/mkdir: cannot create directory `/usr/bin/python': Not a directory

/usr/bin/python is the symbolic link to my python installation, so I don't know why pygobject wants to make a directory there, if that is indeed what's going on.

I've been looking around in the source directory for whichever shell script is trying to mkdir there, but can't find it? A little lost here and grateful for any help :confused:
hi
i don't know what " pygobject-3.0.4 " is. but it's buggy. python is a link to pythonX.Y and that's the real python software. be lucky that it don't works. if the system haven't an ey on it you get rid of your python.
cheers

---

### Post by nimpoura5 on 2013-12-16
Hello ,I am new to Ubuntu. I am trying to install Lemur(indri) on ubuntu 12. I 've just followed the commands cd,./configure --prefix=/install/path
./make
but when I procced to make install it gives this result
./make install
nikol@nikol-laptop:~/Downloads/indri-5.5$ sudo make install
/usr/bin/install -c -m 755 -d /home/nikol/Downloads/indri-5.5/INSTALL/bin
/usr/bin/install: cannot create directory `/home/nikol/Downloads/indri-5.5/INSTALL': Not a directory
make: *** [/home/nikol/Downloads/indri-5.5/INSTALL/bin] Error 1.

Could anyone help me please?

---

