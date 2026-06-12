---
title: "Can't load Windows XP Partition"
date: 2008-01-09
forum: General Help
---

### Post by icanrule on 2008-01-09
I don't know exactly what it is I did but i think I might of hurt my Windows XP partition.  I was playing around with grub a bit and I think in an attempt to install it I may have installed it on  the Windows partition.  Is it it possible it erased the Windows partition?

The computer loads into Grub and when I choose the Windows partition it just loads grub again.  When I go into the menu.lst file the Windows XP version has root of (hd0,0) which I think is what it is suppose to be.

When I do an Fdisk -l I get the following info:

/dev/sda1   *           1        8977    72107721    7  HPFS/NTFS
/dev/sda2            8978       11773    22458870   83  Linux
/dev/sda3           11774       12161     3116610   82  Linux swap / Solaris

The Sda1 is the Windows partition but how do I get it to load or did I really destroy that partition?

---

### Post by amingv on 2008-01-09
I have no idea what might have happened. But if I was in your place I'd give it a quick check with [super grub]("http://supergrub.forjamari.linex.org/") and see what comes up.

At any rate I believe the data is not lost, but maybe grub is pointing to itself there...

---

### Post by wjp.reg on 2008-01-09
Can you post your /boot/grub/menu.lst as well?

---

### Post by icanrule on 2008-01-09
Here is the menu.lst:

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1e546415-9632-459f-a901-401ee4d70853 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1e546415-9632-459f-a901-401ee4d70853 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by logos34 on 2008-01-09
menu.lst looks correct--sda1 is your ntfs windows partition, and root is pointing to hd0,0.  Has the boot flag (*) too.

Can you mount the xp partition in ubuntu and do you see any files like NTDETECT.COM, NTLDR and boot.ini?  If not then running** fixboot** from the XP install CD might repair it.  You can also use Super Grub Disk.

---

### Post by icanrule on 2008-01-10
I can't mount the XP in Ubuntu or PCLOS.  I always used to be able to mount it in PCLOS very easily.  I don't get much of an error in Ubuntu but with PCLOS it tells me the following:

Mount: wrong.fs type bad option, bad superblock on /dev/sda1

missing codepage or other error

In some cases useful info is found in syslog - try

dmseg | tail or so

I don't know where this so called syslog is so I don't know how to check it.  I did throw super grub onto a DVD and try and boot from it.  Although it doesn't have great instructions while using it.  When I try to boot into Windows it goes to the normal grub loader and then we find ourself in the same horrible situation.

As for the fixboot.  I don't have an option.  Unfortunately I am using a Toshiba laptop.  The DVD they game me doesn't include any options except to reinstall the OS.  Although I may do that at some point I don't want to jump on that band wagon yet.

---

### Post by logos34 on 2008-01-10
you run **dmesg | tail** in a terminal--prints last 10 lines of bootup messages

syslog:

>system>admin>system log

You can do the equivalent of fixboot from Super Grub Disk:

Super Grub Disk-->'Advanced'-->'Windows (Advanced)'-->'Fix Boot of Windows (Partition).

---

