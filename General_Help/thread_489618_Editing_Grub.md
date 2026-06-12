---
title: "Editing Grub"
date: 2007-07-01
forum: General Help
---

### Post by bonestonne on 2007-07-01
i've been in and out of here enough times to be compelled to join, and i have this strange problem that i'm hoping people can shed light on.

I'm currently dual booting with Ubuntu 7.10 and Windows XP. the grub boot menu is as expected, linux on top, windows on bottom.

now, my main issue is that there are two instances of Linux on the GRUB boot menu.  the top most one is what i use, as i trust it wont fail me, but the second one worries me, because when looking at the menu.lst, they're both accessing the same drive. i think it from a failed install on the drive, but i don't want to mess up my GRUB.

i saved a new copy of the GRUB menu.lst on my desktop, which has the second Ubuntu and recovery entry removed, is it safe to replace the current one with that?

thats my main concern. i really don't want to reinstall everything because of a stupid mistake..as my new computer comes in about a little less than a week, i dont want to be fixing my workstation and trying to set up a new one at the same time.

some of my widely used programs on both OSes are Audacity, K-3D, Gaim and Firefox...generally my life right there, but having to start over would be beyond annoying, as installing Satanic Edition is a lot of  command line stuff that i don't enjoy doing each time [however i think that using synaptic to install it is whimpy].

thanks for the help in advanced,
bonestonne

---

### Post by CheShA on 2007-07-01
it's safe to replace your grub menu.lst with the other one - peachy.  just remove the offecnding section and it won;t appear on your list any more :) back up the old menu.lst -  if you've messed anything up, the worst case scenario is you have to boot from the Ubuntu live cd, mount your hard drive and copy the old menu.lst back.

---

### Post by bonestonne on 2007-07-01
thanks a bunch, worked without a problem.

if i'm right, that would mean that if i wanted to add another OS to the list on another drive or partition, i just enter it the same way the others are? meaning the partition its located on, a mount point and name?

could make it much easier for me to triple boot when i try it.

---

### Post by CheShA on 2007-07-01
Dependent on the os, basically yes.  Like almost everything else, it's just a case of rewriting a text file.  Here's mine:
```

# Tue Jun 26 17:18:07 BST 2007
default 0
timeout 8

title Ubuntu Linux 64Bit
root (hd0,4)
kernel /vmlinuz root=/dev/mapper/nvidia_acjibbfe8 ro quiet splash
initrd /initrd.img

title Ubuntu Linux 64Bit - Verbose Boot
root (hd0,4)
kernel /vmlinuz root=/dev/mapper/nvidia_acjibbfe8 ro 
initrd /initrd.img

title Ubuntu Linux 64Bit - Single User
root (hd0,4)
kernel /vmlinuz root=/dev/mapper/nvidia_acjibbfe8 ro quiet splash single
initrd /initrd.img

title Windows XP 32 or Windows Vista Enterprise x64
rootnoverify (hd0,0)
chainloader +1

```


Notice the last entry is slightly different for Windows; it tells grub not to verify the status of   the partition i've pointed it at then tells it there is another "boot-sector-type" instruction coming,     The result of choosing this option is the menu provided by windows' own boot loader on the partition I pointed at, I don't know how it would look if you added an OSX.  

My partitions are considered to be located at /dev/mapper/nvidia* because I use nVidia fakeraid.

---

### Post by bonestonne on 2007-07-01
i was sort of aiming towards adding mac to the mix.

i have a Pentium D 940 in the mail, and i plan on triple booting Mac/Windows/Linux...i guess i'll have to look around for how to add it.

I'm also debating using XP or Vista...there are parts of one that i like more than in the other, so i might just stick with XP and look for more support. i'll be using a 64bit linux, and 32bit windows and 32bit OS-X.

---

### Post by CheShA on 2007-07-01
As i said, I don;t have experience messing with osx/linux (apart from about 5,000 completely failed attempts at installing it on the iMac g5 work gave me).  Here's  a grub entry  I just found for BSD though :

```

# For booting FreeBSD 
title FreeBSD 
root (hd1,a) 
kernel /boot/loader 

```

And, as i expected, the A quick Google for "OSX Grub" quickly [yielded]("http://forum.insanelymac.com/lofiversion/index.php/t3622.html") a string similar to the Windows one, since OSX will want to have it's own boot sector (and con its self it's the only OS worth using) just like Windows does:

```

title OSX86
root (hd0,0)
chainloader +1
```

---

