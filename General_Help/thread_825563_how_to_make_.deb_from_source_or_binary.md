---
title: "how to make .deb from source or binary??"
date: 2008-06-11
forum: General Help
---

### Post by maq21 on 2008-06-11
hi all
im new here and i wnana know how to make .deb from source code or binary code

---

### Post by vikrant82 on 2008-06-11
> **maq21 said:**
> hi all
im new here and i wnana know how to make .deb from source code or binary code

```
sudo apt-get install checkinstall
```

```
checkinstall --help
```

In most cases 

```
./configure
make
checkinstall -D --install=no
```

Doing this will ask you some questions. Pressing enters would do for most of them. Eventually you will get a nice shiny, deb which you can install offline.

---

### Post by Xiong Chiamiov on 2008-06-11
If you're making a .deb for the purposes of being able to uninstall a program from the package manager, compile as usual, but replace the make command with checkinstall.

For distribution purposes, follow [this guide]("http://ubuntuforums.org/showthread.php?t=51003").

---

### Post by loell on 2008-06-11
there's **[apt:checkinstall]("apt:checkinstall")** for personal deb packaging/ none distributable.

and theres the proper way..

[ubuntu packaging guide]("https://help.ubuntu.com/6.10/ubuntu/packagingguide/C/index.html")


**Edit: ahh.. beaten two times :D**

---

### Post by vikrant82 on 2008-06-11
Just to make it interesting, for already installed programs you could do something like : 

```
fakeroot -u dpkg-repack `dpkg --get-selections | grep program_name | cut -f1`
```

So you could do

```
./configure
make
sudo make install
fakeroot -u dpkg-repack `dpkg --get-selections | grep program_name | cut -f1`
```

- which should also give you a deb.

---

### Post by abhiroopb on 2008-06-11
What are the prolems with using checkinstall? As in why isn't checkinstall the "official" method?

---

### Post by vikrant82 on 2008-06-11
May be because it assumes that the dependencies are already installed. That's why most of the times it work great for the system on which the deb was created. 

However, with a custom control file you can specify the depenedencies as well.

Refer to following thread for the same.

[http://ubuntuforums.org/showthread.php?t=169333]("http://ubuntuforums.org/showthread.php?t=169333")

---

