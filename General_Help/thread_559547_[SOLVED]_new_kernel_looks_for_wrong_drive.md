---
title: "[SOLVED] new kernel looks for wrong drive"
date: 2007-09-25
forum: General Help
---

### Post by dpar on 2007-09-25
When the new kernel installed today, it changed my menu.lst to look on a drive that doesn't exist anymore.
When my other drive crashed I moved my ubuntu drive and it went from hd1 to hd0.The kernel looks for it in hd1 after the update.
I imagine this has to do with a change to my fstab setting that I never made. Could someone point me in the right direction?             Thanks

---

### Post by jamvegan on 2007-09-25
It sounds like you know what you have to fix, you just don't know how to boot into Ubuntu now?  If that's the case, you can edit the grub boot command by highlighting the Ubuntu entry that you want in the grub menu when you first start up the machine and typing "e".  Make the appropriate changes and type "b" to boot.  Then you can edit your /boot/grub/menu.lst and /etc/fstab once you log in.

If this isn't what you're having trouble with, or if you need more help with editing the files once you boot, let us know.

---

### Post by NJC on 2007-09-25
dpar;

Check out this Grub help page, it's very helpful. [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I'm not near my Ubuntu computer, but I believe you need to specify the proper drive in menu.lst using kopt:
```


[snip]

## e.g. kopt=root=/dev/hda1 ro

[snip]
```

[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)

Of course change the hda1 to wherever your Linux boot sector is. Until I did this on my machine, every kernel update would overwrite the location of my drive.

---

### Post by dpar on 2007-09-26
Thanks guys.......been out of town for a while so I couldn't get back for a while.

> It sounds like you know what you have to fix, you just don't know how to boot into Ubuntu now?
Nope, I now how to get into ubuntu, just don't know how to fix it.:lolflag:

NJC: I think you got me onto the right track!!  I'll give that a try, I'm pretty sure it will solve the problem.

---

### Post by NJC on 2007-09-26
I just checked my menu.lst. Here's my boot line:
```
kernel		/boot/vmlinuz-2.6.15-29-386 root=/dev/hdb1 ro quiet splash acpi=off
```

To ensure "/dev/hdb1" is replaced after kernel update, I used:
```
kopt=root=/dev/hdb1 ro
```

For the "ro quiet splash acpi=off" part of the line I use:```
defoptions=quiet splash acpi=off
```

---

