---
title: "Kernel panic after online update..."
date: 2007-01-15
forum: General Help
---

### Post by moogii on 2007-01-15
I installed Ubuntu 6.10 few days ago..alongside with my SuSE,Fedora Core 6 on 40GB single hard drive ....It was good and amazing

Yesterday I got error message

"Unable to mount root fs on unknown-block(0,0)"

Then unable to boot into Ubuntu, surprisingly....

I suspect the online update got something wrong.because I applied online update just before reboot.....](*,) 

I read some1 was complaining about this online update somewhere around ,bu I couldnt find the treat.

Now is anyone out there to help me.I have the Alternate install CD..Also i able to fix boot options within SuSE GRUB ..


PS; I started few other treats in this forum,but no one able to help me before...
It seems this forum users are a little selfish or kind of busy people?

cos when I needed help for my FC6,SuSE, I able to get help easily and quickly from their forum,but here NO......I hope this is only at the beginning....:rolleyes:

---

### Post by moogii on 2007-01-15
Also it could be kind of lock up that happens after force shut down.

I once shut it down by pushing the power button

---

### Post by moogii on 2007-01-16
No one??????????????

Dont even compare Ubuntu to Windows 3.

Ubuntu is the worst distro ,No one knows whats the solution.

Doesnt even have repair option like most other major linux distro...

Total waste of time.................................................................................................

---

### Post by Pawel Stolowski on 2007-01-16
Did you make any changes to /boot/grub/menu.lst after installing edgy? If you ever changed root=/dev/... (because e.g. hdd reordering) parameter for the kernel entry you were using but forgot to copy the change to the default entry, then newly installed kernels could use wrong "root=..." setting. 

I'm just guessing, something like the above just happened to me some time ago...

---

### Post by chrisccoulson on 2007-01-16
It might help if you boot from the live CD and post the output of
```
fdisk -l
```

Also, can you mount your root filesystem and post the contents of /etc/fstab and /boot/grub/menu.lst. With that information, somebody here might be able to help you.

---

### Post by moogii on 2007-01-16
> **Pawel Stolowski said:**
> Did you make any changes to /boot/grub/menu.lst after installing edgy? If you ever changed root=/dev/... (because e.g. hdd reordering) parameter for the kernel entry you were using but forgot to copy the change to the default entry, then newly installed kernels could use wrong "root=..." setting. 

I'm just guessing, something like the above just happened to me some time ago...



It may well be the issue.Because I changed the VGA mode within "boot config"-YaST-SuSE.

Because there was no boot screen, during start up as well as before shutting down.

i read a threat somewhere in this forum that some1 able to get the boot screen by adding 
"vga=791" or corresponding value to boot menu.

So I just add "vga=791" at the end of the list.

personnally I think thats not capable of messing that serioius?

i  even changed back to as it was.still is the error

---

### Post by moogii on 2007-01-16
This is my GRUB entry list looks like :

> 

root (hd0,1) kernel /boot/vmlinuz root=/dev/hdc2 vga=0x314 selinux=0 resume=/de-initrd /boot/initrd

root (hd0,0) kernel /boot/vmlinuz-2.6.18-1.2798.fc6 root=LABEL=/1 ro rhgb quiet

root (hd0,5) kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc6 ro quiet




---

### Post by moogii on 2007-01-16
Hey thank you


> **chrisccoulson said:**
> It might help if you boot from the live CD and post the output of
```
fdisk -l
```

Also, can you mount your root filesystem and post the contents of /etc/fstab and /boot/grub/menu.lst. With that information, somebody here might be able to help you.

I dont have the /boot/grub/menu.list" Do I?

bECAUSE i didnot install GRUB boot loader....However I was able to load Ubuntu before.

Do you recommend me install GRUB if I install Ubuntu again?

Cos as u know i installed Suse.FC6 on my hard already. I only installed SuSE GRUB..


Here is my /etc/fstab entry:

> # /etc/fstab: static file system information.	
#	
# <file system> <mount point>   <type>  <options>       <dump>  <pass>	
proc            /proc           proc    defaults        0       0	
# /dev/hdc6	
UUID=7ae9af12-3990-43c3-956a-6ceb68a1b7a8 /               ext3    defaults,errors=remount-ro 0       1	
# /dev/hdc5	
UUID=1521ff29-e615-4e78-8591-ce2ca78c01bc /home           ext3    defaults        0       2	
# /dev/hdc1	
UUID=e55e574b-87f5-4340-9ca3-45671df7385f /media/hdc1     ext3    defaults        0       2	
# /dev/hdc2	
UUID=a8e33998-77be-425f-9cdd-cc878df2cfc4 /media/hdc2     reiserfs defaults        0       2	
# /dev/hdc3	
UUID=8ba8838e-11bc-4803-8ea7-5bfedc947cf8 none            swap    sw              0       0	
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0	
/dev/           /media/floppy0  auto    rw,user,noauto  0       0	

---

### Post by jocko on 2007-01-16
> **moogii said:**
> No one??????????????

Dont even compare Ubuntu to Windows 3.

Ubuntu is the worst distro ,No one knows whats the solution.

Doesnt even have repair option like most other major linux distro...

Total waste of time.................................................................................................

Usually you'll get answers within a few minutes to a few hours if you provide enough information. Saying Ubuntu is the worst distro is probably not a good idea for solving the problem.

And yes Ubuntu does have a recovery option. In a standard install you will get a recovery mode option in the grub menu, which lets you boot into a root CLI. I'm not sure what happens when you dual boot with other distros.

> **moogii said:**
> This is my GRUB entry list looks like:
root (hd0,5) kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc6 ro quiet


I'm not sure if anything is wrong with your grub menu, but try adding these lines to the end of your menu.lst (the second section is for recovery mode):
```

title        Ubuntu, kernel 2.6.17-10-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc6 ro quiet splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc6 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

```

---

### Post by moogii on 2007-01-16
> **jocko said:**
> Usually you'll get answers within a few minutes to a few hours if you provide enough information. Saying Ubuntu is the worst distro is probably not a good idea for solving the problem.

And yes Ubuntu does have a recovery option. In a standard install you will get a recovery mode option in the grub menu, which lets you boot into a root CLI. I'm not sure what happens when you dual boot with other distros.




I'm not sure if anything is wrong with your grub menu, but try adding these lines to the end of your menu.lst (the second section is for recovery mode):
```

title        Ubuntu, kernel 2.6.17-10-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc6 ro quiet splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc6 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

```




thanks for your try .Your reply might well help for the others who are having same problem as me

..........After adding these line to my menu list ,then after rebooting

my original ubuntu boot text line replaced with the recovery mode,then 2 more recovery mode boot text line appeared on my GRUB LIST Entry                                                            ,of course none of them work..... loaded into black screen of death;)

---

