---
title: "Ubuntu 12.04.2 Update Manager updating two kernels - 3.2 and 3.5"
date: 2013-05-22
forum: General Help
---

### Post by maglinu on 2013-05-22
I have two machines on which I installed 12.04.2 from the iso (ie from the same cd burn of it)

The first only updates kernel 3.5

The second updates 3.5 and 3.2 - though uname -r only shows 3.5.

The first is a 32bit machine, the second is a 64bit machine (both running 32bit ubuntu).

Is this behaviour normal? Do I need to keep the 3.2 kernel on the 64bit machine?

Thanks

Dave

---

### Post by plucky on 2013-05-22
> Is this behaviour normal? Do I need to keep the 3.2 kernel on the 64bit machine?


That is because you still have both kernels installed and it will update both.

```
ls /boot
```

If you open Synaptic Package Manager and remove the 3.2 linux-images and headers,it should not try to update them again.

Good Luck

---

### Post by ibjsb4 on 2013-05-22
Both kernels are supported on 12o4, so you can choose which one to keep and which one to delete.

I use [synaptic package manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9") to [delete old/unwanted kernels]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager+delete+old+kernels&sa=Search&cof=FORID:9").

---

### Post by grahammechanical on 2013-05-22
When 12.04 was first released it had Linux kernel 3.2.0 series. When 12.10 came out it had Linux kernel 3.5.0 series. You have a point release of 12.04, the .2 release in fact. The purpose of these point releases is to keep the 12.04 Long Term Support release up to date with the Latest Linux kernel support for newer hardware. That is why 12.04.2 has Linux kernel 3.5.0 series.

I do not know how the 3.2.0 kernel got on that machine but as it is still supported by Linux developers it will be updated. How many 3.5.0 kernels do you have? If you have more than two 3.5.0 kernels and they both load without problems then you can remove all the older kernels using Synaptic Package Manager. It is sensible to have at least two working kernels then if something (like a video driver update) were to break the desktop then you could use Grub to load the previous kernel. I think that 12.04.2 also has the Grub 2.0 version so you will find all your previous kernels in the Advance Options for Ubuntu sub-menu.

Regards.

---

### Post by maglinu on 2013-05-22
Thanks for the replies.

What I can't understand is how the 3.2 kernel got onto the 64bit machine.

I guess it's possible that I actually installed from a 12.04.1 iso by mistake, but then can't understand how the 3.5 kernel got onto the machine.

Here are the kernels I have installed.

```
abi-3.2.0-41-generic-pae         initrd.img-3.5.0-28-generic
abi-3.2.0-43-generic-pae         initrd.img-3.5.0-30-generic
abi-3.5.0-23-generic             memtest86+.bin
abi-3.5.0-28-generic             memtest86+_multiboot.bin
abi-3.5.0-30-generic             System.map-3.2.0-41-generic-pae
config-3.2.0-41-generic-pae      System.map-3.2.0-43-generic-pae
config-3.2.0-43-generic-pae      System.map-3.5.0-23-generic
config-3.5.0-23-generic          System.map-3.5.0-28-generic
config-3.5.0-28-generic          System.map-3.5.0-30-generic
config-3.5.0-30-generic          vmlinuz-3.2.0-41-generic-pae
grub                             vmlinuz-3.2.0-43-generic-pae
initrd.img-3.2.0-41-generic-pae  vmlinuz-3.5.0-23-generic
initrd.img-3.2.0-43-generic-pae  vmlinuz-3.5.0-28-generic
initrd.img-3.5.0-23-generic      vmlinuz-3.5.0-30-generic
```

Sounds like I can safely remove the 3.2s and 3.5.0.23.

---

### Post by ibjsb4 on 2013-05-23
> Sounds like I can safely remove the 3.2s and 3.5.0.23

Yep, sounds like a plan :)

---

### Post by maglinu on 2013-05-27
Removing the 3.2s has solved the problem.

Still don't know why the original 12.04.2 install put two kernels (3.2 and 3.5) on the machine (both are part of the 12.0.4.2 iso though).

Possibly something to do with a feature of my hardware that triggered that action by the installer? The fact that I am installing 32bit ubuntu on a 64bit processor machine may have played some part.

Thanks to all

Dave

---

### Post by ibjsb4 on 2013-05-27
> The fact that I am installing 32bit ubuntu on a 64bit processor machine may have played some part.

Nope, thats the same setup I have and the 3.5 kernel is not installed.  My install CD (mini.iso) is the first one out (12.04.00).

The 3.8 kernel is now in the repositories :)

 [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

