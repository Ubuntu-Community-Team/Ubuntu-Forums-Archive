---
title: "Ubuntu won't boot after partition"
date: 2015-12-20
forum: General Help
---

### Post by jonathan104 on 2015-12-20
I used gparted to partition my hard drive to attempt to install Windows on my laptop, but after I restarted it all I see is a white cursor, I have tried booting from a USB image of Ubuntu but it doesn't work

---

### Post by gtozzi on 2015-12-20
It's hard to give you advice without knowing what you've done in detail.

If you have a backup of the partition table, try to restore it.

If you don't please try to describe winch steps you took with gparted.

---

### Post by jonathan104 on 2015-12-20
I'm not really sure, I followed some steps on the Internet and created a new ntfs partion with the software, but it didn't show up on my disk analyser so I thought I should restart, but not it won't boot.
I don't have a back up
Also I can only get into the bios, and booting from USB with a fresh Ubuntu isn't working

At this point I just want to remove it but I Can't access anything but the bios

---

### Post by gtozzi on 2015-12-20
It's hard to recover it with so few information.
It's probably best if you try a fresh install/automatic recover.

If you had any important data on that drive, it's time to do a backup before attempting anything else.

If the bios does not boot from USB, then probably there is some problem with that USB strick.
Please double-check your boot order, then try a different USB stick or a DVD: there is no apparent reason why gparted should have interfered with the bios.

---

### Post by jonathan104 on 2015-12-20
I only have 1 USB big enough so I'll order a new one and try, I'm sorry I don't have enough information I am not very good at this and just messed around with gparted

---

### Post by sudodus on 2015-12-20
As *gtozzi* wrote, it is hard to give you advice, because we know too little about your computer.

Please tell us about the hardware

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

and about the software

- is the computer running in UEFI or BIOS mode?
- version of Windows
- version of Ubuntu

-0-

- What system was running before the problems started?

- Did you move the head (left edge in the graphics) of the Ubuntu root partition with gparted? That would confuse the bootloader grub, and in that case you need to reinstall the bootloader.

- How did you install Windows?

- Did you check with md5sum that the downloaded iso file is good (for Windows, for Ubuntu)?

- How did you create the DVD/USB boot drive (for Windows, for Ubuntu)?

- Did you try in another computer, if the DVD disk / USB boot drive works?

---

### Post by gtozzi on 2015-12-20
Also, before buying a new USB, try to erase and recreate from scratch the one you have (assuming you do not have important data inside of it).

---

### Post by jonathan104 on 2015-12-20
It's a Dell xps l502x 
Cpu is I5 
Gpu is gtx 525m
4gb of ram
Not sure about the WiFi chip

Running in bios mode (I think)
Ubuntu 14.04
I didn't install Windows yet but I had a bootable USB drive with it on, which now has Ubuntu on it

Ok I will do thanks

---

### Post by sudodus on 2015-12-20
This computer should work well with standard Ubuntu as well as the other flavours (Kubuntu, Lubuntu ... Xubuntu). You might need the boot option nomodeset for Ubuntu's basic graphics to work, and then install a proprietary nvidia driver. See this link (scroll to the post about boot options and find links for detailed descriptions)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

Do you know how to boot it from USB? Probably you should press a function key, for example F12 (but it could be another one, sometime information about it flashes quickly early during boot).

If you want to dual boot with Windows and Ubuntu, it is better to start installing Windows, and then install Ubuntu, because Windows overwrites the bootloader for Ubuntu. Which version of Windows are you intending to install?

---

### Post by jonathan104 on 2015-12-20
I know how, it's just not working when I select it so I'll use a different USB

---

### Post by jonathan104 on 2015-12-20
How can I whipe my partition if I can't boot to an OS?

---

### Post by sudodus on 2015-12-20
The pendrive might be bad, but I suggest that you try again with another tool, for example mkusb. But first you should

- check with md5sum that the downloaded iso file is good (for Windows, for Ubuntu) - see [UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

- check that the pendrive is recognized as a mass storage device, /dev/sdx, where x is the drive letter a, b, c ... Please post the output of

```
sudo lsblk -fm
```

and then get and try [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by jonathan104 on 2015-12-20
I can't get onto the OS so I can't get on the terminal

---

### Post by sudodus on 2015-12-20
> **jonathan104 said:**
> How can I whipe my partition if I can't boot to an OS?

You need another computer in order to get a pendrive that works. Can you borrow a computer? It could be any kind of computer, with linux, Windows or MacOS, that can connect to the internet and has working USB ports.

---

### Post by jonathan104 on 2015-12-20
Yeah I can but not until tomorrow so

---

### Post by sudodus on 2015-12-20
Come back with questions, when you know what computer you will use :-)

---

### Post by Image on 2015-12-23
Jonathan, have you disabled UEFI? Are you using the USB 2.0 port or a 3.0? If 3 then I suggest using the 2.0.
Also format the usb stick FAT32 and make it bootable. Boot to it, does it boot from USB now?

---

