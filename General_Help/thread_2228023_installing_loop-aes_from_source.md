---
title: "installing loop-aes from source"
date: 2014-06-05
forum: General Help
---

### Post by Hotchilli on 2014-06-05
installing loop-aes from source on pricese where should I point the make file to? not sure where the kernel is

thanks



ana@ubuntu:~$ cd /usr/src
ana@ubuntu:/usr/src$ ls
linux-headers-3.11.0-15          linux-headers-3.11.0-22-generic
linux-headers-3.11.0-15-generic  loop-AES-v3.7b
linux-headers-3.11.0-22
ana@ubuntu:/usr/src$ cd loop-AES-v3.7b
ana@ubuntu:/usr/src/loop-AES-v3.7b$ sudo make
[sudo] password for ana 
Unable to guess linux kernel source directory. Please specify
directory like this:  make LINUX_SOURCE=/usr/src/linux-2.2.20aa1
make: *** [all] Error 1
ana@ubuntu:/usr/src/loop-AES-v3.7b$


i think i need to install the source package  but apt-get cannot find it?

ana@ubuntu:~$ uname -r
3.11.0-22-generic
ana@ubuntu:~$ sudo apt-get install linux-source-3.11.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-source-3.11.0 

;)

---

