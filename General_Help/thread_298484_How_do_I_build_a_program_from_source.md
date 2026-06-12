---
title: "How do I build a program from source?"
date: 2006-11-12
forum: General Help
---

### Post by thenetduck on 2006-11-12
Hi, 
  I have often tried, but was never successful in building a program from source. I just downloaded the latest MySQL server to try to build that from source and get it up and running on my computer so I can play with databases. Does anyone know how I can learn how to do this? Or is there a certain step of how things should normally be down when building for source? I really would like to learn this as I have used Ubunt for a while and don't like to have to just wait until there is the proper .deb file out for a program that I want. Thanks,
 

 The Net Duck
 
 P.S. I do have the build essentials all ready installed.

---

### Post by chriscando on 2006-11-12
A good place to start is to install gcc and other compilers by
```
sudo apt-get install build-essential
```
Next use
```
uname -r
```
to find the kernel version you are currently using.
Then look for your kernel headers using synaptic.
Then typically all you have to do is something like this in the directory with the source code.
```
./configure
make
sudo make install
```
but check with source on specific instructions
Hope this helps

---

### Post by Peepsalot on 2006-11-12
Try this
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

