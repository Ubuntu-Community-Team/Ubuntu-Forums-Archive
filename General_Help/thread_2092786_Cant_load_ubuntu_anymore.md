---
title: "Cant load ubuntu anymore"
date: 2012-12-08
forum: General Help
---

### Post by tygsxr on 2012-12-08
Hi, just recently i switched on my pc to find it loaded the bios then when it was meant to load ubuntu i got this black screen with a heap of numbers and writing and no ubuntu. i got some of the error messages
mount:mounting /dev on /root/dev failed :No such file or directory
mount: mounting /sys on /root/sys failed:No such file or directory
mount:mounting /proc on /root/proc failed:No such file or directory
Target file system doesnt have requested /sbin/init
No init found. Try passing init=bootarg

BusyBox v1.15.3(Ubuntu 1:1.15.3-1ubuntu5)
built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs)
(initramfs)

I have been running Ubuntu 10.04 for about a year and a half now with relatively no probs up to this point. I suspect the problem is due to a faulty usb port.  Any help would be much appreciated. Thanks

---

### Post by Kirk Schnable on 2012-12-08
I manage hundreds of Linux computers at work, and I've never seen an initramfs that wasn't the result of corrupted files on the hard drive. Unfortunately, our solution is to reimage the machine.  Works every time. 

What in the world would make you suspect a faulty USB port?

---

### Post by tygsxr on 2012-12-09
The reason that i suspect that it was something to do with the faulty usb port is because at the time that it first started i pulled out the usb stick and thats when the first error messages started. The screen weird blue flickered a bit so i restarted the pc and that was the message i got. Are you telling me that it is impossible to reload these files from command.. I want to try and fix the problem as i have files on the machine that i dont have a back up of. Cheers

---

### Post by tygsxr on 2012-12-09
tt

---

### Post by tygsxr on 2012-12-09
I found this post [http://pinoy-computing-tips.blogspot.com.au/2010/08/how-to-fix-ubuntu-error-no-init-found.html](http://pinoy-computing-tips.blogspot.com.au/2010/08/how-to-fix-ubuntu-error-no-init-found.html) Its says to put in the ubuntu live cd then do the try ubuntu option. Once that is done it says open terminal then type fdisk -l and read the output. It tells me the Device eg; /dev/sda1 so i typed fsck /dev/sda1 and it says File system mounted or opened exclusively by another program. How do i unmount the file system or find out how which program has it opened

---

### Post by Kirk Schnable on 2012-12-09
> **tygsxr said:**
> I found this post [http://pinoy-computing-tips.blogspot.com.au/2010/08/how-to-fix-ubuntu-error-no-init-found.html](http://pinoy-computing-tips.blogspot.com.au/2010/08/how-to-fix-ubuntu-error-no-init-found.html) Its says to put in the ubuntu live cd then do the try ubuntu option. Once that is done it says open terminal then type fdisk -l and read the output. It tells me the Device eg; /dev/sda1 so i typed fsck /dev/sda1 and it says File system mounted or opened exclusively by another program. How do i unmount the file system or find out how which program has it opened

```
sudo umount /dev/sda1
```

---

### Post by tygsxr on 2012-12-14
Hey Kirk, thanks for your replies, i ended up downloading a copy of slax from [www.slax.org](www.slax.org), then made a bootable disk. Booted it up then run fsck  /dev/sda1 this fixed the errors. Its seems that when i ran the ubuntu live disk it seems to mount something on the drive when technically it should be running straight off the cd. i tried the unmount command but it didnt work. Anyway problem is now fixed. I was wondering buddy which program you would recommend for making a disk image for these sort of emergencies. Cheers mate.

---

### Post by Kirk Schnable on 2012-12-14
> **tygsxr said:**
> I was wondering buddy which program you would recommend for making a disk image for these sort of emergencies. Cheers mate.

If you mean how to make a copy of your hard drive, I use CloneZilla for that sort of thing. 

[http://clonezilla.org/](http://clonezilla.org/)

---

