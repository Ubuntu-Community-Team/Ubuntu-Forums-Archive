---
title: "Commands not found?"
date: 2007-05-16
forum: General Help
---

### Post by shadow_boi on 2007-05-16
Sorry, I am a newbe to Ubuntu and to this forum.

I have installed Ubuntu with VMware under window XP.

Commands like cd, man, mkdir... work well

But commands like make, run couldn't work. 
It said command not found.  (i have a makefile on that folder, and i want to compile and run a .c file )

Can any one tell me what caused this problem?

Thanks.

---

### Post by anaconda on 2007-05-16
You cant use programs that are not installed!

Ubuntus default installation doesn't have the compilers installed.. (dont know why). actually they are in the Ubuntu-CD, but you have to install them separately.

Just open a terminal and type:
```
sudo apt-get install build-essential
```
to install the needed package.

---

### Post by rich.bradshaw on 2007-05-16
If you have a file in a directory that is exexutable, you have to write the full path for some reason, so if there is  a configure script you need

./configure

not just 

configure

or what ever. I would get build-essential as well, as it has most compilers etc.

---

