---
title: "Strange OS issue"
date: 2008-03-18
forum: General Help
---

### Post by coninsan on 2008-03-18
Hi 

recently i installed some updates after installing my sounddriver, the sound works but the strange thing came after i rebooted. 

normally when i enter the Grub menu, there is 4 types of OS's that i can chose from, Unbutu, Ubuntu failsafe, memorytest and WinXP. 
But after the updates and whatever it brought with it, the is 12 options...ubuntu server, ubuntu rt, ubuntu 386 and ubuntu umc, plus a recovery mode for each of them have been added. How come?

i have no idea how they got there, and i would to get them to go away, i tried some of them and they do not work right.
So please, do anyone know how to remove those entries, either in grub or anywhere else it would be of great help :razz:

---

### Post by bodhi.zazen on 2008-03-18
Don't know how it happened, but you can edit /boot/grub/menu.lst and delete or edit out options you do not want.

```
gksu gedit /boot/grub/menu.lst
```

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by coninsan on 2008-03-18
Is this a first timer or what?

---

### Post by coninsan on 2008-03-18
So if i wanted to remove the ubuntu rt (recoverymode) entry i would just delete:

```
title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=24412e94-b4cc-49ba-9a2d-137df34206b5 ro single
initrd		/boot/initrd.img-2.6.22-14-rt

```
?

just to be sure so i dont mess something up :)

---

### Post by bodhi.zazen on 2008-03-18
Yes, but with config files best to comment them out.

Normally everything after a # = comments. Grub is the only exception I know of, gurb uses two ##

so :

```
## title		Ubuntu 7.10, kernel 2.6.22-14-rt (recovery mode)
## root		(hd0,2)
## kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=24412e94-b4cc-49ba-9a2d-137df34206b5 ro ## single
## initrd		/boot/initrd.img-2.6.22-14-rt
```

---

### Post by forrestcupp on 2008-03-18
Make sure you want to delete them first.  The rt kernel is a real-time kernel.  It sounds like you may have installed Ubuntu Studio or something.

It's probably ok to delete some of the recovery modes, but I'd leave the one for the generic kernel if I were you.

---

### Post by kaurman on 2008-03-18
I think you should remove the kernels you do not need instead of deleting them from menu.lst.

Why? Because deleting the lines from menu.lst just removes the lines from the boot up options menu but the packages remain installed & take up space. If you remove the packages (with synaptic or apt-get) the system will modify menu.lst for you.

I think that in synaptic the search keyword would be 'linux-image' but make sure you know what exactly you remove. 

AFAIK the system warns you when you are trying to remove a kernel from which it is currently working so nothing bad shouldn't happen...

---

