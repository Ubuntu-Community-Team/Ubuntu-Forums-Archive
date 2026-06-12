---
title: "Can't boot Ubuntu iso from USB stick"
date: 2012-12-29
forum: General Help
---

### Post by groundnut on 2012-12-29
I am trying to boot an Ubuntu iso from an USB stick.
My BIOS is from American Megatrends (1985-2005).
There are three boot devices mentioned:
1=CD/DVD, 2=hard drive, 3=realtek boot agent.
At each number I can use one of these 3 options or disabled.
No other options are mentioned.
Also mentioned is Boot from other device, this is set to yes, the other option is no.

How can I boot from USB?

---

### Post by Mark Phelps on 2012-12-29
You can't boot from an ISO file; instead, you have to EXPAND the ISO file onto the USB stick.  Then, you will be able to boot from it.

---

### Post by cwsnyder on 2012-12-29
Your BIOS may not want to boot from USB even if it is installed properly by unetbootin (Windows or Linux executable).  In that case, you can download [http://download.plop.at/files/bootmngr/plpbt-5.0.14.zip](http://download.plop.at/files/bootmngr/plpbt-5.0.14.zip), unzip and find the plbt.iso and burn it to a CD with Brasero (burn disk image).  As you can read from the Documentation at [http://www.plop.at/en/bootmanager/index.html](http://www.plop.at/en/bootmanager/index.html) , the Plop Linux Boot manager, after you boot from the CD, will allow you to boot from a properly prepared USB memory stick even if your BIOS doesn't support that function.  You _can_ write Plop to the hard disk, but read some warnings at [http://www.webupd8.org/2010/02/plop-boot-manager-lets-you-boot-from.html](http://www.webupd8.org/2010/02/plop-boot-manager-lets-you-boot-from.html) near the bottom of the article.  One big limitation is that it may not support USB keyboards.

---

### Post by Topsiho on 2012-12-29
Booting from an USB-stick is a recent feature of computers. Probably your computer is too old to have this possibility. I have a laptop from 2005 which doesn't boot from an USB-stick.

Topsiho

---

### Post by C.S.Cameron on 2012-12-29
Check if your flash drive shows up as a hard drive in BIOS, if so set it as first hard drive.

If you want to boot a Ubuntu ISO file you need to install grub2, see MultiBootUSB etc.

Easier to install to USB stick using Startup Disk Creator or UNetbootin.

---

### Post by efflandt on 2012-12-29
It is tough to say exactly when the ability to boot from USB became common.  My old HP desktop with American Megatrends (AMI) BIOS from 2004 could, but a low end laptop from 2005 could not. Note that the USB device would need to be connected for CMOS setup to even give you that choice.

With the USB connected, see what choices you have for boot devices when pressing the hotkey for that (which I think ia Esc key for AMI BIOS).

---

### Post by Gremlinzzz on 2012-12-29
:popcorn:I have a new notebook and have to put USB stick in while computers on,then reboot.

---

### Post by groundnut on 2012-12-30
Apparently the USB stick has to be connected while booting in order to show up as a possibility in the BIOS Boot sequence. Now it does.
I have now set USB as the first choice for booting.
So far so good.

However now I get the following message:
Invalid system disk
Replace the disk,
and then press any key

So what is the next step?

---

### Post by oldfred on 2012-12-30
So how did you install it to flash drive? You do not just copy it as posted above by  Mark Phelps.

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

    
       [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by groundnut on 2013-01-02
I simply copied the ISO file to the USB stick.

What does Mark Phelps mean by EXPAND the ISO file onto the USB stick?
Is that different from UNebootin?
Is it preferable to use UNebootin or USB creator?

---

### Post by oldfred on 2013-01-02
If you just copy ISO as one large file it will not be bootable.

If you use an installer like unetbootin, USB creator, or pendrive then those applications extract the ISO into several folders & files and create a bootable device.

Some have posted issues with one installer or the other. Also some have issues with different brands of flash drives or USB3 ports that some BIOS do not support for booting. Your results may vary.

       How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)

   Usb installer from Windows
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

            Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by Calinou on 2013-01-02
> **groundnut said:**
> I simply copied the ISO file to the USB stick.

What does Mark Phelps mean by EXPAND the ISO file onto the USB stick?
Is that different from UNebootin?
Is it preferable to use UNebootin or USB creator?

Copying the ISO to the USB stick will not work.

Use Unetbootin. It supports a lot of Linux distros (though it is optimized for Ubuntu and Ubuntu-based distros), is open source and works on all platforms.

---

### Post by cwsnyder on 2013-01-03
There are basically 2 different methods of installing an .iso file to a USB thumb drive:
1)Simply install the .iso as a Live media with the **initread** and **squashfs** compressed RAMdisk and file system and the system is never updated or at least only when re-mastered, or
2)Full install as if to an operating hard drive with the file system uncompressed.

Unetbootin and USB Creator create the first type.  Using the Install to Disk option from within the operating system creates the second type.

The first type is usually a smaller install, but starts more slowly as it needs to decompress the files for use during the boot process.

---

### Post by groundnut on 2013-01-03
Problem solved!
Thank you very much guys.

I installed UNetbootin from the Ubuntu Software Center.

---

### Post by Eugene King on 2013-01-03
as a note 

unless you made it a permanent installation it won't save anything you did.......

---

### Post by C.S.Cameron on 2013-01-03
> **Eugene King said:**
> as a note 

unless you made it a permanent installation it won't save anything you did.......

UNetbootin now makes Persistent USB installs that will save up to 4GB of data in a casper-rw file.
You can make a casper-rw and home-rw ext partition of unlimited size.

---

### Post by Eugene King on 2013-01-03
edit, wrong thread......

---

