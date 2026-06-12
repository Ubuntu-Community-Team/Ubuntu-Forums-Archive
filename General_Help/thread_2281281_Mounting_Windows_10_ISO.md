---
title: "Mounting Windows 10 ISO"
date: 2015-06-05
forum: General Help
---

### Post by Ansley on 2015-06-05
I am a very new user of Kubuntu, and only switched over due to buying a computer that had a faulty Windows OS. I want to install and try out the Windows 10 technical preview, and have the iso downloaded, but I cannot get it mounted. All the methods I've looked up failed, and I do not have a USB with enough storage for the OS. Help?

---

### Post by alex288 on 2015-06-05
If you want to use Virtualbox to install Windows 10 as a Guest operating system, you could do that like I have.
If you mean installing it in a partition with kubuntu that may be some trouble due to the fact that the windows installer overwrites the GRUB boot loader that kubuntu uses.
You could overwrite kubuntu with Windows 10 if you want, but as Windows 10 is in beta and it is unstable something could go wrong, so I would rather use Virtualbox.
It's up to you for what option you want

---

### Post by Ansley on 2015-06-06
I want to overwrite it. I have friends that have used it primarily no issue, I miss the wide compatibility windows 10 has. Again, I can't get it to mount and need instructions

---

### Post by SeijiSensei on 2015-06-06
Usually you just use the mount command like this:
```
sudo mount -o loop -t iso9660 /path/to/image.iso /mnt
```
Nowadays Linux can usually determine the type of filesystem automatically, but for good measure I've included the "-t iso9660" parameter to be sure.

I'm not really clear on what you're trying to do though.  Just mounting the disk will let you browse the files, but it won't let you install Windows at all.  If you're just doing this to try out Windows, then I'd follow alex288's suggestion that you install [VirtualBox]("http://www.virtualbox.org/") and create a Windows 10 virtual machine running as a "guest" under Linux.

If you want to boot the image directly, you'll need to burn it to a DVD or create a bootable USB device.

---

### Post by yancek on 2015-06-06
You haven't given much information but I think the suggestion above to use Virtualbox to test is a good idea.  It is possible to loop mount the windows iso file and boot it but there are some caveats.  You would need to loop mount the windows iso in Kubuntu, then create an ntfs formatted partition on your hard drive and copy the extracted windows iso to that partition and put a correct entry in the grub.cfg file for a one time boot of the windows extracted iso.  The link below explains this method.  They refer to using a usb drive but the same method works when using a separate partition on a hard drive for the windows extracted iso.  You have not indicated how many physical hard drives you have.  You can't install windows to an external usb drive as you will get this message if you try:   "windows setup does not support configuration or installation to a disk connected through usb or IEEE 1394 ports.  I'm not sure if it will work trying to install from a partition on an internal drive to another partition on that same drive.  Here's the link.  When it refers to a flash drive just change that to the hard drive partition.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

With your apparently limited experience, I think you will find after reading the info at this link that VirtualBox is a better option.

---

### Post by buzzingrobot on 2015-06-06
I'm not certain, but I believe the OP will need to boot from the ISO to install Windows 10.  There is no "live" mode. The VM approach will work, as well. if the OP wants to go that way.

I've never been able to burn the iso to a USB stick and get it to boot.  Burning it to a DVD works fine, and that's what I'd recommend. (It's 3.5 gigs).

A large number of updates will be available after installation.  Users can choose to be in the "Slow" or the "Fast" channel of the Insiders program.  Those in the Fast channel  see more rapid, more frequent, buggier upgrades. 

Depending on which build the OP is installing, the install may stall out if the OP signs in with a Microsoft account rather than create a local account.

---

### Post by yancek on 2015-06-06
> I'm not certain, but I believe the OP will need to boot from the ISO to install Windows 10.

The method suggested at the link I posted above of loop mounting the windows iso and copying it to a flash drive or hard drive partition will work   The Disk Imager didn't work as the iso file was too large so loop mounting was necessary.  Tried this and was surprised that the method worked but then I haven't really used windows for over 10 years.  The problem is someone not understanding the terminology or not exactly following the instructions will have problems as every step needs to be done and done correctly and in order.

Much easier to use VirtualBox or a DVD if possible.

---

### Post by alex288 on 2015-06-06
If you want to make a Windows 10 ISO, here's some steps with dd.
First find out what /dev/sd* is on. For example mine would be /dev/sdb (don't include partition number)
Type in a terminal sudo dd if=/home/alex/Windows10.iso of=/dev/sdb bs=1M
Be sure to replace the /home/alex/Windows10.iso and /dev/sdb with what yours is.
It may look like nothings happening. It is happening, just doesn't show you any progress until you finish. Then, take your USB and boot up your machine. Press any ways to get to the boot menu on your BIOS (or UEFI) on mine it is F9 and select your USB. It should have the Windows Logo then some white spinning dots. Press Next then Custom then delete all partitions. Create a new one with all the space, and click next. Then install windows like normal.

---

