---
title: "ndiswrapper 1.44 installation problem"
date: 2007-05-27
forum: General Help
---

### Post by Siwelb on 2007-05-27
I just recently upgraded to Feisty, and the other day I was attempting to install the latest version of ndiswrapper (1.44). After I unzipped the .gz file, I tried to issue the "make" command, but got this error:

> 
make -C driver install
make[1]: Entering directory '/home/brian/Desktop/ndiswrapper-1.44/driver'
Can't find kernel build files in /lib/modules/2.6.20-15-386/build;
give the path to kernel build directory with
KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory '/home/brian/Desktop/ndiswrapper-1.44/driver'
make: *** [install] Error 2


I've only been using Ubuntu (and Linux) for about a month now, so I'm pretty inexperienced. Could somebody give me a clue as to what's going on and what I should do to correct this problem? Thanks!

---

### Post by benmoreassynt on 2007-05-27
> **Siwelb said:**
> I just recently upgraded to Feisty, and the other day I was attempting to install the latest version of ndiswrapper (1.44). After I unzipped the .gz file, I tried to issue the "make" command, but got this error:


Is there any reason why you are trying to compile it yourself? If not, use synaptic package manager, search for 'ndiswrapper' and schedule it for installation. Much easier all round. A lot of new people try to compile, thinking they have to install in a 'Windows' fashion. There is no such thing, and it is just painful as a rule. Synaptic is the way to do it.

---

### Post by Siwelb on 2007-05-27
The only reason I was compiling was because the version of ndiswrapper that Synaptic installs wasn't working for me...I would try to install the driver for my wireless adapter, but it keeps telling me that the driver is invalid.

---

