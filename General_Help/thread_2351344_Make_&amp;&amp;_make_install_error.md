---
title: "Make &amp;&amp; make install error"
date: 2017-02-02
forum: General Help
---

### Post by nals2 on 2017-02-02
Hello
I want to install some drivers and my guide explains after navigate in a folder where they are, I have to run make && make install. Here start the problem, because the result of command is "No such file or directory", indeed the "build" file is empty. Then I install another linux-headers. Now I want when I run make && make install, the command search in "build" folder of the new kernel and not in the old. How do I do?  

Regards

---

### Post by Perfect Storm on 2017-02-02
you can change directory with the command **cd**
eg. cd /home/<user>/build
or type **cd** then drag the folder into the terminal. Then hit <enter>

**cd ..** move you one level up in the directory
plan **cd** move you directly to your home directory.

after that run the **make && sudo make install** command.

Any trouble please post the terminal output.

---

### Post by nals2 on 2017-02-02
I explain better, these are the commands 

cd /home/user/Downloads/drivers
~/Download/drivers$

then go in root mode with 'su' 
~/Download/drivers$ su

and run make && make install

/home/user/Downloads/drivers# make && make install

the result is that the command searches always in /lib/modules/oldkernel/build and not in /lib/modules/newkernel/build

---

### Post by Perfect Storm on 2017-02-02
Try symblink it

```
sudo ln -s /lib/modules/oldkernel/build /lib/modules/newkernel/build
```

---

### Post by steeldriver on 2017-02-02
Is the kernel headers package for you current kernel actually installed?

```

dpkg -l linux-headers-`uname -r`

```

it might not be - if you installed the previous headers package manually instead of installing the `linux-headers-generic` package

---

### Post by nals2 on 2017-02-02
> sudo ln -s /lib/modules/oldkernel/build /lib/modules/newkernel/build

Doesn't solve

> Is the kernel headers package for you current kernel actually installed?

     Code:
     dpkg -l linux-headers-`uname -r` 
it might not be - if you installed the previous headers package  manually instead of installing the `linux-headers-generic` package                 


  I see that it isn't installed. How do install it?

---

### Post by steeldriver on 2017-02-02
install the linux-headers-generic package

---

