---
title: "Sata drivers"
date: 2007-12-07
forum: General Help
---

### Post by lunxer on 2007-12-07
Hello!
I have a sunix SATA2100 with a initio 1623 chip on it, there are no good support for that card in the 2.6 kernel (No LBA48 :/) 

So i contacted the manufacturer and got a zip file with the drivers that he said should work for 2.6.
Now, how do install these?

[http://kranvatten.se/Linux.zip](http://kranvatten.se/Linux.zip)

Thanks!

---

### Post by lunxer on 2007-12-07
I tried to copy the files from that zip into a 2.6 src, but when i run "make clean && make mrproper" 
i get this error

/usr/src/linux-2.6.23.9/drivers/ide/Makefile:81: /usr/src/linux-2.6.23.9/Rules.make: No such file or directory
make[2]: *** No rule to make target `/usr/src/linux-2.6.23.9/Rules.make'.  Stop.
make[1]: *** [drivers/ide] Error 2
make: *** [_clean_drivers] Error 2

---

### Post by mali2297 on 2007-12-07
I used apt-file to search for packages that include Rules.make. This is the only package that showed up:
> 
rtlinux - Real-Time-Linux, a POSIX-compatible hard realtime operating system.

I don't know whether it helps. :-|

---

### Post by lunxer on 2007-12-07
thanks for trying, but i don't think that would work, since its looking for that in the newly unpacked src of 2.6.

---

