---
title: "EasyBCD Vs Grub"
date: 2013-03-18
forum: General Help
---

### Post by kkelly77 on 2013-03-18
I have my laptop dual booted with Ubuntu 12.04 and Windows 7 Ultimate. I used [THIS]("http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/") installation guide to assist me with the install. I used EasyBCD in Windows 7 to allow me to select which OS would be used upon boot up. I did not realise that Ubuntu 12.04 would have this feature setup automatically. So now when I boot up I get 2 boot option screens:

[IMG]http://i48.tinypic.com/15qdz5c.jpg[/IMG]

[IMG]http://i46.tinypic.com/35mi1vs.jpg[/IMG]

What I would like to do is change the boot process so that only GRUB provides boot options. I tried removing both entries in EasyBCD but this led to the laptop not booting at all, saying it could not find the bootloader. Fixed this by running Windows 7 repair. I then tried to set the countdown timer in EasyBCD to zero but then this meant I was only able to boot into Ubuntu.

Does anyone know what changes I need to make so GRUB boot screen is the only boot option screen I see and that GRUB is the only one that provides OS boot option? Thanks.

---

### Post by oldfred on 2013-03-18
We need to see details to make specific suggestions. But you need grub in the MBR (if not new UEFI) and then grub controls boot. You would have to edit BCD to remove the extra entries to directly boot Windows.
EasyBCD uses grub4dos to chainload to Ubuntu installed in a partition. But grub in a partition is a compromise as it does not really fit. It converts to blocklists or just addresses to find the rest of grub. If grub in Ubuntu is updated it address may change and then you have to re-install grub to partition. Always have Ubuntu live flash drive handy then to make fixes. But you should also have the Windows repairCD just in case also.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by sgage on 2013-03-19
All you have to do is put grub in the MBR:

```
sudo grub-install /dev/sda
sudo update grub
```

That's all.

---

### Post by kkelly77 on 2013-03-19
> **sgage said:**
> All you have to do is put grub in the MBR:

```
sudo grub-install /dev/sda
sudo update grub
```

That's all.

Should I remove all EasyBCD settings before or after putting grub in the MBR?

---

### Post by sgage on 2013-03-19
You don't ***have ***to do it before, but you'll probably want to go in after you're sure it's working and at least set it to 'skip the boot menu'. When you use grub to launch Windows, it simply invokes the Windows boot menu (not the part that's in the MBR, the part in the Windows system partition that generates the boot menu). Since you don't want to see the Windows boot menu, just set it to zero seconds delay or skip it entirely - easily configured with EasyBCD.

---

### Post by Mark Phelps on 2013-03-19
> **kkelly77 said:**
> Should I remove all EasyBCD settings before or after putting grub in the MBR?

IF you get the GRUB menu BEFORE you see Windows and can then boot into Ubuntu without going through the Windows OS selection menu -- you already HAVE Grub in the MBR.

All you would need to do then is use EasyBCD to remove the Ubuntu entry from the Windows BCD.

---

### Post by kkelly77 on 2013-03-19
Solution given by sgage worked. I entered the commands in Terminal and upon restart the GRUB boot menu came up first. I booted into Windows and removed Ubuntu from EasyBCD. Laptop will now boot straight into Windows when selected from GRUB boot screen.

Thanks to everyoe who posted a reply. Now where the hell is the 'SOLVED' option for the thread?!!?

---

### Post by sgage on 2013-03-19
Ha! Finding the 'solved' label baffled me for a bit. You have to edit your message, go to Advanced, and you'll find it under 'prefix' I believe it is...

---

### Post by Moose on 2013-03-19
Just edit the delay for grub and make it 1. So much easier. ;)

---

