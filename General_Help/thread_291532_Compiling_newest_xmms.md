---
title: "Compiling newest xmms"
date: 2006-11-02
forum: General Help
---

### Post by johnny9794 on 2006-11-02
I am new at compiling.

I have instructions on how-to compile and install the newest xmms but when i run ./configure i get an error stating "configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details. 

This error is on line 69

Would anyone like to help me on this :)?

Thanks.

---

### Post by taurus on 2006-11-02
```

sudo aptitude update
sudo aptitude install build-essential

```

---

### Post by johnny9794 on 2006-11-02
Well i believe i have build-essential installed because i had to install it to install my xgl.nwiz which i installed xgl/nwiz last night.
[edited]
ok i did that and its installing now so it must be a different form of build-essential.

---

### Post by taurus on 2006-11-02
```
gcc -v
```

---

### Post by johnny9794 on 2006-11-02
ok new error while running ./configure

> checking for GLIB - version >= 1.2.2... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***
johnny@linux-box:~/Desktop/xmms-1.2.10$

I cannot upload the new config.log its to big.

---

### Post by jmacak on 2006-11-02
Hi Johnny

It's just telling you that it requires at least that version of the glib libraries.  

That's how it goes when you compile on your own.  Configure checks to see if you have all of the prerequisites, if you don't it tells you.  You install what it asks for and re-run configure and then it tells you about another missing prerequisite, which you install.  wash rinse repeat.

That's why folks like to install packages and use tools like apt rather than manually compiling things.

cheers

joe

---

### Post by rattking on 2006-11-02
that's in the libglib1.2-dev package

you can use apt-file to find out what package contains the missing file

apt-file search glib-config
make sure you update first
sudo apt-file update

---

### Post by taurus on 2006-11-02
Looks like you need libglib2-dev also...

---

### Post by johnny9794 on 2006-11-02
ok thank you both for your support :).

---

### Post by johnny9794 on 2006-11-02
Ok update. I am compiling as i type right now and I found a great tutorial on  How to Compile Free Software Apps and here is the link for it if any other newbies like myself would like to compile apps or are curious about compiling :D.

[http://www.pcworld.com/article/id,127601-page,2-c,linux/article.html](http://www.pcworld.com/article/id,127601-page,2-c,linux/article.html)

---

