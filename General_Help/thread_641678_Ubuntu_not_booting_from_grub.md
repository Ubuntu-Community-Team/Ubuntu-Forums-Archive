---
title: "Ubuntu not booting from grub"
date: 2007-12-15
forum: General Help
---

### Post by ThumbBumpkins on 2007-12-15
Hey all, I just installed Ubuntu on my system for the first time after a several month break, and I downloaded, burned and ran Ubuntu 7.10 without a hitch. However, after the installation, GRUB failed to appear and instead Windows XP booted up directly. After some tinkering I have managed to get GRUB to load. However, when I select Ubuntu, I get error 22 (I think): Partition does not exist. Windows loads completely correctly.

Even more mysterious, when I try to open /boot/grub/menu.lst in either gedit or kate, it is completely blank.

Both Windows and Ubuntu are installed on the same SATA drive.

/dev/sda1 = NTFS, my Windows partition
/dev/sda2 = ext3, Linux root partition
/dev/sda3 = swap for Linux

Any help at all would be very much appreciated, I'm eager to jump back into Ubuntu.

My Ubuntu install is brand new, so I could repartition/reformat/reinstall as necessary. However, I would really, really like to avoid reinstalling windows or deleting that partition.

---

### Post by logos34 on 2007-12-15
On the ubuntu menu selection hit 'e' key...what does the 'root' line read?  It should be '(hd0,1)' -- i.e. the second partition. (grub starts counting frm 0).

---

### Post by ThumbBumpkins on 2007-12-15
It does say hd(0,1).

---

### Post by logos34 on 2007-12-15
> **ThumbBumpkins said:**
> Hey all, I just installed Ubuntu on my system for the first time after a several month break, ... After some tinkering I have managed to get GRUB to load. However, when I select Ubuntu, I get error 22 (I think): Partition does not exist. Windows loads completely correctly.
...

Even more mysterious, when I try to open /boot/grub/menu.lst in either gedit or kate, it is completely blank.

Have you ever run ubuntu successfully on this machine before?  And what 'tinkering' did you do to get grub to load?

The blank menu.lst: maybe you had the path wrong (common mistake when working frm live cd)

---

### Post by logos34 on 2007-12-15
try running a filesystem check on ubuntu frm the live cd:

sudo e2fsck -y -f -v /dev/sda2

And then reinstall grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ThumbBumpkins on 2007-12-16
Yes, this machine did run linux completely without incident in the past, and I haven't made any hardware changes at all since then.

As for the tinkering, I don't really remember exactly what it was that made grub start actually loading. I think I replaced it with NTLDR and then reinstalled grub, at which point it started loading at least.

I just did your directions, checking the disc and reinstalling, but nothing seems different. Menu.lst is still blank and Ubuntu still wont load from GRUB.

---

### Post by logos34 on 2007-12-16
> **ThumbBumpkins said:**
> Yes, this machine did run linux completely without incident in the past, and I haven't made any hardware changes at all since then.

As for the tinkering, I don't really remember exactly what it was that made grub start actually loading. I think I replaced it with NTLDR and then reinstalled grub, at which point it started loading at least.

I just did your directions, checking the disc and reinstalling, but nothing seems different. Menu.lst is still blank and Ubuntu still wont load from GRUB.

when you access menu.lst from the live cd, the path (if you clicked to mount root in nautilus) is most likely **/media/disk**/boot/grub/menu.lst.  It can't be blank because Grub is accessing it when you boot--that's what is displayed on the grub screen (you choose xp and it starts, but not ubuntu).  

When you had ubuntu installed previously, was it in approximately the same place--second partition after windows? 

You could try a different bootloader, like [GAG]("http://www.users.bigpond.net.au/hermanzone/p12.htm") or even LILO.

---

