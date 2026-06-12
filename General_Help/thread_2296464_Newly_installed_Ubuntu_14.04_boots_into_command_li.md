---
title: "Newly installed Ubuntu 14.04 boots into command line+no internet connection"
date: 2015-09-26
forum: General Help
---

### Post by dominick3 on 2015-09-26
Hey all, I am having a very frustrating issue with a newly installed version of 14.04. First off, I didn't get the newest version because it didn't support my graphics card, but 14.04 allows me to actually boot without an error message. I've read several threads on here about other users who had their install boot to command line, but none of them were helpful. 

I tried "startx", but X isn't even installed. Which seems like the major issues here, haha. I'm not very experienced in Ubuntu, so bear with me here. When I tried "sudo apt-get update", it couldn't resolve the host to the ubuntu servers. I tried numerous ways to get my wireless working, but I couldn't seem to find any manageable solutions. "ifconfig" shows that my wireless card is recognized, however. Also, I have no ethernet port on the comp because it is a netbook, so that is not an option. 

Any help would be appreciated.

---

### Post by ajgreeny on 2015-09-26
What did you actually use to install the OS and which version of Ubuntu was it; if you have no X installed, and I am not certain what you mean by that, or how you found out that fact, there is obviously something wrong with
[LIST=1]
[*]the .iso image file you used, or
[*]the install medium you made, DVD or USB, or
[*]it was the minimum install CD which installs command line only.
[/LIST]

What hardware do you have, particularly the graphic card?

---

### Post by dominick3 on 2015-09-26
I used Unetbootin to create the bootable flash drive, and I used the netboot mini .iso found here: [http://cdimage.ubuntu.com/netboot/trusty/](http://cdimage.ubuntu.com/netboot/trusty/) 

It is an  Amd a4-1250 apu with radeon hd graphics.

---

### Post by Bashing-om on 2015-09-26
dominick3; Hello;

If this is your 1st time installing 'buntu; you have jumped off the deep end choosing to install from minimal.
The Minimal install is only the kernel, what is required to boot that kernel, and a minimal WIRED networking capability. That is all. You are expected to know what you you want to install onto this bare bones.
You might - and I do say might - be better served to install a mainline system. However, if you choose the course of completing the install from minimal, well we can help but you will not be aware of all the amenities that are in the full release install.

[INDENT][INDENT][INDENT]choose wisely grasshopper
[/INDENT][/INDENT][/INDENT]

---

### Post by dominick3 on 2015-09-26
Thanks, I just got a bigger flash drive, so I'm going to attempt installing from the live boot this time. This isn't my first time installing Ubuntu, but I am not experienced enough to get things working just from the command line and kernel. Thanks for all the help.

---

### Post by Bashing-om on 2015-09-26
dominick3; Good 'nuff .

Let us know how it goes. We are here to help in whatever capacity that you require.
We await your install to mark this thread in a concluded manner.

[INDENT][INDENT]where there is a will there is a way[/INDENT][/INDENT]

---

