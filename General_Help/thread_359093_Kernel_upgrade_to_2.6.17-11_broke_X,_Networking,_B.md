---
title: "Kernel upgrade to 2.6.17-11 broke X, Networking, Beryl"
date: 2007-02-11
forum: General Help
---

### Post by elcasey on 2007-02-11
I unwittingly installed the kernel upgrade and rebooted to find myself with a broken X server. I attempted to reinstall the Nvidia driver in a TTY in -11 only to find that my networking also didn't work. 

I was able to install the [FONT="Courier New"]nvidia-glx[/FONT] driver from the Ubuntu repositories and, while X works fine in both -10 and -11 now, Beryl refuses to start (and I need my transparency - metacity doesn't cut it) and I still have no network access in -11.

After doing an [FONT="Courier New"]lsmod[/FONT] to log files in both -10 and -11 and comparing them, I discovered that -11 kernel is not loading the "rt61" module that drives my Gigabyte PCI wifi card, which has a Ralink RT61 chipset.

I booted to -11 and tried [FONT="Courier New"]modprobe rt61[/FONT] but I received a "FATAL: module not found" error.

I considered re-installing Beryl via the Automatic Install script, which would reinstall the stable beta Nvidia drivers, which successfully ran Beryl for me before the -11 upgrade broke everything. But I would also like to get everything running properly, including Beryl, on the 2.6.17-11 kernel...

And I just don't know how to do that. HELP! :-s

---

### Post by elcasey on 2007-02-11
I reinstalled the binary Nvidia drivers from Nvidia's website and now Beryl runs again. I'm still getting weird issues, however, like windows whiting or blacking out until I minimize and reopen them (and yes, Rendering Path is set to Copy).

I still need to get my network card working in 2.6.17-11.

*BUMP*

---

### Post by elcasey on 2007-02-12
Got everything working again...thanks for all the great feedback. :-k

---

### Post by jgeewax on 2007-02-14
I have just resorted to hitting ESC in GRUB and booting the -10 kernel. I'm sick of kernel upgrades breaking just about everything. 

Can anyone give a full summary of what is broken by -11, and if so, a fix for the stuff -- namely the Beryl stuff?

Inside -11 Beryl will not start, and I just don't have nearly enough time to fiddle with this stuff!

---

### Post by kenden on 2007-02-18
To solve the "X not booting" problem, do the following:

sudo apt-get install linux-restricted-modules-2.6.17-11-generic 

Or see the thread:
[http://ubuntuforums.org/showthread.php?p=2174047#post2174047](http://ubuntuforums.org/showthread.php?p=2174047#post2174047)
for more solutions

Hope this helps,
kenden

---

