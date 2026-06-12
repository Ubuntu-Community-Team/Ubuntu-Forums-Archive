---
title: "Ubuntu install used on 2 different pcs"
date: 2007-05-25
forum: General Help
---

### Post by Mykle87 on 2007-05-25
I have feisty fawn installed on an external hard drive. I am getting frustrated running it on my desktop w/ an x850xt but I am not ready to give up on Ubuntu yet! I also have a Dell Latitude D620 and knowing that the intel graphics card plays nicely with Ubuntu I bet I will have a much better experience. Is there a way that I can make a new session for my laptop or would I be better off just reinstalling feisty?

---

### Post by Happy_Man on 2007-05-25
You could copy your /home, and stick on another partition on your laptop.. and then install Ubuntu and set it so that it recognizes the partition as /home....

---

### Post by Mykle87 on 2007-05-25
Well, I want to keep Ubuntu completely independant on my external hard drive. The only thing is I have 2 different computers I want to use it on. Also, it will allow me to run it on any x86 computer.

---

### Post by Pisi-Deff on 2007-05-25
That is doable... You'll simply have to install GRUB on both PC's and create entries, which point to the ubuntu hard drive

---

### Post by Mykle87 on 2007-05-25
Ok I'd rather not install GRUB to the Windows MBR. Can't I just create different sessions with the appropriate drivers installed?

---

### Post by Happy_Man on 2007-05-25
Nope, otherwise Ubuntu won't boot.

---

### Post by m.musashi on 2007-05-25
> **Mykle87 said:**
> Ok I'd rather not install GRUB to the Windows MBR. Can't I just create different sessions with the appropriate drivers installed?

Installing grub to the mbr is not all that scary and it's easily reversed if you have have a windows install disk. 

However, I'm pretty sure most newer laptops will boot off a usb drive. You could modify the bios to boot usb first. If there is no drive present it will boot the internal HD. If there is a usb drive, with a bootable os, it will boot that.

That being said, getting a working install on a usb drive could be a bit of trick. I've not personally tried it but I've seen some threads that lead me to believe it is not a straight forward process. Of course, you'll never know if you don't try.

I can also foresee at least one other potential problem. If you install with one set of hardware (i.e. the computer it's connected to) and the try and boot a different set of hardware you could run into problems - particularly if you use proprietary drivers.

Let us know how it goes.

---

