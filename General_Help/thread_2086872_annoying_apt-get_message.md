---
title: "annoying apt-get message"
date: 2012-11-22
forum: General Help
---

### Post by mnicholson01 on 2012-11-22
Hi all, I'm not sure if this is the correct forum for this question, but hopefully you can point me in the right direction.

I recently installed 12.10 64-bit on my laptop, and just now installed one of my favorite programs, Guitar Pro 6. Guitar Pro only supports 32-bit Linux, however this is not my first time installing it on a 64-bit system, and after only a few minutes the program was up and running flawlessly.

However, in my taskbar I now have a red circle with a horizontal white line which informs me that one of my packages has an unmet dependency. Upon running apt-get:

```
matt@apollo:~$ sudo apt-get install
[sudo] password for matt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 guitarpro6:i386 : Depends: gksu:i386 but it is not installed
E: Unmet dependencies. Try using -f.
matt@apollo:~$ 

```'apt-get -f install' only wants to remove Guitar Pro, and the dependency, gksu, doesn't seem to be necessary, as when I ran the GP6 Updater I was greeted with a graphical prompt asking for my password (which is what gksu is for, right?).

So, how can I get apt-get to ignore this broken dependency and quit trying to remove GP6?

---

