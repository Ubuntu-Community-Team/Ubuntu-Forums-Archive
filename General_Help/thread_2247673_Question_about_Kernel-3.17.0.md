---
title: "Question about Kernel-3.17.0"
date: 2014-10-09
forum: General Help
---

### Post by michael210 on 2014-10-09
Hallo everyone, i have some questions about compilling new Kernel.
The way i did was:
1
```
sudo apt-get install libncurses5-dev
```
2
```
wget https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.17.tar.xz
```
3
```
tar -xJvf linux-3.17.tar.xz
```
4
```
cd linux-3.17
```
5
```
cp /boot/config-`uname -r` .config
```
6
```
yes "" | make oldconfig
```
7
```
make -j2 bzImage modules
```
8
```
sudo make modules_install install
```
9
```
sudo reboot
```
and after reboot:
```
lsb_release -a
```
i got:
> Linux Michael **3.17.0** #1 SMP Thu Oct 9 17:39:28 CEST 2014 x86_64 x86_64 x86_64 GNU/Linux
.
Well, my Ubuntu (64BIT) works fine, so my questions are:
1
did i used the right way
2
If, let's say, i have a device (eg. wireless card) which didn't work with the previous kernel version but works with the Latest kernel version, will that device work using the above steps or i have to issue another commands.
Thank you,

---

### Post by michael210 on 2014-10-16
> **michael210 said:**
> 
If, let's say, i have a device (eg. wireless card) which didn't work with the previous kernel version but works with the Latest kernel version, will that device work using the above steps or i have to issue another commands.
Thank you,
Can someone please answear to that question.
Thank you.

---

### Post by Alireza_Zamani on 2014-10-16
hi
you can install that from here : [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
good luck

---

### Post by michael210 on 2014-10-17
i never sayed that i need a way to compile a kernel. please READ AGAIN my question.
Thank you.

---

### Post by Doug S on 2014-10-17
I saw your original post, but didn't reply because you are compiling the kernel in a way that I am not familiar with. Note that there seems to be several ways to compile the kernel.

I think the answers to your two questions are yes and yes.

However, note that you are compiling the kernel.org kernel and not the Ubuntu version of the kernel. I use the kernel.org kernel also, for release candidate testing. There are some subtle differences. For example, I am unable to reliably run my Virtual computer quests when I am using the kernel.org kernel.

Edit: Here is how I do it:```
Get and compile the mainline kernel:

see also: https://wiki.ubuntu.com/KernelTeam/GitKernelBuild
I do things a little different.

mkdir temp-k-git-3.10rc4
cd temp-k-git-3.10rc4
git clone   git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
cd linux
ls -l /boot
cp /boot/config-3.10.0-031000rc4-generic .config
scripts/config --disable DEBUG_INFO

time make -j8 deb-pkg          <<< note -j6 on the 6 CPU 32 bit virtual machine

or

time make -j8 deb-pkg LOCALVERSION=-dirk    <<< For a localized verion name append

cd ..
sudo dpkg -i linux-headers-3.10.0-rc4+_3.10.0-rc4+-1_amd64.deb
sudo dpkg -i linux-image-3.10.0-rc4+_3.10.0-rc4+-1_amd64.deb

... Say sometime later you want to get any changes and recompile ...

cd ~/temp-k-git-3.10rc4/linux
git pull
time make -j8 deb-pkg
cd ..
sudo dpkg -i linux-headers-3.10.0-rc5_3.10.0-rc5-2_amd64.deb
sudo dpkg -i linux-image-3.10.0-rc5_3.10.0-rc5-2_amd64.deb
```If you don't want to use git then just merge into your method at step 4 "cd linux-3.17" where I do "cd linux"

---

### Post by michael210 on 2014-10-23
> **Doug S said:**
> I saw your original post, but didn't reply because you are compiling the kernel in a way that I am not familiar with. Note that there seems to be several ways to compile the kernel.

I think the answers to your two questions are yes and yes.
, 
i discovered my self that, by compiling kernel on one machine wich didn't worked a device before, thank you.
I  got rid of a lot of code, i succided to compile the last kernel (3.17.1) to work just with devices i have inside my Laptop.
Ubuntu boot's between 15-20 seconds, default takes more than 2-3 minutes LoL.

---

