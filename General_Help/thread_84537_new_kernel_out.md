---
title: "new kernel out"
date: 2005-10-31
forum: General Help
---

### Post by djjuice on 2005-10-31
so the new kernel is out...is there a way i can compile it and use it with ubuntu? Does it work like that?

---

### Post by daller on 2005-10-31
Well, it's quite hard!

I did this:

sudo apt-get install build-essential kernel-package libncurses5-dev 

sudo mkdir /usr/src/

cd /usr/src/ 

sudo apt-get source linux-image-2.6.12-9-386 

(If you are thinking abaout 2.6.14, just download it - untar it to /usr/source/linux-source-2.6.14 - and make the symlink to this folder instead)

sudo ln -s linux-source-2.6.12-2.6.12 linux 

cd linux 

sudo make menuconfig

**** THIS IS THE TRIGGY PART, WHERE YOU HAVE TO CONFIGURE EVERYTHING  ****

sudo vi Makefile

	EXTRAVERSION = -custom (or whatever)

make

sudo make install

sudo update-grub

....Someone correct me, if there is an easier way to do this...

---

### Post by Kyral on 2005-10-31
There is a new option in the kernels (Actually since 2.6.13-something) that allows you to append a custom version string automatically in kernel make menuconfig, so when you do a make && make modules_install install it makes the bzImage with that string automatically appended

---

### Post by 23meg on 2005-10-31
I'd like to learn how to apply the Ubuntu patches to the stock Breezy kernel to a newer kernel version.. if that's possible.

---

### Post by Kyral on 2005-10-31
Um...I dunno? The vanilla 2.6.14 kernel is working fine for me

---

### Post by 23meg on 2005-10-31
No hardware recognition issues? Do you have mostly recent or old hardware? Perhaps (part of) Ubuntu's patches make it into upstream? I'd like to hear the official word on this.

---

### Post by Kyral on 2005-10-31
I dunno what patches Ubuntu applies to the kernel....maybe someone on the KernelTeam could answer this. I'm just saying in my case it works (well, my Wireless card doesn't, but that was because I was an idiot and forgot to compile in support)

---

### Post by 23meg on 2005-10-31
Btw, [this thread]("http://www.ubuntuforums.org/showthread.php?t=84174") has some detailed instructions.

---

### Post by RAOF on 2005-10-31
Or, you could use the generic Kernel compile howto :)

[https://wiki.ubuntu.com/KernelHowto?highlight=%28kernelhowto%29](https://wiki.ubuntu.com/KernelHowto?highlight=%28kernelhowto%29)

You don't need to get the kernel sources through apt - exact same steps will work if you download your sources direct from kernel.org.  

I personally recommend running "make oldconfig" before running "make menuconfig/gconfig/xconfig".  This starts off by setting all the options to the same as your current kernel, and the ubuntu kernels come with sane options set :)

---

