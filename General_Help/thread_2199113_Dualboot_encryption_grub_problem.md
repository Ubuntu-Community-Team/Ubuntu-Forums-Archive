---
title: "Dualboot encryption grub problem"
date: 2014-01-12
forum: General Help
---

### Post by chaosdesigner on 2014-01-12
Hey all,

I wanted to install ubuntu 13.10 with windows 8 on my new thinkpad and I'm having some small problems. This was my approach:

[LIST=1]
[*]Windows (8.1) was installed first
[*]Then I installed Ubuntu 13.10 and encrypted the system, in addition I used /dev/sda6 in my case as a boot partition
[*]Next I encrypted windows with truecrypt
[/LIST]

Now when I boot up I get to the truecrypt password promt and can log on to windows with it. If everything went correctly I should be able to press ESC and boot up to ubuntu, but when I do so windows starts to do some repairing and he obviously can't find ubuntu.

I'm not sure, but I'm guessing my mistake was, that after installing ubuntu I didn't explicitly install grub on my /boot parition (I guess on the MBR?).

Is there any way for me to fix grub so that the truecrypt bootloader can find it? 

Right now, when I try to install grub I get the following message:

```
root@ubuntu:/# grub-install --force /dev/sda6
/usr/sbin/grub-bios-setup: warning: File system `ext2' doesn't support embedding.
/usr/sbin/grub-bios-setup: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.

```

Thank in advance for your help!

---

### Post by oldfred on 2014-01-12
I do not know encryption, but one other user just installed grub to a flash drive. Then when he wants to boot Ubuntu he boots the grub installed in the flash drive which boots the Ubuntu install on the hard drive.

I think truecrypt takes total control of MBR, and with BIOS only the system in the MBR is bootable. Truecrypt will not configure to multi-boot.

---

### Post by chaosdesigner on 2014-01-15
I'm pretty sure it's doable, there are obviously already a lot of topics about this.

[http://ubuntuforums.org/showthread.php?t=1559318](http://ubuntuforums.org/showthread.php?t=1559318)
[http://wiki.ubuntuusers.de/Dualboot_verschl%C3%BCsseln](http://wiki.ubuntuusers.de/Dualboot_verschl%C3%BCsseln) [German]

At this point I'm sure that if I can somehow reinstall grub to my /boot partition I can get this to work, but when I try to do so, even if I use --force, grub tells me the only way to do so would be with blocklists. Do I maybe need to resize the /boot partition? As soon as I have the time I will post my fdisk output, maybe there is a clue there.

---

### Post by oldfred on 2014-01-15
When you install grub to the PBR or partition boot sector you force it into the PBR. The PBR is just like the MBR in that it has boot code and partition table space. Used more for logical partitions and Windows always uses PBR for boot code. But it is a fixed size.
But grub2 is so large and PBR has no space after it like MBR for core.img that it has to convert to blocklists or hard coded addresses for the rest of grub in boot folder whether partition of in / (root). If a grub file gets moved on update or even fsck then you have to reinstall grub to PBR. So always have a live installer to let you make repairs.

Not sure how you chain load from truecrypt to a PBR? That is why another MBR works easier, whether another drive, or flash drive.

---

