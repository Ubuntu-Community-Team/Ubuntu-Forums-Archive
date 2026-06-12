---
title: "Monitor Stanby After Reboot [Nvidia Problem]"
date: 2007-06-15
forum: General Help
---

### Post by J.One on 2007-06-15
Hi everyone! I'm new and sick 'n tired of "Billy" and his....programs...
Ubuntu Linux is perfect and i will stick for sure.For that, i need your help.
My Pc is AMD64 1024 Ram and 6600gt XFX graphics card.I also have instaled Ubuntu 7.04 for AMDx64.All went perfect till the time i decided to install compiz (because i heard that beryl is unstable) and for that i need to enable nvidia driver or install it in every way.
First things first, i trusted to istall the nvidia driver from System > preferences > Desktop Effects 
and of course enable the driver.All went ok till restart.Ubuntu loads good and before login screen monitor stands by.I hear sounds and everything wich that means it loads ok.
I forced to install over and over ubuntu, about 4 times so far because i can't find a way hot to fix it from the "safe mode" wich is dos like...
After a clean install i tried drivers from nvidia site, the x64 ones of course and when i type

sh NVIDIA-Linux-x86_64-100.14.09-pkg2.run

on terminal of course nothing happend.

I tried another command that i have read and i don't remember now and it extract it just fine but after that i didn't knew what to do to enable it because extrcting wasn't the only way.
Please help because i can't find the right forums and the speciefic user problems...

Greeds!

---

### Post by Cappy on 2007-06-15
On GRUB you can boot to (recovery mode) to fix this kind of problem. When using (recovery mode) use commands **without** "sudo" on the front or else it won't work.

First off,
```
sudo nano /boot/grub/menu.lst
```

Scroll down past all the lines beginning with "#" and "##".

You'll see something like this:
```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=Longnumber ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=Longnumber ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=Longnumber ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=Longnumber ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

```

Take out the words that say "splash". If you added a "VGA=whatever" line take it out too.
It should look like this:
```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=Longnumber ro quiet
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=Longnumber ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=Longnumber ro quiet
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=Longnumber ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

```

Once you are done making the changes use Control + O to save it. Then use Control + X to exit nano.

DO NOT COPY AND PASTE ANY LINE FROM THIS POST; ONLY REMOVE THE WORD "splash".

```
reboot
```
will reboot your computer

---

### Post by J.One on 2007-06-15
Thank you very much it is very helpfull but now pc is on fresh install state withought nvidia drivers.Can you please help me to find the right drivers install them correctly withought monitor standby on startup?
i would be gratefull!

---

### Post by Cappy on 2007-06-15
It isn't a problem with the drivers. You need to go ahead and follow those instructions.
After you do that, install the nvidia drivers from Desktop Effects like you did before and reboot.

---

### Post by J.One on 2007-06-15
When i do what you say on first post i take a "Error writing boot/grub/menu.lst : Permision denied

I don't have the rights to save? How do i get those rights?

Thank you very much

---

### Post by Cappy on 2007-06-15
```

sudo nano /boot/grub/menu.lst
```

You didn't use "sudo" on the front.

---

