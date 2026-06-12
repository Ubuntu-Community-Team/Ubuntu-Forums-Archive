---
title: "nvidia beta driver"
date: 2006-11-04
forum: General Help
---

### Post by johnny9794 on 2006-11-04
Hi all, i would like to install Beta Graphics Driver (NVIDIA) so i may install Beryl/AIGLX (Nvidia).

But i am having a problem, I read and followed the tut on "How to install Beta Graphics Driver (NVIDIA)" but when I went to install "libxorg-sched-yield-hack0" but got "Couldn't find package libxorg-sched-yield-hack0"

>   johnny@linux-box:~$ sudo apt-get install nvidia-glx libxorg-sched-yield-hack0
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libxorg-sched-yield-hack0
johnny@linux-box:~$ sudo apt-get install libxorg-sched-yield-hack0
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libxorg-sched-yield-hack0
 

Could someone help me out plz or have any suggestions on what i shall do?

Here is my sources list file.

Thank You.

---

### Post by johnny9794 on 2006-11-05
Ok i got it all working "the bete driver" I would not suggest using 
the ubuntu starter guide on  How to install beta driver (Nvidia).

I would suggest using 

[http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers](http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers)

Works GREAT!!! :)

---

### Post by ~LoKe on 2006-11-05
The yield hack was said to be useless and unneeded, so it was removed.

---

