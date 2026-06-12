---
title: "What is the proper way to update a kernal?"
date: 2007-07-09
forum: General Help
---

### Post by gottatrieit on 2007-07-09
I was browsing through the internet and came upon a site that had information in it about kernals.  Among the statements was one that caught my eye as I have an AMD Sempron processor in my machine.
As a gNU-Bee, I didn't realize that there are different kernals for different processors.  I attempted to update my machine and may have been partially sucessful as it still runs!  LOL
The kernal I now have is: 2.6.15-28-k7.
The reason I changed was due to a statement within the site that said I could gain some improvement in performance by converting to the AMD kernal from the i386 or x86 kernal that I may be using.
According to the Synaptic listings, there are several types of kernals available: Linux image kernals; Linux headers kernals; and Linux restricted modules kernals.
When I tried to exchange/delete the 386 kernals, I got a message that it would not be advisable as it could possibly "hose" my system!
What do I do to get the best performance out of my system?  It is a single system unit, not dual boot.  I've given up XP as a bad habit and am trying to ween my wife off of it as well.
Thanks and sorry for the length of my query.

---

### Post by fredj on 2007-07-09
An i386 kernel should work on any processor including the Athlon. But leave kernel updates to
the update manager. You don't need to do anything. The update manager will always update to the
latest kernel that is suitable for you processor.

---

### Post by Kodfish on 2007-07-09
You won't get much out of switching kernels, i do not reccomend it on binary systems like Ubuntu. If you want to look around at the things the kernel can do, do a 
```
 sudo apt-get install linux-source-2.6.20 build-essential
cd /usr/src/linux
make menuconfig 
```
and then configuring things. I like to buil things into the kernel. [*] instead of [M]. exit, and save your changes.
```
 make && make modules_install
mount /boot
cp arch/{YOUR PROC TYPE HERE}/boot/bzImage /boot/kernel-linux-2.6.20-b{BUILD NUMBER}
gksu gedit /boot/grub/menu.lst 
```

then add ```

title Ubuntu Linux, Custom Compile [BUILD NUMBER]
root {LOOK @ OTHER KERNELS AND USE THE hd(#,#)}
kernel /kernel-linux-2.6.20-b[BUILD NUMBER] 
```


try rebooting and selecting it. it might not work, but hey. if it doesn't, thats how you learn.

---

### Post by jocko on 2007-07-09
The "correct" way to switch from the -386 kernel to a -k7 kernel:
First install the -k7 kernel:
```
sudo apt-get install linux-k7
```Or find the package "linux-k7" in synaptic and mark it for installation.
Then reboot into the new kernel before you try to remove the -386 kernel (but it's probably good to leave it installed for a while until you know everything works ok).
And if you use any restricted drivers from the repos, you'll want to install the correct linux-restricted-modules for the new kernel as well:
```
sudo apt-get install linux-restricted-modules-k7
```Note: From what I have read on these forums, you'll probably not notice any improved performance between the -k7 and -386 kernels. But if you have a dual cpu setup or dual core cpu you'll need to run a "-smp" kernel to make use of both processors/cores.

Note 2: For edgy and feisty, the name of the optimized kernel ends with "-generic" instead of "-k7", "-686" or "*-smp".

---

### Post by gottatrieit on 2007-07-09
Thank you guys for answering.
I guess I'll leave things alone, then.  Everything seems to be working fine, so I don't want to mess it up again ---(I've installed one or more Ubuntu flavors on this machine about once every 6-10 weeks for the last year 'cause I messed up!)

---

