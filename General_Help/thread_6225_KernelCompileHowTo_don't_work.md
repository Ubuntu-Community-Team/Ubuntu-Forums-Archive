---
title: "KernelCompileHowTo don't work"
date: 2004-11-26
forum: General Help
---

### Post by leos on 2004-11-26
Hi,
 I don't speak well english and i am new in the linux world....
I wnted config my Kernel because i wanted install my modem usb,
so i have found this guide:

[URL=http://www.ubuntulinux.org/wiki/KernelCompileHowto]
http://www.ubuntulinux.org/wiki/KernelCompileHowto[/URL] 

but when i do

```
# apt-get install build-essential bin86
``` 

Ubuntu say me that is impossible to find bin86

help me!
thank you

---

### Post by Juergen on 2004-11-26
No problems here. 

Typo? Maye your package-mirror is missing files?

If nothing helps, you could connect to your package-mirror via ftp and look in pool/main/l/linux86. If it's there download bin86_0.16.14-1_i386.deb and install with dpkg -i

---

### Post by leos on 2004-11-26
[QUOTE=Juergen]No problems here. 

Typo? Maye your package-mirror is missing files?

If nothing helps, you could connect to your package-mirror via ftp and look in pool/main/l/linux86. If it's there download bin86_0.16.14-1_i386.deb and install with dpkg -i[/QUOTE]

hi,
 thank you for reply me 

 i did like you say but now, when i do 

```
#make menuconfig
``` 

Ubuntu say that not  to find ncurses-dev and install it, but  i have  installed libncurse5-dev and not find ncurses-dev in [this mirror](http://mirror.xmission.com/ubuntu/pool/main/n/ncurses/)

---

### Post by Juergen on 2004-11-27
[QUOTE=leos]Ubuntu say that not  to find ncurses-dev and install it, but  i have  installed libncurse5-dev and not find ncurses-dev in [this mirror](http://mirror.xmission.com/ubuntu/pool/main/n/ncurses/)[/QUOTE]
Hm, difficult to say out of the distance,  libncurses5-dev should IMHO be OK.

Maybe you could try to get 'make gconfig' to work. I think you need libglib2.0(-dev), libgtk2.0(-dev) and libglade2(-dev) for this.

---

### Post by leos on 2004-11-27
Hi,
 now "make menuconfig" work, because i had confused lincurses5-dev with libncurses5_5....  :D 
a question:
After i have config my kernel, how i modify /boot directory?

thanks

---

### Post by leos on 2004-11-28
Hi
 I have created and installed the kernel-image
In the HowTo page say that installing the new kernel, it set up "vmlinuz" and "initrd" but this isn't true! because in "/" directory there are vmlinuz, vmlinuz.old, initrd.old but there isn't initrd.img!!!

Now, in /boot/grub/menu.lst, there is a new choose (the new kernel) and when i select it, ubuntu say:
 **crc-error system halted**    
Why?

thanks

---

