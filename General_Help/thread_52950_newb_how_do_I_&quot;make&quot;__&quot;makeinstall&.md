---
title: "newb: how do I &quot;make&quot; / &quot;make/install&quot; sources?"
date: 2005-07-29
forum: General Help
---

### Post by royg1234 on 2005-07-29
Hey,

I just downloaded a .tgz file (855resolution), and all the readme says about installing is:

```

Installing
----------

$ make
$ su
# make install

```

Can someone explain exactly what this means?  (And tell me what I need to type, step by step in terminal)?

---

### Post by Sam on 2005-07-29
Go in a terminal, in the right directory. Then type
```
$ make
```
After that
```
$ sudo make install
```


The '$' means to run the command in a terminal, the '#' means to run the command as root.

'su' is to switch to the superuser (root), but it's not used in Ubuntu, you should use sudo instead.

---

### Post by nemin on 2005-07-29
[QUOTE=royg1234]Hey,

I just downloaded a .tgz file (855resolution), and all the readme says about installing is:

```

Installing
----------

$ make
$ su
# make install

```

Can someone explain exactly what this means?  (And tell me what I need to type, step by step in terminal)?[/QUOTE]
I would not advise you to compile programs from source, though I'll tell you how to do. Open a terminal and `cd` to the directory where you downloaded the .tgz file. Then, enter```
 tar -xzf <tgz file>
```
Next, `cd` into the directory where the tgz file was extracted to and enter:```
make
sudo make install
``` 
That should do it.

---

### Post by Kimm on 2005-07-29
if you install checkinstall removing packages installed from source will be very very simple.

Just apt-get checkinstall and where you would have typed "sudo make install" you type "sudo checkinstall", usualy you only have to press enter whenever your asked for something.

I personaly prefer installing from source... all that I dont like is when something doesnt work and when it takes forever...

---

### Post by royg1234 on 2005-07-30
thanks for the tips

---

### Post by thagame on 2005-07-31
remember though. some stuff requires you to run ./configure before you run make && sudo make install

---

### Post by newage on 2005-08-13
btw check this out: [source installer](http://www.gnu.org/software/sourceinstall/sourceinstall.html) 

maybe this one can make your source installation easier :)

---

