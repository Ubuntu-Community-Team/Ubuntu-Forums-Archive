---
title: "Problem compiling Ralinktech driver using Makefile!"
date: 2008-02-01
forum: General Help
---

### Post by eduardo.mendes on 2008-02-01
Hi everyone,

I am new to Linux, and bláblá, you know the story, lots of probs

I have a Wireless G USB D-Link DWL-G122 version 3.10 C1, which I am trying to install in Ubuntu 7.10 (Gutsy Gibbons). I got the Linux driver from [http://www.ralinktech.com/ralink/Hom...ort/Linux.html](http://www.ralinktech.com/ralink/Hom...ort/Linux.html), and downloaded the RT2500USB(RT2571/RT2572) (source Code).

After unpacking that bundle, have been trying to follow the instructions in the README file. My current problem is, when trying to execute the Makefile, I get the following error:
$ make
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/eduardo/Downloads/USB G Wireless adapter/RT25USB-SRC-V2.0.8.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** No rule to make target `G'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2

Below, I am also posting the result (pls see attachment) when I run make -d. Does any of you have any idea why this is happening? Where does this G target come from? Thanks in advance for any help you can give. I have already lost so much time with this issue, that I am even ashamed to tell :-(

P.S. I have also placed this post in the Networking & Wireless forum, but thought that, given the nature of the problem, this would be a more appropriated place for it.

---

### Post by renzokuken on 2008-02-01
have you installed build-essential?

if not run ```
sudo apt-get install build-essential
```

and then try **make** again

you will need a net connection though (do you have a wired connection available?) if not i think its on the CD

---

### Post by eduardo.mendes on 2008-02-01
Thanks Renzokuken. Just did that, and also have removed empty spaces from the directory where I was keeping this driver's files... Am now getting some compile errors, but that should now be a different problem, and hopefully one step further from where I was before. Thanks again! :-)

---

