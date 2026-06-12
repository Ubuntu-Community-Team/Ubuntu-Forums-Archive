---
title: "Gray, distorted boot screen and freeze on GDM with Edgy"
date: 2007-01-02
forum: General Help
---

### Post by bsharitt on 2007-01-02
First of all, Dapper worked fine, and I can use Edgy just fine if I use my old Dapper kernel(2.6.15-23-amd64-generic). This error occurred after I upgraded to Edgy, and when trying to use the Edgy LiveCD. I can install Edgy with the alternate install CD, but have the same problem when I finally boot the OS. 

The problem is this:

1. When booting the old brown(or at least it was in Dapper) boot screen is gray scale and badly distorted.

2. When it does boot and reach the gdm login screen, it just freezes.

3. The gdm load notification drumbeat gets caught in some sort of infinite loop that keeps going, even after gdm is killed. 

After switching to a terminal and killing gdm, I can login in and X session with the startx command, though that looping drum beat is still there.

I compiled and installed a vanilla kernel(2.6.19.1) using the .config file from the 2.6.15-23-amd64-generic kernel, but the result is the same as the Edgy 2.6.17-10-generic kernel.

Hardware wise I'm using a Sempron 2800+ system with an ATI Radeon Xpress 1100 chipset with and unused X200 integrated video card. I'm using a PCIe x16 Radeon x1300 video card, and I also have a PCI firewire card installed. 

If you have any ideas, or need any more information, please let me know.

Thanks.

---

### Post by bsharitt on 2007-01-03
I've also tried recompiling the the latest Ubuntu kernel (2.6.17 I belive)

---

### Post by bsharitt on 2007-01-03
Well it seems the gray boot screen is completely boot screen is completely unrelated to my real problem, and is just a bug with a simple fix that the Ubuntu developers are choosing to ignore.

Any way, there's still the problem with Gnome freezing at login. Any ideas or thoughts?

---

### Post by tommyhot on 2007-02-02
I have exactly the same problem, with the gray boot screen and with the gdm login. It just freeze and I can't even restart X server using Ctrl+Alt+Backspace.

I bought new PC and couldn't even Install ubuntu. I had 1.5GB RAM (1GB+512MB) which both of them were broken so I got 512MB for some period of time and I could install it and use it. Today I replaced the one piece of 512MB RAM with new 1.5GB and again it freezes right after it reaches the gdm login screen. 

I'm pretty sure my hardware is working correctly as it was tested and reported no errors. And my windowsXP works fine.

I'm using Ubuntu Edgy Eft 64bit desktop, with the latest kernel. Is there any issue in Ubuntu with RAM higher than 1GB? My Dapper (Ubuntu and Kubuntu) also freezes, I can instal SUSE 10.1 but it doesn't start and my old knoppix boots just fine. I have beryl installed and replaced my NVidia driver so my xorg.conf is not the default one - could this be the problem too?

---

