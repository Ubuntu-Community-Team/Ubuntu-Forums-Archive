---
title: "Is it possible to disable X-server, by default?"
date: 2008-06-02
forum: General Help
---

### Post by ruipedroca on 2008-06-02
Hi,

I'm running a virtual kubuntu 7.10 machine and i'm very satisfied.

My question is:
Is it possible to disable X-server, by default?

I mean, is it possible to program kubuntu so when it starts it doesn't start X, but instead just to terminal. 
Then, if needed one could start manually X-server.
This would be useful for saving resources that X normally wastes.
And when we have more than one virtual machine, savings become necessary.

I need X server because i need it to install and configure initially all the applications.

Regards

---

### Post by SirPerigrin on 2008-06-02
I had to do a lot of digging as debian is a bit odd in this respect but you can add init=1 to your kernel boot parameters to specify runlevel 1

Ubuntu/Debian specify 
runlevel 1 as text
runlevel 2-5 as multi-user X

to add this open /boot/grub/menu.lst

then, using my personal entry as an example, add the line as such

> title		Ubuntu 8.04 Hardy Heron
root		(hdx,x)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6132141c-6732-4bcd-bed0-b2e74236c4bd ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet


> title		Ubuntu 8.04 Hardy Heron
root		(hdx,x)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6132141c-6732-4bcd-bed0-b2e74236c4bd ro quiet **init=1**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

---

### Post by aysiu on 2008-06-02
```
sudo apt-get remove kdm
``` is another way to do it. Then type ```
startx
``` if you want to start the X server.

---

### Post by ruipedroca on 2008-06-03
Thanks!

I'm going to try both methods and then post feedback.

Regards

---

