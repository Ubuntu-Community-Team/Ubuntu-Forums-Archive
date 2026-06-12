---
title: "[SOLVED] Need Advice for my Dual Boot problem."
date: 2008-06-20
forum: General Help
---

### Post by redonwhite on 2008-06-20
Hello.  I have been trying to dual boot xp and ubuntu with two sata hard drives.  I finally decided to just do a clean install of both OS.  I installed XP on Sata 1, and Ubuntu on Sata 2.  On set up of Ubuntu i told it to use entire space of Sata 2 with default advanced options.

Both OS have been installed.  But when i reboot i get this message
"DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"

So i went into my BIOs and made sure that my first boot item was Sata 2.  So that grub could come up and ask me to boot either XP or Ubuntu.  But still it says that Error.  I checked Sata cables and power cables to make sure they weren't loose. And both Sata Hard drives are recognized in BIOS as well.  
Thank you for your time.

---

### Post by iaculallad on 2008-06-20
What did you install first, Windoze or Ubuntu?

---

### Post by VMC on 2008-06-20
> **redonwhite said:**
> Hello.  I have been trying to dual boot xp and ubuntu with two sata hard drives.  I finally decided to just do a clean install of both OS.  I installed [COLOR="Red"]XP on Sata 1[/COLOR], and Ubuntu on Sata 2.  On set up of [COLOR="Red"]Ubuntu[/COLOR] i told it to use entire space of [COLOR="Red"]Sata 2[/COLOR] with default advanced options.

Both OS have been installed.  But when i reboot i get this message
"DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"

So i went into my BIOs and made sure that my first boot item was Sata 2.  So that grub could come up and ask me to boot either XP or Ubuntu.  But still it says that Error.  I checked Sata cables and power cables to make sure they weren't loose. And both Sata Hard drives are recognized in BIOS as well.  
Thank you for your time.

The red above means that Grub is installed on the first SATA drive or SATA 1. Change BIOS to boot on the first SATA drive.

If that doesn't work you need to output these

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by redonwhite on 2008-06-20
> **iaculallad said:**
> What did you install first, Windoze or Ubuntu?

I installed XP first on Sata 1.  Then ubuntu on Sata 2.

---

### Post by redonwhite on 2008-06-20
> **VMC said:**
> The red above means that Grub is installed on the first SATA drive or SATA 1. Change BIOS to boot on the first SATA drive.

If that doesn't work you need to output these

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

Thank you my friend.  Switching my boot device to Sata 1 fixed my issue.  Ive boot tested Ubuntu and XP and both seem to be booting perfect.  Thanks again for your time.

Out of curiosity, why did Ubuntu install grub on sata 1 even though it was installed on sata 2?

---

### Post by werries on 2008-06-21
i think its the default to install on the first harddrive. cause thats usually the one that is the boot device.

you could have changed it at install. when you confirm, theres an "advanced" button for boot stuff.

---

### Post by BLTicklemonster on 2008-06-21
My problem is different. I installed xp64 on a drive, then turned around and installed hardy 64 and bam, no grub. Saw this post, then installed hardy 64 on the first drive because the other install was on the third hard drive, and bam, no grub.

I got nothing here.

I can't get into ubuntu at all, so where do I go from here? I know I left the computer booting from the cdrom, maybe (doubtful but work a try) if I set it to boot from the first drive instead. 

Hint:

this motherboard only has one ide slot. I have the first drive as master, then the cd slaved. I have a pci mount ide controller mounted with two hard drives on it.

Ubuntu was running great like this before, but it was 32 bit from when I had a different motherboard in this machine, so when I upgraded, I just dropped all the drives in with the ide controller installed, and everything but windows worked fine. So I figured upgrade them both to 64 bit at the same time, windows first, then ubuntu, just like I'm supposed to. And here I am. Dang!


Edit: Suffice it to say I'm stupid. All is well now, move along, move along. Quit staring at the monster, move along.

---

### Post by VMC on 2008-06-21
With Linux is doesn't matter what partition it resides on. The boot loader, in this case Grub, needs to boot off the first hard drive, first partition. 

You have an add-on controller. What controls it? The BIOS somehow. Look at your BIOS and see who is in control. What hard drive. Does your BIOS even see the PCI controller?

---

### Post by BLTicklemonster on 2008-06-21
> **BLTicklemonster said:**
> 


Edit: Suffice it to say I'm stupid. All is well now, move along, move along. Quit staring at the monster, move along.

:) I'm good to go, thanks.

---

