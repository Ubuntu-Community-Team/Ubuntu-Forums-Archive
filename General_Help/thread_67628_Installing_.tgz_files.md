---
title: "Installing .tgz files"
date: 2005-09-20
forum: General Help
---

### Post by ubuntuubuntu on 2005-09-20
How do I install a program that is downloaded as .tgz file?
Thank you!

---

### Post by mlomker on 2005-09-20
That probably means that it has to be compiled, which can vary a great deal.  The following command should uncompress it, anyway:

```

tar zxvf filename.tgz

```

---

### Post by DJ_Max on 2005-09-20
.tgz files are tarballs (gzipped TAR files). It's a compression format like .zip. There should be a README included.

[https://wiki.ubuntu.com/FileCompression](https://wiki.ubuntu.com/FileCompression)

---

### Post by OBnascar on 2005-09-20
[COLOR=Blue]ubuntuubuntu wrote: How do I install a program that is downloaded as .tgz file?[/COLOR]


It isn't as easy as someone explaining here in one post, it will take a lot of home work. A good book will help. Here is one web page to look at: 
[[COLOR=Orange]CLICK HERE[/COLOR] ](http://developer.gnome.org/doc/API/2.0/gtk/gtk-building.html) 

Also do a google search, this will keep you busy for a while. Then post back when you understand some of the basics and someone should be able to help you then with any remaining questions, ok ?

Best Regards,
jerry

---

### Post by ppl on 2005-09-20
In my case, I uncompress it to a folder, and try to find a file named install, open it and following the instruction inside about how to install it, it should tell u how to compile it. like :
1. ./configure
2. make 
3. make check
4. make install
5. make clean
6. done.

Sometimes it is as sample as that, buy make sure you get build essential by following:
sudo apt-get install build-essential.

I am a newbie as well, so not sure is it a general idea  about howto or just in some case, point out if I am wrong! :)

---

### Post by mlomker on 2005-09-21
> a general idea  about howto or just in some case, point out if I am wrong! :)

Yup, that's the general process.  Where it gets tricky is that sometimes you have to download various development files, kernel headers, etc. that the program needs for the ./configure to finish.  Determining what you need can be the hard part--packages have different names in different distributions and the install instructions are always generic.

Post a link to the package and post the ./configure errors and someone might be able to help.

---

