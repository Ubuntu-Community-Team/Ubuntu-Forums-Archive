---
title: "GRUB Recovery Live CD"
date: 2007-08-09
forum: General Help
---

### Post by Atra_Phasma on 2007-08-09
Here's my story
I was waiting for my copy of Windows XP (boo!) to come in the mail for my new desktop. I had a small get together with some friends that night and installed Ubuntu 7.04 just so I could use my computer, as all i was lacking was an operating system. After XP came in, I "uninstalled" Ubuntu by using Gparted to reformat the disk. (several times) Now, even though I did that, I still get an error similar to this when I turn on the computer

Error:

GRUB 2.2 cannot load

I now cannot boot the Live CD as it says my APIC timer is not connected, which I bypassed at the boot screen by adding noapic before the last -- that worked, but then I got a message saying 

request_module: runaway loop modprobe binfmt-01ff

that repeated itself a few times. the Windows install disk does not work, Ubuntu LiveCD does not work, and Gparted will not boot from the disk either, giving me similar errors. After searching around, I concluded that it was because GRUB was all messed up on my MBR that nothing was working. Is there a way to fix that I can Restore GRUB to fix this without the LiveCD booting into Ubuntu or a floppy image or something? what is the problem here???????

---

### Post by merlinus on 2007-08-09
Boot from live cd.  Run this in a terminal:

```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```

Substitute results from find for (hdx,x).

-merlin

---

### Post by Atra_Phasma on 2007-08-09
I cant boot from live CD i can only get to the terminal on the main screen that says 

Boot:

---

### Post by merlinus on 2007-08-09
Try SuperGrub:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

If you need help with it:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

### Post by Atra_Phasma on 2007-08-09
thanks!!!! I'll try that!! <3

---

### Post by Circuit99 on 2007-08-09
Hi,

What is happening that your booting direct to hard drive

Need to change bios and boot first from Cdrom

then you can boot straight into Live CD.   


This is link info on Grub Manual

[http://orgs.man.ac.uk/documentation/grub/grub_toc.html#SEC_Contents](http://orgs.man.ac.uk/documentation/grub/grub_toc.html#SEC_Contents)

This is link on how to fix Mbr using FIXMBR

[http://www.ntfs.com/mbr-damaged.htm](http://www.ntfs.com/mbr-damaged.htm)

This link on Fix Mbr and Ubuntu

[http://www.neowin.net/forum/lofiversion/index.php/t365026.html](http://www.neowin.net/forum/lofiversion/index.php/t365026.html)


You don't say what is on your hard drive ?
If you want clean your hard drive is boot with Win9X floppy drive  and use Fdisk the old fashion  way.

The modern solution is PartedMagic found here 

[http://partedmagic.com/](http://partedmagic.com/)

Has Fdisk and similar tools and good manual. 

This should allow do what ever you want to your hard drive and you have the option to boot from usb or PXE(what ever that is.)

Good Luck

:)

---

### Post by Atra_Phasma on 2007-08-09
I have a problme like the one in the link below... I jsut want GRUB off now... not to reinstall Ubuntu... But I dont have Windows.... any idea?
[http://www.neowin.net/forum/lofiversion/index.php/t405091.html]("http://www.neowin.net/forum/lofiversion/index.php/t405091.html")

---

### Post by Atra_Phasma on 2007-08-09
I guess i just want to clear the MBR, but I have nothing to boot into to clear it from, and cant reinstall ubuntu

---

### Post by Atra_Phasma on 2007-08-11
Oh... stupid me.. Hit F5 in XP install CD to bybass ACPI, then load, it overwrites MBR, thanks guys!:)

---

