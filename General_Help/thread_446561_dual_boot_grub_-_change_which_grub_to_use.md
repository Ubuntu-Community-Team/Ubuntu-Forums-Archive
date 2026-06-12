---
title: "dual boot grub - change which grub to use"
date: 2007-05-17
forum: General Help
---

### Post by falkenberg_cph on 2007-05-17
Hi
I'm sure this question has been asked before. but i searched i didnt find nothing.

I have Ubuntu and OpenSuse installed. Unfortunately i installed OpenSuse later, so it is now the GRUB menu installed with that, that is being used.

How do i tell the computer to use the GRUB menu of Ubuntu?

I have installed UbuntuStudio and need to boot with a special low-latency kernel. I realize that i could just create the option in the OpenSuse GRUB menu, but i would prefer to use the Ubuntu Menu.

Thanks
Carsten

---

### Post by falkenberg_cph on 2007-05-17
Well i found out a little more, and i am now trying to reinstall grub from ubuntu.
My problem is that the first step is giving me an error.

Im doing this from terminal:
> 
grub

find /boot/grub/stage1
Error 15: file not found


Looked in the folder - it is there, and also there is a stage2
Whats going on

/Carsten

---

### Post by NIKOSHIBA on 2007-05-17
when you installed suse, didn't it show in grub during boot that you have ubuntu installed?

if no, in suse:

```
kdesu kwrite /boot/grub/menu.lst
```
it will open text editor with your grub menu
then go to ubuntu folder (considering that you have mounted it already). and go to /boot/grub and open menu.lst in text editor. copy lines that should look as following:
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4eb078ed-acda-4717-90a3-4450f6357d7f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

```

and paste it in suse grub.
if you want to boot to ubuntu first then paste it before suse entry, if not at the end.
and anyway no matter where you paste you can always scroll to distro you want to boot during start up in grub.

sorry for bad english

---

### Post by falkenberg_cph on 2007-05-17
Yes, OpenSuse Grub was showing ubuntu, and i could start ubuntu from the menu. The problem was that i wanted to use the menu.lst installed with ubuntu not OpenSuse.

Anyway, since i wasnt really using opensuse that much, i decided to reinstall ubuntu on top of it. That way i will have a normal ubuntu and an ubuntustudio partition.

So i guess, for my part, the problem is over
Thanks
Carsten

---

