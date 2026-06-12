---
title: "grub hanging - please help!"
date: 2006-09-16
forum: General Help
---

### Post by ninjamatic on 2006-09-16
EDIT NOTE: when i booted into winxp for the first time after installing ubuntu, IT AUTOMATICALLY RAN CHKDSK AND REBOOTED. i have a sneaking suspicion that it overwrote my mbr, but i don't know how to restore the mbr and i can't access my cd burner and i don't have a floppy drive (see below).

hi all,

i'm a linux newbie. i recently installed ubuntu on my laptop (hp pavilion dv5000, 80gb hd, 1gb ram), next to winxp. i just installed a new kernel (686-smp), and i haven't been having any problems booting into winxp or ubuntu. about 10 mins ago i turned on my computer and my system just hung at grub loading screen. it said "Grub loading 1.5..." and it didn't do anything else. i finally shut it down and tried again. still nothing.

so i booted with my ubuntu live cd and went into safe mode. that's where i am right now. i tried installing lilo with synaptic, but when i try to run liloconfig, i get:

```

LILO, the LInux LOader, sets up your system to boot Linux directly
from your hard disk, without the need for a boot floppy.

    WARNING!
        Your /etc/fstab configuration file gives device unionfs as the root
        filesystem device. This doesn't look to me like an "ordinary" block
device. Either your fstab is broken and you should fix it, or you are
using hardware (such as a RAID array) which this simple configuration
program does not handle.

You should either repair the situation or hand-roll your own
/etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig
again to retry the configuration process.
Documentation for LILO can be found in /usr/share/doc/lilo/.

```

this is what /etc/fstab looks like:

```

ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
ubuntu@ubuntu:~$

```

i have no idea what any of this means. before, my computer would load up grub and i'd have about 9 options (new kernel + safe mode, old kernel + safe mode, memtest, and three windows options, and something else). i'd usually either go with the first win option ("Microsoft Windows XP Professional") or with the new kernel option.

i read somewhere that i should run fstab /mbr. i did that and this is the output:

```

ubuntu@ubuntu:~$ fdisk /mbr

Unable to open /mbr

```

and my laptop doesn't have a floppy drive. AND i don't have a windows recovery cd.

i'd reinstall ubuntu, but the exact same thing would probably happen.

thanks in advance,
mike

EDIT: here are some screenshots.

here's the ubuntu partition with some very not-cool looking messages:

[IMG]http://www.booyaka.com/~aziel/Screenshot.png[/IMG]
Fig. 1: Not cool, dude. Not cool.

and here's the "hard disk" with unionfs (i don't get this. i only have one hd):

[IMG]http://www.booyaka.com/~aziel/Screenshot-1.png[/IMG]
Fig. 2: Also not cool.

---

### Post by Oxin on 2006-09-16
I reread your post and here's my suggestion. The other stuff I'll leave up for reference at the bottom but you probably won't need it.
1. Boot with the Ubuntu Live CD
2. Open the terminal
3. Enter: fdisk -l     and make note of your linux partition
4. Enter: sudo grub
4. You should have a grub prompt and enter the following but for the root part, make sure you aim it to your linux partition.
For example:
hda1 => root (hd0,0)
hdb1 => root (hd1,0)
hda2 => root (hd0,1)
and so on.
> grub
> root (hd0,0)
> setup (hd0)
> quit
Now reboot and you should be good to go.

-----------------------
Ok. Well, lucky for you I experienced a similar problem last night and after about 2+ hours, I'm back to normal. My problem occured after I resized my ntfs partition and basically split it. That resulted in my partition numbers being off by one. I don't know if that's the case since you had the problem randomly.
Here's a few bits of helpful info:
1. The additional harddrive is the ramdisk. Instead of looking in /etc/fstab , look in /media/<your linux partition>/etc/fstab
2. You can download such a thing as Grub for Dos which will work under XP but you probably won't need it.

---

### Post by ninjamatic on 2006-09-17
thanks for your help. since i had a fresh install of ubuntu, i decided to just reinstall (before i saw your post). i haven't booted into winxp as of the reinstall, but i expect the same thing is going to happen. when it does, i'll use your advice. i also made a copy of the super grub cd, since it supposedly fixes problems like this.

thanks again!

---

