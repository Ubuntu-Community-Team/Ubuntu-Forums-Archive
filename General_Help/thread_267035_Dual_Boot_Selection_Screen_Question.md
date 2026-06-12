---
title: "Dual Boot Selection Screen Question"
date: 2006-09-28
forum: General Help
---

### Post by laklive on 2006-09-28
I currently dual boot Windows XP and Ubuntu on my laptop. Since installing Ubuntu for the first time, there have been a couple of udpates that I have installed. Per every update installed so far, my dual boot screen has cluttered with multiple "Ubuntu kernel 2.6.15-27-386" and "Ubuntu kernel 2.6.15-27-386 (recovery mode)" entry selections. So if I need to boot windows, I have a long way to scroll down. I'm sure there's a way to edit this screen so I only have ubuntu and windows xp entries. Can anyone help??

Also, how do I edit my boot order so windows is the default OS? I'm still in the learning process for Ubuntu so I still tend to use windows on a regular basis.

---

### Post by Tomosaur on 2006-09-28
You can do this by editing the following file:

/boot/grub/menu.lst

You will need super user priveleges. Altering the actual order of the boot menu is needless, since you can just set the default selection to whatever you like anyway. However, you can swap the boot menu order if you so wish, it's just a matter of copying and pasting some of the lines near the bottom of the menu.lst file. 

If you decide to just set Windows to be pre-selected on bootup, you must change the 'default 0' line to reflect your choice. Grub counts from zero, so the first menu item is seen as 0, second as 1 etc etc. The little 'Other Operating Systems' divider DOES count as a menu item, so remember to take it into account.

Alternatively, the script in my sig will allow you to change most of the common grub settings, such as default selection etc. If you don't feel comfortable editing the /boot/grub/menu.lst file by yourself, you may want to give it a try.

---

### Post by tommcd on 2006-09-28
Here is a comprehensive tutorial on grub for ubuntu:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
For changing the default OS that boots:
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

All you would ever want to know!

---

### Post by d_xtremw on 2008-02-01
is there any way to change it so that there is no count down or u get infinite time to pick??

---

### Post by Gutz on 2008-06-03
> **d_xtremw said:**
> is there any way to change it so that there is no count down or u get infinite time to pick??

You can do it by setting timeout to -1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		-1

Regards

---

