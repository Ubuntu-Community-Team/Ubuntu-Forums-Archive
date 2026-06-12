---
title: "linux-kernel-2.6.24.18-virtual: no mouse and no keyboard"
date: 2008-06-07
forum: General Help
---

### Post by knutschr on 2008-06-07
I want to run opengeu in Virtualbox.
When I try to configure it, it says I have to activate some moduls in the kernel.
I searched in Synaptic, and installed the virtual things.
When I restarted, linux-kernel...virtual was listed first.
When I start that, I can't log in, as neither my mouse nor keyboard respond.
This is so in recovery mode, too :-)

Kernel ......-rt works fine, (but can't start Virtualbox.

Anyone knows how to fix this?

---

### Post by Vivaldi Gloria on 2008-06-07
> **knutschr said:**
> 
I searched in Synaptic, and installed the virtual things.
When I restarted, linux-kernel...virtual was listed first.
When I start that, I can't log in, as neither my mouse nor keyboard respond.
This is so in recovery mode, too :-)


Virtualbox doesn't need anything extra installed. So whatever you installed has nothing to do with virtualbox. It seems that you installed some linux kernel. 

I am assuming that the latest kernel in your box is 2.6.24-18-generic. First during boot press Esc to reach the grub menu then select 2.6.24-18-generic to boot (or whatever the highest numbered generic kernel is). Now it should start with all your hardware working. If not then do NOT continue below instructions. 

We will make the changes in the grub menu so that evertime 2.6.24-18-generic is chosen automatically. So backup menu.lst first:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

Now 

```
sudo gedit /boot/grub/menu.lst
```

We are interested in those group of lines at the very end after

```
 ## ## End Default Options ##
```

If a line has a # at the front of it, then GRUB ignores it. Put a # before everything (after ## ## End Default Options ##) EXCEPT the following lines

```
title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd*,*)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID= *** blah blah blah
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd*,*)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID= *** blah blah blah
initrd		/boot/initrd.img-2.6.24-18-generic
```

So keep those lines as is and put a # before other kernel versions. Now save and reboot. It should start fine. Let me know.

---

### Post by knutschr on 2008-06-07
Thanks for your answer!
I saw in Synaptic that they have not included .....18 virtual modules yet.
I installed the ones for kernel....17, restarted using that kernel, and it works :-)

---

