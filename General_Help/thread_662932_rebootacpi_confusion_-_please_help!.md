---
title: "reboot/acpi confusion - please help!"
date: 2008-01-09
forum: General Help
---

### Post by kiisu on 2008-01-09
Hi,

I've had some problems using both restart and shutdown on my Toshiba p200 - first documented here without any success or help:
[http://ubuntuforums.org/showthread.php?t=655896](http://ubuntuforums.org/showthread.php?t=655896)

To summarize, the laptop would often get stuck on a blackish-grey screen before loading. Once I figured out it actually was loading but not displaying anything on my laptop screen, I tried hooking into my tv through s-vid and that worked. So it seems to be a problem of recognizing my screen.

Using the s-vid connection I can look around at the system log but being a newbie I'm not 100% sure what to look for - I saw something about a bad kernel module, also error messages about acpi.

Searching the forums, I see a lot of reports about acpi problems in toshiba / phoenix bios, but no real solutions, just a lot of lists of possible codes to add to the /boot/grub/menu.lst (eg. acpi=off, noapic, apm=on etc etc....)

Is there anyone who can work with me on this to diagnose the exact issue? or can it be fixed by modifying/updating the kernel? or should I try a distro other than Ubuntu, since this seems to be a distro-specific issue from what I have read?

any and all help is appreciated - I really dont want to run away from the problem especially after I have worked so hard to get everything else in my system up-and-running

---

### Post by kiisu on 2008-01-10
I decided to do something crazy (for a new-b) and upgrade to the development version, Hardy.

When it tried to reboot into the new kernel the Ubuntu splash screen got stuck at about 3/4 loading. But, I am able to boot Hardy using my old kernel version fine, and theres no restart problems anymore and the computer is even faster.

So, how do I set it to boot into that kernel version everytime?

---

### Post by kiisu on 2008-01-10
From my /boot/grub/menu.lst:
> 
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all


## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.24-3-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-3-generic root=UUID=611e71a2-0261-4dbf-b0c6-0c5fa1672ab8 ro noapic pnpbios=off acpi_osi=!Linux quiet splash
initrd		/boot/initrd.img-2.6.24-3-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-3-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-3-generic root=UUID=611e71a2-0261-4dbf-b0c6-0c5fa1672ab8 ro noapic pnpbios=off acpi_osi=!Linux single
initrd		/boot/initrd.img-2.6.24-3-generic

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=611e71a2-0261-4dbf-b0c6-0c5fa1672ab8 ro noapic pnpbios=off acpi_osi=!Linux quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=611e71a2-0261-4dbf-b0c6-0c5fa1672ab8 ro noapic pnpbios=off acpi_osi=!Linux single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

Is it just as simple as putting the 2.6.22-14 kernel above the 2.6.24-3 ?

---

### Post by Craigus on 2008-01-10
You can do that.

Alternatively if you change the line ```
default		0
```

to:

```
default		2
```

that should also work.

---

### Post by kiisu on 2008-01-16
Thanks Craigus - your solution worked, I tried it first.

In regards to my original problem, not loading the screen at boot: upgrading significantly helped but didn't totally fix it (still occurs every 10 boots or so).

Comparing wit h a very similar computer, I'm strongly suspecting a BIOS upgrade will solve it once and for all. I have a Phoenix BIOS v1.40, my friend's nearly identical computer is Phoenix 1.70, and running the same systems he encountered zero boot issues.

2 questions: a) Can anyone who has gone through this updating process on Ubuntu help me?    and b) Considering I still have a warranty valid on this laptop, am I better off letting Toshiba do this rather than run the risk of bricking my own?

maybe I should make a  new thread for this ......

---

