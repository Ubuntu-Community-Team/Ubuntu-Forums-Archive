---
title: "edgy shutdown freez"
date: 2006-10-31
forum: General Help
---

### Post by hardkaare on 2006-10-31
Hi

sometimes when I restart edgy i get this colorfull screen:
[IMG]http://kaare.baastrup.org/colorfull.jpg[/IMG]

My spec's are as following:

Centrino duo core 2 2.0Ghz

nvidia go 7600 512 mb

Linux 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux
nvidia-glx, restricted-modules. installed

---

### Post by David Corrales on 2006-10-31
Space invaders anyone?
Looks like you're having a problem with the driver maybe?
Why don't you switch the driver in /etc/X11/xorg.conf, from **nvidia** to **nv** and do some testing. If you stop getting the galaga attack, then you can try with another Nvidia driver.

---

### Post by hardkaare on 2006-11-20
Looks like the nv, driver works.
hmm found out that i could provoke a crash doing ctrl+alt F2 console thing.

I have a few questions:

Will the new nvidia driver, be available in u buntu 6.10?
what do modules do I need in xorg, dri, glx? when using nv drivers?
is there any way to stress test the graphic card under linux without buying quake4/doom3.

Thx for the help.

---

### Post by der_joachim on 2006-11-20
The new NVidia driver is available. There is a HOWTO for installing it in the HOWTO subforum.

---

### Post by hardkaare on 2006-11-20
oki I tryed with nvidia version 1.0-9629

same problem, hmm maybe its a hardware error, but how do I convence the company that there is som kind of error with this laptop. in windows it only crash sometimes when playing games.
no crash with nv, as far as i have seen, maybe it has something to do with glx?
hmmm

---

### Post by _Mo on 2006-12-17
I've got the same problem as you. And I have the same graphic card (I also have a Zapto laptop). Did you find out how to solve this problem? Or can anyone else help?

---

### Post by hardkaare on 2006-12-18
I have e-mailed zepto and asked them for a new bios upgrade.
still wating on reply.

I still need to test a newer kernel, like 2.6.19 and see what happens.
I have tried a lot of different  nvidia drivers without luck.
så et must be the bios firmware or the kernel.

if you find anything plese let me know,

---

### Post by _Mo on 2006-12-18
Hm... I thought about trying Feisty or another linux distribution. But I'm a bit busy at the moment. Maybe later I'll try this. 
If you have time, you can try to run Feisty (or another distro) in a virtual machine (VMWare, QEMU, ...).

---

### Post by hardkaare on 2006-12-18
Hehe time is my problem too.

I have been trying the new bios udate 1.0.9v. witch include vga bios updates.
I dident help though.

So we have to try wirh a never kernel until the next bios update come out.

running tests from an emulator wont tell os anything, course, the emulator emulates the graphic card.

maybe we are able to boot from the new ubuntu unstable livecd.

good luck.

Best regards.
Kaare

---

### Post by _Mo on 2006-12-24
A friend of mine told me, that this problem could appear because of the frambuffer... Try "sudo rmmod vesafb" before shutting down. This might help for the moment. 
I'm trying to find out more about the framebuffer. You cold do so, too ;). Merry christmas!

---

### Post by hardkaare on 2006-12-24
Hmm maybe you'r right about the frame bufer when we reboot, but I also have problems when going to a console like ctrl+alt F1, if I go back and forth between x and a console the machine freezes.

so I still thing it has something to do with the kernel or the nvidia drivers

Merry christmas to you too :-)

---

### Post by _Mo on 2007-01-07
The problem seems to be solved with a newer kernel. I compiled a 2.7.19-kernel by myself and there I can switch between the tty's as many times as I want. I just have to get wireless working in this kernel and then everything's perfect :). 
Just have a look at the Master Kernel-Thread in this forums, there's a good explanation howto compile a kernel.

---

### Post by hardkaare on 2007-01-10
Sovled with feisty, everything works for me too :-)

so it must have been a kernel probelm

---

