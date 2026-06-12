---
title: "Why will many Ubuntu and linux distros only boot from cd/dvd and not a usb stick?"
date: 2014-12-18
forum: General Help
---

### Post by ultragamer2 on 2014-12-18
The standard ubuntu distro is one that seems to boot fine from a usb stick but the majority of other distros and other versions of ubuntu will not.

I am downloading the iso and then using unetbootin and always often try LILO as well.

When you try to boot usually you just end up with an error that leaves you in a command terminal like dos.

Is there any way to boot these linux distros from a usb stick (for a noob).

They always boot from cd/dvd fine but with my dvd connected to a pci card this isn't an option.

---

### Post by sudodus on 2014-12-18
Most linux distros can be booted from USB pendrives. Some of them need special tools for it, some work with standard tools like ***Unetbootin***.

If the iso file is a ***hybrid iso file*** (treated with isohybrid), it can be cloned easily to a bootable USB pendrive using ***mkusb***. If necessary, treat it yourself

```
isohybrid filename.iso
```

But there are problems with some computers, particularly very old computers, to boot from USB. Other computers boot, but have errors with drivers, that the [automatically] selected driver does not work well with the hardware, for example graphics chip or wifi chip.

See these links for more details

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

[Ubuntu Forums tutorial "Howto make USB boot drives with mkusb"]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by ultragamer2 on 2014-12-18
Thanks, often I am trying to make a bootable usb flash drive with windows, what are the best tools to use with windows when unetbootin doesn't work?

---

