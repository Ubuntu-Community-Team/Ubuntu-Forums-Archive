---
title: "Changing /boot to be mounted on a different partition?"
date: 2007-06-01
forum: General Help
---

### Post by x1a4 on 2007-06-01
Hi,

I recently said 'goodbye' to windows by removing all windows partitions.  Unfortunately, a lightning strike in the area caused a short blackout and my Xubuntu rebooted before I could update GRUB and the MBR.  

I got things up and running using my Edgy LiveCD but not quite as I would have liked to.  So, here's the situation.  

(hd0) contains the MBR.  (hd0,0) is a 2G partition which I want mounted as /boot/.  Currently it contains the /boot/ directory with grub/ in it.  Kernels are in /boot/ on (hd1,0) and symlinked in / on (hd1,0).  

Here's what I *think* I should do to get /boot/ to be mounted on (hd0,0): 

Move kernels to (hd0,0)
Symlink them to (hd0,0)
modify _/etc/fstab_ to mount (hd0,0) on /boot/

Is this correct?  What else (if anything) do I have to do? 

Thank you.

---

### Post by Rescue9 on 2007-06-03
I'm glad this came up. Like you, I'm dumping another OS, but mine happens to be Gentoo. 

I tried baking a boot partition and copying all the information over, but it crapped out my system completely. I had to use the liveCD to copy back the information.

I think it may have to do with using grub vs grub-install. but I'm not entirely sure. 

I'll be following this thread for sure.

---

### Post by gimfred on 2007-07-01
WOW! now there are three of us! my situation is:

Installed Kubuntu with multiple partitions
```
   /                      |---------------hda5
   swap                |---------------hda2
   /boot/               |---------------hda1
   /home/             |---------------hda6
   /usr/                |---------------hdb5
   /usr/local          |---------------hdb6
   /var/                |----------------hda7
   /opt/                |----------------hda9 (could be 8)
   /temp/              |---------------hda8 (could be 9)
   /scratch            |---------------hdd1 (where I keep all my data; it is a 114gb drive and a   
                                                    left-over from using MS Windows dual-booted with 
                                                    Suse several years ago.)
```

Because I have a huge HD (hda), I then installed Kubuntu 64 to try it out on:

```
/                      |----------------hda10
```

as a single partition. It quickly became my main system. I now want to change the /boot of the 64 bit Kubuntu to the 32 bit Kubuntu /boot/ (hda1). I believe it can be done via softlinks but unsure. My grub is:
```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=95b92bb0-a641-4eb5-8561-f19c816b6ee9 ro quiet splash
initrd		/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-generic root=UUID=95b92bb0-a641-4eb5-8561-f19c816b6ee9 ro single
initrd		/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-9-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-9-generic root=UUID=95b92bb0-a641-4eb5-8561-f19c816b6ee9 ro quiet splash
initrd		/initrd.img-2.6.20-9-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-9-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-9-generic root=UUID=95b92bb0-a641-4eb5-8561-f19c816b6ee9 ro single
initrd		/initrd.img-2.6.20-9-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

title		Ubuntu, kernel 2.6.20-9-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-9-generic root=UUID=95b92bb0-a641-4eb5-8561-f19c816b6ee9 ro single
initrd		/initrd.img-2.6.20-9-generic

title		Ubuntu64, kernel 2.6.20-16-generic
root		(hd0,9)
kernel	        /boot/vmlinuz-2.6.20-16-generic root=UUID=2ead6ea1-4de5-4997-83dd-54a02115f7ba ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
# kernel	/boot/vmlinuz-2.6.20-16-generic root=UUID=2ead6ea1-4de5-4997-83dd-54a02115f7ba ro quiet splash

title		Ubuntu64, kernel 2.6.20-15-generic
root		(hd0,9)
kernel	/boot/vmlinuz-2.6.20-15-generic root=UUID=2ead6ea1-4de5-4997-83dd-54a02115f7ba ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
```

Yes, I could easily make the Ubuntu64 the default, but when the kernel is updated i have to fix it manually. Not a huge problem, I even enjoy doing it. It isn't good system management though.

---

