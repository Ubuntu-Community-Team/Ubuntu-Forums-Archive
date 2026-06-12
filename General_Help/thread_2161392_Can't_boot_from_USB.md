---
title: "Can't boot from USB"
date: 2013-07-10
forum: General Help
---

### Post by Cotopaxi on 2013-07-10
Can't boot from USB

Hi,

I have been booting from USB devices for more then a year now but, after a system update, I can't boot from there any more. When I get into the BIOS into “choose temporary boot device” the USB stick is not displayed.

The 0S version is 12.04.

The Laptop is a Lenovo Edge E325 and does not have a DVD.

What I have tried so far:
I have modified the EFI / legacy boot,
I have deleted the FAT 32 partitions on the different pens, & created new ones,
I have used Unetbootin to install the ISO file on the pen,
etc. etc. etc.

Now,

Can anyone please give me step by step instructions on how to proceed?

How should I set my BIOS settings?

Is there a command line instruction for installing the system from an ISO file to the pen? This way I would see the error messages.

Any other idea?

Thanks for your help!

---

### Post by chenzero on 2013-07-10
first,need to check that the USB/removable device is set to be the 1st boot device in BIOS. 
if &#8220;choose temporary boot device&#8221; is not displayed, I guess that option is changed to other name because most BIOS now support boot from USB.

please try to create a boot USB by Ubuntu self include tool --- "Startup disk Creator"( from menu: Application >> System Tools >> Adminstartion,  or run from command line: usb-creator-gtk )
whether also can not boot ?

---

### Post by Cotopaxi on 2013-07-12
Hi Chenzero,

Thank you for your reply.

In BIOS is selected "USB HDD" as the first boot device. But anyhow I do not get offered the pen drive under "temporary boot devices", it only shows me the laptop's Harddisk.
With the "Startup Disk Creator" I have tried several times and previously it DID work, but after an upgrade it stopped working.

I do not know if "Statup Disk Creator" is not managing to make the USB stick bootable or if something went wrong with my BIOS.

I have also tried the command:

> sudo dd if=/home/no/AC_Software/Kubuntu/kubuntu-12.04.1-desktop-amd64.img of=/dev/sdc bs=1M

and also no luck.

What I plan to do is to prepare a Windows USB stick on another computer and see if that might work. If that does not work than I am sure that I have a problem with my BIOS.

Anyhow, thanks very much indeed for your help chenzero!

---

### Post by ana551 on 2013-07-12
check whether the usb is recognized when connected in any other system i.e is the usb bootable.....because i think setting usb as first preference should have solved the issue

---

### Post by C.S.Cameron on 2013-07-12
Are you doing a Full install to pendrive or a Persistent install?
With a Persistent install it is recommended not to do an Update as it quickly fills persistence and not to Upgrade as the kernel is part of a read only file.

If you are doing a Full install just treat the flash drive just like an internal drive, and unplug your regular internal drive before installing to the USB.

---

