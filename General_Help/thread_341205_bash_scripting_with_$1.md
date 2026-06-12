---
title: "bash scripting with $1"
date: 2007-01-18
forum: General Help
---

### Post by oscartheduck on 2007-01-18
I want to write an alias that changes to a directory then lists the contents of the directory and remains in the directory.
I want
```
lc foo
```
To be equivalent to

```
cd foo
ls
```

Sounds reasonably simple.

I tried

```
alias lc="cd $1 && ls"
```

But this changes directory, lists the contents, then returns to the original directory.

So I tried

```
cd $1 && ls && cd $1
```

This lists the contents of the current working directory, then changes to $1. I tried it in several distros, so I'm assuming I'm misunderstanding something to do with bash scripting.

---

### Post by evilghost on 2007-01-18
alias lc = "cd foo;ls"

---

### Post by oscartheduck on 2007-01-18
You, my friend, are a lifesaver. I can't believe I missed that. Thanks!

---

### Post by evilghost on 2007-01-18
I'll PM you my paypal address :-D 

Always glad to help a fellow Ubuntu user.

---

### Post by chavo on 2007-01-18
Try putting a function in your .bashrc.
```

lc() {
    cd $1
    ls
}


```

I'm not sure an alias can handle the command line argument correctly.

---

### Post by evilghost on 2007-01-18
> **chavo said:**
> Try putting a function in your .bashrc.
```

lc() {
    cd $1
    ls
}


```

I'm not sure an alias can handle the command line argument correctly.

Alias will work.

```

luser@ids-m8cj4:/$ cd /
luser@ids-m8cj4:/$ alias foo="cd ~/;ls;echo -n;echo 'Current Directory:  ';pwd"
luser@ids-m8cj4:/$ foo
Desktop                Firefox_wallpaper.png  libwps     maplaptop.sh
Examples               libwpd-0.8.7           logout.sh  minicom.log
Firefox_wallpaper.pgm  libwpd-0.8.7.tar.gz    mapfs.sh   rdp.sh
Current Directory:  
/home/luser
luser@ids-m8cj4:~$ 

```

---

