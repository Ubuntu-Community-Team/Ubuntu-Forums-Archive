---
title: "what happen with my /boot"
date: 2008-04-13
forum: General Help
---

### Post by quienesanonimo on 2008-04-13
Hi, I have a problem

I have installed Ubuntu 7.10 with the "alternate cd" and the option that allow me to encrypt the hard disk

If you don't know, that thing create a 250mb partition for /boot (without encryption) and the other one with the rest of the memory for everything else (encrypt)

So that was the distribution of the HD

sda1 250 mB in ext3 (for grub)
sda2 119 gB (extended partition only with sda5)
sda5 119 gB unknown format (crypt)

Usually grub loads ok and then usplash was stopped for half second and askew me for the password for sda5 and it continue 


But one day, rebooting the grub for an error with 15 not found files

in /boot/grub/menu.lst says this
##
default        0
timeout        0    
hiddenmenu

title linux
    root (hd0,0)
    kernel /vmlinuz-2.6.22-8-generic ro quiet splash boot=disk
    initrd /initrd.img
##

But when I did an ls /boot I found this

-rw-r--r-- 1 root root  424317 2008-02-12 10:39 abi-2.6.22-14-generic
-rw-r--r-- 1 root root   75311 2008-02-12 10:39 config-2.6.22-14-generic
drwxr-xr-x 2 root root    1024 2008-04-07 01:37 grub
-rw-r--r-- 1 root root 8030152 2008-03-27 15:33 initrd.img-2.6.22-14-generic
-rw-r--r-- 1 root root 8382216 2008-03-27 14:58 initrd.img-2.6.22-14-generic.bak
drwx------ 2 root root   12288 2008-03-22 04:49 lost+found
-rw-r--r-- 1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root  823535 2008-02-12 10:39 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root 1764536 2008-02-12 10:39 vmlinuz-2.6.22-14-generic


If you look the name doesn't look the like the settings of the grub, even if you try to change the configuration of the menu.lst for check the names even if you rename the files for works if is solve the 15 error of grub and started to charge the uplash as always (also tried with initrd.img-2.6.22-14-generic.bak) I also tried with the second (but when before asked me for the password for sd5) but it gets blocked, if I do before alt+f2 I get realized that I have a Kernel panic. 

I am so ******, I think that for any motive I delete or downgrade any file of /boot or I ****** something of grub.

Sorry for my english
thanks

---

### Post by schnittchen on 2008-04-14
quienesanonimo,

did you actually rename files in your boot partition? If so, please revert this if possible. You should be able to do so from a livecd.

Please first try the following:
* Enter the grub menu by pressing escape before boot
* Instead of pressing enter on a menu item, type "e" to (temporarily) edit it
* Pick the line which says "kernel" in front and press "e" there again
* Change the kernel image to the exact filename present in your boot partition
* Do the same for the initrd line
* Boot (I think by pressing "b", but it says on the bottom of the screen)

If that does not work, please post the exact error lines you see.
If it does work, you still need to configure things permanently.

---

