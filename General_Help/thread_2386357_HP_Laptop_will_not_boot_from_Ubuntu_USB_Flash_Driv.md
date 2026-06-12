---
title: "HP Laptop will not boot from Ubuntu USB Flash Drive"
date: 2018-03-04
forum: General Help
---

### Post by georgef1600 on 2018-03-04
I put the ubuntu iso file on a 16G usb flash drive.  I then successfully booted off that flash drive, then clicked on "Install Ubuntu".   I installed Ubuntu on a 32G usb flash drive.  I can successfully boot my Dell desktop machine from the 32G flash drive and ubuntu works perfect.   However my newer HP Pavilion laptop refused to boot off the 32G flash drive.   

I do have the boot order on the HP laptop setup to try the USB drive first.   The HP will boot off the original 16G flash drive with the ubuntu iso file so I know the HP is looking for a boot device on the usb port.  However every time I try to boot off the 32G Ubuntu installed flash drive the HP machine will look at the flash drive then boots under windows.

Any ideas?
Thanks.

---

### Post by kerry_s on 2018-03-04
did you install leagacy or uefi on the 32gb ?

whats your bios set at? pressing f9 at boot should be the device selection

i have 2012 hp pavilion g6

---

### Post by georgef1600 on 2018-03-04
How do I know if I"m installing Leagacy or UEFI on the 32gb?

When pressing F9 I at boot I do get the device selection, it appears the HP is looks at the usb flash drive and doesn't seen what its looking for then starts booting Windows.

---

### Post by kerry_s on 2018-03-04
try switching it to legacy & see if it boots.

what was the old laptop running? i think up to win 7 used legacy, after 7 was uefi.

---

### Post by georgef1600 on 2018-03-04
I tried setting bios to legacy. I also made sure that USB was the first device in the boot order under the legacy setting.  However the "fine" print says that priority is given to the uefi boot order (where I also have USB the first device in the boot order).....about to pull out my hair......

---

### Post by kerry_s on 2018-03-04
when legacy is turned on uefi is disabled.
make sure you put everything back the way it was, so as not to mess up your windows.

i'm thinking what you did was installed on the usb, but you put the boot loader on that other laptop.

---

### Post by sudodus on 2018-03-05
> **kerry_s said:**
> when legacy is turned on uefi is disabled.
make sure you put everything back the way it was, so as not to mess up your windows.

i'm thinking what you did was installed on the usb, but you put the boot loader on that other laptop.

+1

In UEFI mode, the ESP partition (which is/contains the UEFI bootloader) will be put on the first drive **/dev/sda**, typically an internal drive. You can make the installer put it on the external drive (USB pendrive) by *unplugging/disconnecting/disabling the internal drive*.

There is a detailed description at the following link,

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

---

### Post by HermanAB on 2018-03-05
Eh?  You installed the disk on a Dell and now you want to run it on an HP?  

That won't work.

---

### Post by kerry_s on 2018-03-05
> **HermanAB said:**
> Eh?  You installed the disk on a Dell and now you want to run it on an HP?  

That won't work.

no, he installed to usb using a dell. the problem is unless you select custom partitioning you won't see the option to chose where to put the boot loader, so the boot loader will go to the main drive, in this case on the dell.

any way he's going to have to install a grub boot on the usb to make it complete.

---

### Post by sudodus on 2018-03-05
> **HermanAB said:**
> Eh?  You installed the disk on a Dell and now you want to run it on an HP?  

That won't work.

I have made several installed systems in USB drives, that are portable between Dell and HP computers. (I avoid proprietary drivers.)

---

### Post by HermanAB on 2018-03-05
Yes, but... by installing on the Dell, you will have the wrong device drivers for a whole lot of things.

---

### Post by sudodus on 2018-03-05
@HermanAB,

If the two computers are 'too different', yes, there can be problems with an installed system. (It may not be portable between the computers.)

In this case, it might be better with a persistent live system according to the following links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by kerry_s on 2018-03-05
what ? is it like that now ?

my understanding was that hardware is supported by the kernel & ubuntu uses a generic kernel to support the widest range of devices
so it should not matter what the os is booting on, it most likely will just work, if the device is linux friendly of course & not to new.

---

### Post by sudodus on 2018-03-05
> **kerry_s said:**
> what ? is it like that now ?

my understanding was that hardware is supported by the kernel & ubuntu uses a generic kernel to support the widest range of devices
so it should not matter what the os is booting on, it most likely will just work, if the device is linux friendly of course & not to new.

Yes, in most cases an installed system will just work. But there are exceptions, for example if one of the computers needs a proprietary driver for graphics or wifi, and the other computer does not work with that proprietary driver.

---

### Post by kerry_s on 2018-03-05
drivers are only loaded when the devices is available, that includes gpu & wifi
you can have the drivers installed & not used on other systems
you can add additional drivers, on any system you boot up on

that's why there are fall back settings

---

