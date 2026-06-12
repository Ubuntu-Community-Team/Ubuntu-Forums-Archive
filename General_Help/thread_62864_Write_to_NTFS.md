---
title: "Write to NTFS?"
date: 2005-09-06
forum: General Help
---

### Post by Gibbz on 2005-09-06
Ive tryed seting up captive, and also tryed the demo of paragon ntfs for linux. But neither will install. Has anyone got a how-to guide on the topic?

---

### Post by odin on 2005-09-06
just guessing but do you have ntfs write support in your kernel?

---

### Post by Gibbz on 2005-09-06
im pretty n00b. How do i add ntfs support into my kernel, under the last version of ubuntu captive worked fine but this time it complains of lufs or something?

---

### Post by odin on 2005-09-06
well I have never done it but this should work and you will not break anything.

type uname -r to know what kernel you have.

then download from [www.kernel.org/pub/linux/kernel](www.kernel.org/pub/linux/kernel) the kernel you have.

untar it  with "tar -xvzf file"         if the file is a linux-xxxx.tar.gz or
with               "tar -xvjf file"         if the file is a linux-xxxx.tar.bz2.

after that go to directory created after untar it and type "make menuconfig"
At the end of the menu there is an option called "Load an Alternate confuration file".Select it and load you kernel configuration (the file you have to load it should be called /boot/config-kernel_verion where kernel version is 2.6.8 or whatever version you have)

Then you go to File Systems->DOS/FAT/NT filesystems and check if NTFS write support is select it.


If it is not you have to recompile your kernel so tell me and i'll point you to another thread where there is a nice howto for doing that.

PD:This something I just thought about and that should work.Maybe there is other ways to find out if your probelm is that but I dont know them yet...  :roll: 
I'll search the net looking for another solution if this doesnt work.
good luck and hope to be helpfull

---

### Post by Gibbz on 2005-09-06
So this would then use the built in ntfs? ive heard this version is not stable. Is this true?

---

### Post by frodon on 2005-09-06
There is no good solution for the moment to write on ntfs partitions, captive is really slow and will sometime fail, it could be useful if you need sometimes to write small files on your ntfs partitions but will never be a good way to live with linux. If you really want to use linux as your first OS you should convert your partitions to FAT32 (say thank you to Bill  :-? )

---

