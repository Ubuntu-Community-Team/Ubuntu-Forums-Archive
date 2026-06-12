---
title: "some questions about ViusalBox"
date: 2008-06-24
forum: General Help
---

### Post by dinbrca on 2008-06-24
i saw there is a software called visualbox and what it does:
enables you to use windows xp in ubuntu.. is that enables you all the features of windows xp?.. i saw i need the disk of windows xp too right? if i use it can i do full screen?
how much ram does it takes when working?
demo (if you guys dibt jbiw what is it):
[http://youtube.com/watch?v=ch8X86R6d-g](http://youtube.com/watch?v=ch8X86R6d-g)

---

### Post by danwood76 on 2008-06-24
Virtual box is good,
The RAM it uses depends on what you set for it, you have to realise that the RAM in your virtual machine will be shared with your system RAM.

Full screen is usually possible, only really not if you have a really poor graphics card.

You may want to try using Vmware server as I have found it to be a bit faster than virtualbox.

Also if your CPU supports it there is KVM (Kernel Virtual Machine) which is way way faster than the two previous methods mentioned.
See: [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

---

### Post by isecore on 2008-06-24
The software you're talking about is called Virtualbox. It's a free download and is owned by Sun since a few months back. Website is located at [http://www.virtualbox.org/](http://www.virtualbox.org/)

Think of it as a kind of virtual computer. It's software that creates a virtual computer that you can install any operating system into. Windows is one of them.

Yes, you will need the Windows-cd since it will be installed just like any other operating system into this virtual computer.

Yes, it can do full-screen just fine. I use it to work in Photoshop without having to reboot.

How much RAM it consumes depends on how much RAM you assign it to use when running a virtual machine. If you assign the virtual machine one gigabyte of RAM, then you will need to have that gigabyte + whatever your "real" machine uses. You can of course assign it less memory if you don't have huge amounts, but then the system running inside the virtual machine will run slower just as if you had a real computer with limited RAM.

One limit though is that it will not do accelerated 3D. That means no games inside the virtual machine. Everything that's 2D will however work just fine.

---

### Post by dinbrca on 2008-06-24
thanks guys.. now:
i would like to play 3d games.. and the guy that above me said i cant now.. is KVM supports 3d games? (because i entered the command:
egrep '(vmx|svm)' /proc/cpuinfo  -and it says i have it..) so if you guys can give me more information about KVM i will thank you..

---

### Post by isecore on 2008-06-24
> **dinbrca said:**
> thanks guys.. now:
i would like to play 3d games.. and the guy that above me said i cant now.. is KVM supports 3d games? (because i entered the command:
egrep '(vmx|svm)' /proc/cpuinfo  -and it says i have it..) so if you guys can give me more information about KVM i will thank you..

Nope, won't happen I'm afraid. To my knowledge there doesn't exist a virtualization solution that allows 3D-acceleration. That's one of the major limitations of this type of technology.

---

### Post by dinbrca on 2008-06-24
so the only thing that will allow me to play 3d games is dual booting? (and wine but it doesnt support a lot of things..)

---

### Post by danwood76 on 2008-06-24
Yes, that is how I play 3D games.
Dual booting is the only way.

---

### Post by RagingAardvark on 2008-06-24
Depending on the oomph of your machine, you could try Cedega.

---

### Post by dinbrca on 2008-06-24
cedega is only buy software.. i dont want to buy a software for playing..
danwood.. can i dual boot with xp.. then.. get into ubuntu and with a software use ubuntu and the windows xp i installed? i mean can i use my windows xp i installed inside ubuntu?

---

### Post by danwood76 on 2008-06-24
Probably not, its best to do a fresh install.

Cadega is a bit of a silly option, it is a rewrite of WINE and I bet the performance isnt as good as if you dual booted.

---

### Post by dinbrca on 2008-06-24
yea but you didnt realy answer my question.. can i use windows xp within ubuntu or everytime i want to play i will need to restart my pc.. boot windows xp and then play?

---

### Post by AndyCooll on 2008-06-24
> **dinbrca said:**
> yea but you didnt realy answer my question.. can i use windows xp within ubuntu or everytime i want to play i will need to restart my pc.. boot windows xp and then play?
Dual-booting means rebooting your pc each time you want to swap OS's.

You can have Windows XP in Virtualbox (and hence no reboot required) BUT you don't get 3-D within a virtualised XP.

:cool:

---

### Post by danwood76 on 2008-06-24
> **dinbrca said:**
> yea but you didnt realy answer my question.. can i use windows xp within ubuntu or everytime i want to play i will need to restart my pc.. boot windows xp and then play?

Sorry I mis-read what you said.

AndyCooll sums it up nicely.

---

