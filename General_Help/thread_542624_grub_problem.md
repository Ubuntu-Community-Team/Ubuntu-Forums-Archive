---
title: "grub problem"
date: 2007-09-04
forum: General Help
---

### Post by ndihmo on 2007-09-04
Hi to all.
I'm having a problem with my laptop. I have 3 partitions.
sda1 is a ext1
sda2 is a ntfs
sda3 is a swap

I installed fist the ubuntu 7.04 then after some time i installed win xp.
Now I'm having problems reinstalling grub.

I followed a thread:
used the liveCD of ubuntu 7.04, on a terminal i did this things:
sudo grub
grub> find /boot/grub/stage1     //the result was:
(hd0,0)    // so i did:
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

after i restared my laptop i still have a problem now:
ERROR 17: CANNOT MOUNT THE SELECTED PARTITION.

PLEASE HELP.

Thank you.

---

### Post by Paul Sypien on 2007-09-04
um, i had a similiar grub error when i partitioned a drive, then decided i didnt want it partitioned and unpartitioned it, the computer wouldnt start up it just said "grub error", i tried to do  ALLLOT of things, such as live cds and stuff, but i wasnt able to find anything other then just simple completely rebooting the whole damn thing (which sucks cuz u loose everything), but hopefully you have some backups... good luck

Paul

---

### Post by agemon on 2007-09-04
well.. you could do what Paul said, but personally, i prefer fixing the problem :). And to tell you the truth, yesterday i deleted one of my windows partitions and then my boot one, of course that totally messed up grub and my fstab, i got it working again.. though it did took me half a day :D

anyway, here's what i think you should do. Make a backup copy of /boot/grub then delete everything that is in /boot/grub. This will make it easyer for you to see what has been installed.

then, run sudo grub-install /dev/sda (this should make the files apear in /boot/grub, exept menu.lst)
i don't know if this is necessary but after that you should run sudo grub, root (hd0,0) and setup (hd0)
After that create menu.lst in /boot/grub, here-s mine:
```

default 0
timeout 1

title 		Kubuntu 7.04, kernel-2.6.22.4
root 		(hd0,4)
kernel 		/boot/vmlinuz-2.6.22.4 root=/dev/sda5 ro quiet splash
initrd 		/boot/initrd.img-2.6.22.4
quiet
savedefault

title 		Kubuntu 7.04, kernel-2.6.22.4, recovery
root 		(hd0,4)
kernel 		/boot/vmlinuz-2.6.22.4 root=/dev/sda5 ro single
initrd 		/boot/initrd.img-2.6.22.4

title		Memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin

title 		M4cr0$h1t
root 		(hd0,0)
makeactive
chainloader 	+1

```
then replace with your actual kernel and initrd.

I have Kubuntu on /dev/sda5 (hd0,4) and Win on /dev/sda1 (hd0,0). 
Good luck && hope it works ;)

---

