---
title: "[SOLVED] Kernel security update 2.6.22-14.51 breaks system"
date: 2008-02-06
forum: General Help
---

### Post by DanielH on 2008-02-06
It did the automatic update to kernel 2.6.22-14.51 today and it left my system unbootable.

The system just stops after initializing the SATA devices, as far as I can tell, right before it mounts the root partition. After some time, it falls back into a busybox shell. 

I'm running Ubuntu 7.10 on a Dell Inspiron 6000. The root partition and  the installation seem to be okay, I was able to start it with another kernel.

I have no idea where to start looking, any hints are appreciated.

Cheers,
Daniel

---

### Post by DanielH on 2008-02-06
I found an possible explanation and a solution to the problem.

The root partition is referenced by its UUID in the grub menu file and this UUID has changed during the kernel update.

The solution is to edit the grub menu file
```
$ sudo vim /boot/grub/menu.lst
```

And change the line starting with # kopt=

For me it said
```
# kopt=root=UUID=eda0f92a-bab7-402e-9504-648dd9261e90 ro
```
I changed the UUID in the root parameter the device file of the root partition (/dev/sda3 for me).  
```
# kopt=root=/dev/sda3 ro
```
Don't let the # at the beginning of the line delude you, this line only looks like comment, update-grub will use it as parameter to generate the entries in the boot menu.

Then run
```
$ sudo update-grub
```

update-grub will replace the device file with the correct UUID.


Hope that helps anybody!

Daniel

---

### Post by MikeTheBum on 2008-02-06
I had a similar problem, installing 
linux-image-2.6.2-14-generic (2.6.22-14.51)
via the automatic updates made my system unbootable.

I found that the patch above edited the /boot/grub/menu.lst file

It changed lines like this
root            (hd0,5)
To lines like this
root            (hd0,0)

I was able to use the facilities in grub to edit this back during boot so i could get it going again.

---

### Post by heatblazer on 2008-02-07
Hmmm... I`ve upgraded my kernel but none of such has happened. Guess it`s a rare bug... But souds creepy...

---

### Post by MikeTheBum on 2008-02-10
Dang, happened again on another system, in this case my ubuntu boot disk is hd0,2 - the auto update changes it to hd0,0

I both cases it was a dual boot machine with windows 2000 on the same disk drive, different partition hd0,0.

If you are booting from hd0,0 then it would not cause any problems i guess.

---

