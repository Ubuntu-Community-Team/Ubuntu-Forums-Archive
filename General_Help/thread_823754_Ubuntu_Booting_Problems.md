---
title: "Ubuntu Booting Problems"
date: 2008-06-09
forum: General Help
---

### Post by WeEatVista on 2008-06-09
Today I did a clean install of ubuntu 8.04 using a Live CD burnt today. Ubuntu works perfectly so far, but there is one thing that gets annoying. When I boot ubuntu, after the ubuntu symbol appears and the orange bar loads, it goes into this black screen which says:

Loading files needed to boot                       [OK]
Setting preliminary keymap                         [OK]
Preparing restricted drivers                       [OK]

and this list keeps going. Although this doesn't affect ubuntu, I'd rather have this cleaned up so it loads like a regular OS. (Loads grub, ubuntu symbol and orange bar, then ubuntu loads up) I don't like watching this script. Plus, it makes my boot 10 minutes. That's a little long, almost as long as my vista boot =D So, how can i remove this?

Thanks in advance,

WE Eat Vista

---

### Post by VMC on 2008-06-09
> **WeEatVista said:**
> Today I did a clean install of ubuntu 8.04 using a Live CD burnt today. Ubuntu works perfectly so far, but there is one thing that gets annoying. When I boot ubuntu, after the ubuntu symbol appears and the orange bar loads, it goes into this black screen which says:

Loading files needed to boot                       [OK]
Setting preliminary keymap                         [OK]
Preparing restricted drivers                       [OK]

and this list keeps going. Although this doesn't affect ubuntu, I'd rather have this cleaned up so it loads like a regular OS. (Loads grub, ubuntu symbol and orange bar, then ubuntu loads up) I don't like watching this script. Plus, it makes my boot 10 minutes. That's a little long, almost as long as my vista boot =D So, how can i remove this?

Thanks in advance,

WE Eat Vista

sudo gedit /boot/grub

look for something like below. Its near the bottom:
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d8533154-cef1-4cce-a823-9f3f74aab65b ro splash vga=773
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

On the end of the line that staarts with kernel add quiet splash, like so
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d8533154-cef1-4cce-a823-9f3f74aab65b ro quiet splash

But that won't kelp speed up your 10 minute boot time. Something else is happening. It only takes my system to boot in under 1 minute WITH the splash and text.

---

