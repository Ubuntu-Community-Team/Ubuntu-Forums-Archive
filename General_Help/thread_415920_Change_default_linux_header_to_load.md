---
title: "Change default linux header to load"
date: 2007-04-20
forum: General Help
---

### Post by Bobtheknight on 2007-04-20
My betters,

I installed linux-headers-2.6.20-15-386, but this header is not loaded on default.  I have to press "esc" on boot stage 1.5 and manually select it from  linux-headers-custom.  I tried 

```

sudo rm -rf linux
```
```

sudo ln -s /usr/src/linux-2.6.20-15-386 linux
```

But it doesn't appear to work.

Any ideas?

---

### Post by Jussi Kukkonen on 2007-04-20
Not sure if we're on the same wavelength here, but... headers are used when you compile software that needs to know about the kernel api. The commands you gave are about the kernel itself, not headers...

Can you describe what you are doing in more detail?

---

### Post by Bobtheknight on 2007-04-20
Right okay, my mistake.  I compiled a custom kernel but it didn't work well with the virtual machine.  So I downloaded the 386 version off of the repository.  But the problem is even with the 386 version installed, everytime I boot my computer up, if I don't do anything, it boots to the custom kernel.  If I press "esc" during bootup, when I get to specify kernels and I have the option of linux-2.6.20-15, linux-2.6.20-14, linux-2.6.20-15-recovery, and a bunch of others, I can select linux-2.6.20-15-386, and it'll work fine.

Now I want to know how to make linux-2.6.20-15-386 the default, so when I boot up my machine and don't touch anything, it boots into linux-2.6.20-15-386, and not linux-custom.

---

### Post by Jussi Kukkonen on 2007-04-21
Ok. You've got two choices. 

First, you can (and probably should anyway) remove the broken kernel package by using whetever package manager you like to use.

Second, the default boot option for grub can be found in */boot/grub/menu.lst*. Be careful when editing the file, you can get into trouble by breaking it. The option you want to to set is **default** and  I suggest you set it to **saved** -- that means whatever kernel was last booted is the default. Read the comments in the file if you want to set a specific kernel as default.

---

### Post by Bobtheknight on 2007-04-21
Yay editing menu.lst solved my problem, I can boot from 386 image now.  However I don't think removing the custom (broken) kernel will be that easy.  As it is custom compiled, it didn't register on Synaptic.  I suspect I have to remove it manually, here is the steps I'm considering.

1.  go to /usr/src
2.  remove the following 2 files and 1 directory
linux-headers-2.6.20.7-custom
linux-headers-2.6.20.7-custom_2.6.20.7-custom-10.00.Custom_i386.deb
linux-image-2.6.20.7-custom_2.6.20.7-custom-10.00.Custom_i386.deb
3.  Edit out the entry in menu.lst for 2.6.20.7-custom

Did I miss anything?  The content of /usr/src is
linux
linux-2.6.20
linux-2.6.20.tar.bz2.1
linux-headers-2.6.20-14
linux-headers-2.6.20-14-generic
linux-headers-2.6.20-15
linux-headers-2.6.20-15-386
linux-headers-2.6.20-15-generic
linux-headers-2.6.20.7-custom
linux-headers-2.6.20.7-custom_2.6.20.7-custom-10.00.Custom_i386.deb
linux-image-2.6.20.7-custom_2.6.20.7-custom-10.00.Custom_i386.deb

Thanks a lot!

---

### Post by Jussi Kukkonen on 2007-04-21
> I suspect I have to remove it manually, here is the steps I'm considering.

Well, you haven't got the entire picture: The files/dir you list are the source dir and and packages you built. After building the packages you installed them (with dpkg) -- that means you can remove them using a package manager (synaptic, apt-get, dpkg, whatever). Remove the corresponding header package too.

You *can* remove the files/folder you mentioned, but that has no relation to the installed kernel and header packages...


EDIT: oh yeah: do not edit menu.lst as you planned. The package manager will do that for you.

EDIT2: what I said above only applies if you did install the kernel packages with dpkg. Let me know if you did something else.

---

### Post by Bobtheknight on 2007-04-21
Why you're right again, I did 
cd .. && dpkg -i linux*.deb
as instructed in the master kernel thread.  So I searched for linux-images this time in synaptic, and I found the custom kernel.  I now removed it from synaptic.

I'll reboot to see if I can still see it in the grub list.

I can't see it anymore :D

Thanks for all your help!

---

