---
title: "Huge headache trying to install Nvidia Nforce drivers"
date: 2005-05-18
forum: General Help
---

### Post by smu johnson on 2005-05-18
Hey dudes,

I'm trying to install the nForce drivers from nvidia.com in ubuntu, and nothing is working right... sighs... 

1)  It whined that it couldn't find the kernel source to build a module..
SOLUTION:  Used synaptic to install linux-source-2.6.10 or whatever... untarred it in the /usr/src directory, then tried again...

2) Whined that it still couldn't find it (why could it not find it?  Isn't using apt-get/synaptic susposed to solve these problems for me and make everything "standard"?  It said to do this...

sudo sh NFORCE-Linux-x86-1.0-0301-pkg1.run --kernel-source-path=/usr/src/linux-source-2.6.10

So now, it is whining about Kernel output path.... !!!!  Does it ever stop?  I've given up, now I no longer have any clue what I'm doing, and am surprised to see other people on forums got this working.

Someone please explain to me what I'm doing wrong!  You'd think that this should "just work" but that doens't seem to be too common with unix-like OS's.

PS:  I'm not "sticking" with what Ubuntu gives me, because I am using forcedeth and getting TERRIBLE results with network transfer speeds... about less than half the speed I should be getting with the onboard NIC.  (I test the speed ALWAYS, ie, with Slackware, it was perfect.)  So I'm willing to try anything.  Maybe if someone has a suggestion about this... then I'll be all ears :)

Thanks for reading!!

---

