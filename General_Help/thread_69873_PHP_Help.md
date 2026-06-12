---
title: "PHP Help"
date: 2005-09-28
forum: General Help
---

### Post by Toby2 on 2005-09-28
Hello,

I'm trying to install PHP 5 on my Ubuntu computer. But, on my Ubuntu computer, I don't have an Internet connection. And the computer I am on now has the Internet, and it has Windows XP. So far I've tried all the tutorials at [https://wiki.ubuntu.com//?action=fullsearch&context=180&value=php&titlesearch=Titles](https://wiki.ubuntu.com//?action=fullsearch&context=180&value=php&titlesearch=Titles), but none of them have helped. I've tried downloading this file: [http://www.php.net/get/php-5.0.4.tar.bz2/from/ie.php.net/mirror](http://www.php.net/get/php-5.0.4.tar.bz2/from/ie.php.net/mirror) (and puting it on my flash drive so I can run it on my Ubuntu computer) but I don't know how to install it.

Can anyone give me instructions on how to install PHP 5 on an Ubuntu machine without the Internet? I've already installed Apache.

After I get PHP working, I'll also need to install MySQL.

- Toby

---

### Post by Zotova on 2005-09-28
You will have to compile the file you have downloaded. To do this follow these instructions.

1. Extract the php tar.gz file.
2. Open terminal
3. Navigate to the folder with the php files in. To do this use the 'cd' command followed by the directory. e.g. cd /home/user/php
4. Once in the correct directory type and enter 

./configure

^ This might take a while
5. Type and enter:

make

then type:

make install

--

This should then install php on your machine. If you get any errors then you will probably need other packages to run php on the machine. I hope this helps you in some form.

---

### Post by Toby2 on 2005-09-28
Ok, thanks, I'll try it out right now.

-- EDIT --
I got an error:

```
 toby@ubuntu:~$ cd /home/toby/Desktop/php-5.0.4
toby@ubuntu:~/Desktop/php-5.0.4$ ./configure
creating cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH
```

I must need another package. So, what package(s) do I install?

---

### Post by simon w on 2005-09-28
You need to install the GCC compile ;)

---

### Post by Zotova on 2005-09-28
Is there no way what-so-ever you could get this computer on the net for a few moments to download these packages via synaptics? As it would make what you want to do a whole lot easier and less time consuming.

---

### Post by Toby2 on 2005-09-29
Well, it doesn't have a modem... Soon I'm hopefully going to get a wireless network adapter to network up with the computer with the Internet. But that'll be in a while, about 4 weeks time. I'll see what I can do though. Is there any possible way to install it without the internet though?

---

