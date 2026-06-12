---
title: "Multiple Wubi installs"
date: 2008-07-04
forum: General Help
---

### Post by bob23450 on 2008-07-04
Is it possible to install more than one version of *ubuntu on the same windoze machine with Wubi?

I know this has been asked many times and the answers were always to install another desktop from whithin the first wubi install.

My question is however a little different: what I would like is to setup different and independent **versions**, not distributions, to choose from at boot.

 I'd like, for example, to try out the new version of Ubuntu while leaving untouched the one I work with.

Thanks in advance.

---

### Post by ago on 2008-07-04
Different ubuntu versions are available as normal packages.
So just install Ubuntu, then from there install the appropriate package such as kubuntu-desktop or xubuntu-desktop.

Then whe you LOG IN, under options, you can select the desktop environment

---

### Post by bob23450 on 2008-07-04
Sure. But what about having a separate environment to play (and possibly mess up) with say Ubuntu 8.10 while leaving my Ubuntu 8.04 clean? After all, if the entire os is contained in a few files under the host filesystem, one may think that more os could be hosted as well. If this is not currently possible, it would be a nice enhancement in future releases.
Thank you.

---

### Post by ago on 2008-07-04
It is possible but you have to do it manually. 

Create a copy of root.disk within the same folder, then add an entry to ubuntu/disks/boot/grub/menu.lst pointing to the newly created root.disk and comment out "hidemenu". Now you can dist-upgrade one of the two copies to 8.10.

---

### Post by bob23450 on 2008-07-04
Interesting... I'll try it out.
Many thanks!

---

### Post by studyhard888 on 2008-07-04
it sounds interesting.
but i ever installed ubuntu in xp with wubi,when i run the wubi to install another ubuntu ,a problem occored.
it asked whether uninstall the previous ubuntu or not.
anyone could solve it ?
thanks in advance

---

### Post by ago on 2008-07-04
The installer does not allow for multiple installations (it will ask to uninstall first if you run it again), so you can only run wubi.exe once. The above is a way to go around the issue. A similar trick is to install, rename the ubuntu folder, install again, then modify menu.lst.

---

### Post by phflupp on 2010-09-19
It seems these instructions no longer apply to Wubi since grub2 was deployed. Where can I edit the initial menu (Windows/Ubuntu choice) that appears before the kernel choice menu?

Thanks in advance for any suggestions!
-p.

---

### Post by bcbc on 2010-09-20
You can boot any root.disk that you copy from a grub command line. So you should be able to add a custom entry to your main wubi grub menu:

e.g. put this at the bottom of /etc/grub.d/40_custom 
menuentry "copied wubi" {
insmod ntfs
set root=(hdX,Y)
loopback loop0 /copiedubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sdMN loop=/copiedubuntu/disks/root.disk quiet splash
initrd /initrd.img
}

You can copy the entry from your current /boot/grub/grub.cfg (to get the right partition i.e. (hdX,Y) and /dev/sdMN; just change the linux and initrd to reference the link to the latest kernel, rather than specifying the kernel - then you don't have to update it later.

---