### Post by sudodus on 2014-12-18
[Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") in Windows corresponds to mkusb to make USB pendrives boot Ubuntu and other linux operating systems.

However, it also needs hybrid iso files, and if the iso file needs treatment, I know it works with ***isohybrid*** in linux, but I don't know any corresponding Windows tool. Probably you can find one via the internet.

I made a list of distros that work well with ***mkusb*** (and ***Win32 Disk Imager***). See this link

[https://help.ubuntu.com/community/mkusb/v9#Simple_to_test_mkusb_9_in_linux_distros.2C_which_do_not_manage_an_Ubuntu_PPA](https://help.ubuntu.com/community/mkusb/v9#Simple_to_test_mkusb_9_in_linux_distros.2C_which_do_not_manage_an_Ubuntu_PPA)

---

### Post by monkeybrain20122 on 2014-12-18
> **ultragamer2 said:**
> Thanks, often I am trying to make a bootable usb flash drive with windows, what are the best tools to use with windows when unetbootin doesn't work?

Why Windows? In Ubuntu Multisystem always works for all the distros I have tried (*buntu, Fedora, Centos, debian, OpenSusy and others...)
[http://liveusb.info/dotclear/index.php?pages/install](http://liveusb.info/dotclear/index.php?pages/install)

---

### Post by ultragamer2 on 2014-12-18
Ok thanks, I suppose I can look into making the usb stick in ubuntu. I'm not very experienced with terminal commands though.

---

### Post by monkeybrain20122 on 2014-12-18
> Ok thanks, I suppose I can look into making the usb stick in ubuntu. I'm not very experienced with terminal commands though. 		 	  	 		 		

multisystem has a nice, easy to use gui.

---

### Post by ultragamer2 on 2014-12-18
I just got it to work using the disks program in Ubuntu, I "restored" an iso image to a usb flash drive and it booted, I'm not sure yet if it will work with all distros but it worked with one.

---

### Post by sudodus on 2014-12-18
***Disks*** works similar to mkusb and Win32 Disk Imager, it copies/clones/flashes the iso image to the drive, so it works with hybrid iso files.

---

### Post by xubu2 on 2014-12-18
Unetbootin ain't what it used to be :(
Has worked for a long time but not anymore now.

I use **usb-creator-gtk** now and it works fine.

---

### Post by sgage on 2014-12-19
I, too, often have problems with Unetbootin these days. I've never tried Multisystem. On the Windows side, I've had good luck with LinuxLoader (LILO): [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

It maintains a database of many distros, and can make a bootable USB when nothing else seems to work for me.

---

### Post by sudodus on 2014-12-19
Using ***mkusb*** and ***Win32 Disk Imager*** makes the booting independent of tweaks in the tool (like in Unetbootin and the Ubuntu Startup Disk Creator). The only thing you need is a hybrid iso file. The Ubuntu flavours come with such files and you can make it 'hybrid' yourself in Ubuntu for other distros. So the method is very reliable and independent of versions and distros.

The only drawback is that there is no persistence (except with openSUSE, that uses UDF instead of the ISO9660 file system), but persistence is not needed for installation and repair, which are the main usages of the install iso files.

---

### Post by mcduck on 2014-12-19
I just have one USB drive aroubd with Grub2 installed on it, and then I drop any .iso fles I want and add them to the drive's grub.cfg by hand (as in "copypaste existing .iso boot entry and change name of the iso file). Works pretty well at least for all ubuntu-based, haven't tried too many other distros but probbaly they'd work pretty well although some might require different settings in grub.cfg.

Still pretty nice setup as I can add and remove as many iso files as I want, don't need any special tools, and can do it from any computer or OS as long as it's able to read a normal FAT-formatted USB stick.

---

### Post by Mark Phelps on 2014-12-19
> what are the best tools to use with windows when unetbootin doesn't work? I've used the Universal USB Installer from pendrivelinux.com many times and had it work every time.

---

### Post by kurt18947 on 2014-12-20
I have one machine - 2008-2009 vintage Gigabyte AMD 785 chipset.  It will only boot a live USB if the USB drive has been formatted with windows.  Other machines will boot fine with a flash drive formatted with Gparted, this one machine will not.  It doesn't seem to be a common AMD problem - I have two other AMD machines, one older one newer that both boot fine from any live USB I've tried.

---

### Post by Yellow Pasque on 2014-12-20
I always use dd command (use at your own risk because it's easy to erase data you don't want to).

>  It will only boot a live USB if the USB drive has been formatted with windows. Other machines will boot fine with a flash drive formatted with Gparted, this one machine will not.
What are you formatting it as in gparted? FAT32?

---

### Post by Bucky Ball on 2014-12-20
> **Temüjin said:**
> I always use dd command (use at your own risk because it's easy to erase data you don't want to).


What are you formatting it as in gparted? FAT32?

Which reminds me, it is best to format the USB before using any USB creator. With Unetbootin, for instance, it appears NOT to clear the USB prior to dumping the ISO on it. Therefore, if you have a file on the USB already it will still be there when Unetbootin has done its job. Try to boot from the stick and confusion. It has happened to me in the past.

But if other OSs are working for you, guess you're doing it right. :-k

So if you're not doing it already, wipe that USB with a reformat prior to using the USB creator of choice. ;)

---

### Post by sudodus on 2014-12-20
> **Bucky Ball said:**
> ...

So if you're not doing it already, wipe that USB with a reformat prior to using the USB creator of choice. ;)

+1: concerning Unetbootin, the Startup Disk Creator and similar tools.

-1: but if you are using mkusb, Win32 Disk Imager (and dd, the 'disk destroyer'), they will overwrite also the boot loader, partition table and the file system(s) in the copying/cloning/flashing process, so the pendrive's function will be independent of wiping the drive before. Instead it in a good idea to wipe the drive *afterwards* in order to re-use it as a standard data drive with a FAT32 file system.

---

### Post by kurt18947 on 2014-12-21
> **Temüjin said:**
> I always use dd command (use at your own risk because it's easy to erase data you don't want to).


What are you formatting it as in gparted? FAT32?

Yes, FAT32 with boot flag set. A USB prepared with Gparted and a USB formatted with Windows appear identical but *something* is different. Quick format under Windows is adequate, a full format is not required. I didn't spend a lot of time on the issue because it appears to be a one-off issue with this particular model BIOS/motherboard..

---

