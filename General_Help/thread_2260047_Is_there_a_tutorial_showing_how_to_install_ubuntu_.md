---
title: "Is there a tutorial showing how to install ubuntu on a flash drive?"
date: 2015-01-08
forum: General Help
---

### Post by yeto on 2015-01-08
Is there a tutorial showing how to install ubuntu on a flash drive? Would the easiest way be to use pendrivelinux?

Thanks,
yeto

---

### Post by nerdtron on 2015-01-09
Depends on what you say "install". Are you pertaining to a FULL install on Ubuntu on a flash drive or just a LIVE CD version only?

---

### Post by mastablasta on 2015-01-09
creating bootable stick on windows: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
or unetbootin or linuxliveusb

creating bootable stick on Ubuntu: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

if you want to fully install - then it's juts like a normal disk install only put grub on USB

---

### Post by sudodus on 2015-01-09
You find a lot of tips in the following link and links from it

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by yeto on 2015-01-09
I would like for the whole Ubuntu OS to be on the flash drive. I don't want to install Ubuntu on my hard drive. I would just one time boot from the flash drive when I want to use Ubuntu. My current OS is Windows 7.

Would the following link be the best for what I am trying to accomplish?
[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

---

### Post by sudodus on 2015-01-09
I see. But there are several alternatives how to run Ubuntu from a pendrive. *nerdtron* asked before and I ask again: What kind of installation do you want? Maybe the following link will help you see what we are asking: do you want a live, persistent live or installed system?
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by yancek on 2015-01-09
Pendrive Linux will put Ubuntu as well as other Linux systems on a flash drive as a Live CD.  This method will allow you to boot and use the system from the flash drive.  You will not be able to save any changes, download and save any software to be available on reboot.  If that's what you want, then pendrivelinux will do the job.

---

### Post by yeto on 2015-01-09
> **yancek said:**
> Pendrive Linux will put Ubuntu as well as other Linux systems on a flash drive as a Live CD.  This method will allow you to boot and use the system from the flash drive.  You will not be able to save any changes, download and save any software to be available on reboot.  If that's what you want, then pendrivelinux will do the job.

First of all let me say I am sorry that I do not know how to ask my question properly and I thank all of you for trying to help.

I don't think I am interested in other Linux systems just Ubuntu. I would like to be able to save changes and downloads (to the flash drive) that would be available the next time I boot the flash drive. I don't want to install anything on my internal laptop hard drive.

So is a persistent install to a flash drive what I want?

Thanks,
yeto

---

### Post by sudodus on 2015-01-09
Yes, that would be the easiest way to get what you want, a persistent live pendrive.

I recommend the version 14.04.1 LTS (long time support).

 If you want to run it in 64-bit computers (including UEFI), download Ubuntu 64-bit alias amd64 iso file. If you want to run it also in 32-bit computers, download a 32-bit alias i386 iso file (and I would suggest a lighter desktop environment, Xubuntu or Lubuntu 32-bit).

I recommend that you use the Ubuntu ***Startup Disk Creator*** or ***Unetbootin*** according to the descriptions in this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

-o-

If you want to run the pendrive in 32-bit computers and 64-bit computers including UEFI, download a compressed image file according to the following [URL="http://ubuntuforums.org/showthread.php?t=2259682"]

tutorial about One pendrive for all (Intel/AMD) PC computers[/URL]. 

or make it yourself from the iso files according to the recipe.

---

### Post by yeto on 2015-01-09
For what I am trying to accomplish would this be the best website? I would like to keep this as simple as possible as I am new to Linux.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Thanks,
yeto

---

### Post by sudodus on 2015-01-09
Different descriptions suit different people. Maybe the Sourceforce page is the best one for you. Another alternative is [Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

---

### Post by nerdtron on 2015-01-09
Actually Unetbootin will just install a LIVE CD version to your flash drive. This will be bootable but this is not a FULL install yet. You need another flash drive, preferably a larger one that will install the full Ubuntu.

Basically these steps:
1. Use Unetbootin to setup Ubuntu on flash drive. This is a bootable installer version.
2. Boot on the flash drive you just created.
3. Insert another flash drive (preferably 8GB and up).
4. Click the ubuntu installer on the desktop and start installing to the larger flash drive.

NOTE: it would be better if you this while internal hard drives are disconnected. This is to prevent any damage on the internal drives.

Also, youtube is you friend. Here's a link for the steps above. [https://www.youtube.com/watch?v=lIF8e_5F9B4](https://www.youtube.com/watch?v=lIF8e_5F9B4)

---

### Post by C.S.Cameron on 2015-01-10
Unetbootin is probably the easiest way to make a persistent Ubuntu flash drive, but has an ugly start screen.

If you want to improve things later there are a lot of things you can do:

Remove Try/Install screen.
Add yourself as a User with password.
Increase the 4GB persistence file limit.
Make a Full install flash drive.
Encrypt the drive or home folder. 
Make a Multi boot flash drive.
Increase speed by running in RAM.
To name a few.

A UNetbootin install is a good starting point, (a lot of people have complained about the Pendrivelinux installer.

---

### Post by xmbwd on 2015-01-10
Unetbootin is a good option.  I also use [Multisystem]("http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/") for persistent USB Live Systems.  One nice feature of Multisystem is that you can put multiple distros and/or utilities like Boot Repair -- all on the same USB.  All available at boot.  Here is a [video]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=14&cad=rja&uact=8&ved=0CIUBELcCMA0&url=http%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3Duo24WH3Uc2E&ei=Yc2wVNrmKsXioAS9goKoAQ&usg=AFQjCNHqc93mGifqJ0wTm51n6_WBwYproQ&sig2=OJ1dA1ECayrDdmi7ZafEmA"). 

Oh, and if you get into Ubuntu and want to make a permanent install.  [SystemBack]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&uact=8&ved=0CCAQFjAA&url=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fsystemback%2F&ei=tM2wVMi-Do_aoASS24GIDQ&usg=AFQjCNFEvAGNWGWvGFQQKFtrLsm40GKDTQ&sig2=x9GcJ3LxdSrHM5b-0YafCw") is an awesome tool that create a Live System.

---

### Post by yeto on 2015-01-10
Wow, thanks to all who have taken time out of your day to post. I really appreciate your help.

Kind regards,
yeto

---

### Post by sudodus on 2015-01-10
You are welcome. Please go ahead, and report your results, whatever they are :-)

---

### Post by yeto on 2015-01-10
> **sudodus said:**
> You are welcome. Please go ahead, and report your results, whatever they are :-)

I started by trying to download to a SanDisk Cruzer Glide 8GB formatted to FAT32. Unetbootin would not recognize this flash drive. Next I formatted an ADATA 8GB flash drive to FAT32 an Unetbootin DID recognize this drive. Unetbootin gave me the option to select 14.04_Live and the download was just under 1GB in size. Next Unetbootin automatically extracted the files and set up persistence. I did the one-time boot sequence and Ubuntu booted with no problems. I do have some questions though.

1) On the desktop is a file/folder/icon or something that says Install Ubuntu 14.04.1 LTS. Do I click on this an install?

2) Also, can I put another/different flash drive in a different USB port and make a backup copy of the original Ubuntu?

3) And, is there an "Ubuntu software store" that I could visit to see what software is available for Ubuntu?

Again, thanks for all the help. So far so good. I think I am going to really like Ubuntu.

Kind regards,
yeto

---

### Post by nerdtron on 2015-01-10
1. Yes. That will take you to the Ubuntu installer. Note that you can't install Ubuntu on the flash drive your are currently using as installer. You need another flash drive on which you will install the full version of Ubuntu.

2. What do you mean? Your unetbootin install won't be erased if you install ubuntu to another flash drive. You can install to as many flash drives as you want.

3. It's called Ubuntu Software Center. Even before you install Ubuntu, while you are in Live, you can open it and see available software, both free and paid.

---

### Post by C.S.Cameron on 2015-01-10
2. There are several ways to clone your flash drive:
    a) dd is recommended for experienced users, you can have disastrous results if you make an error.
    b) Clonezilla is a bit more user friendly, but not foolproof.
Do your own research on either of these before using, probably best to unplug your internal hard drive first.

---

### Post by sudodus on 2015-01-11
> **C.S.Cameron said:**
> 2. There are several ways to clone your flash drive:
    a) dd is recommended for experienced users, you can have disastrous results if you make an error.
    b) Clonezilla is a bit more user friendly, but not foolproof.
Do your own research on either of these before using, probably best to unplug your internal hard drive first.

+1

---

### Post by yeto on 2015-01-11
> **nerdtron said:**
> 1. Yes. That will take you to the Ubuntu installer. Note that you can't install Ubuntu on the flash drive your are currently using as installer. You need another flash drive on which you will install the full version of Ubuntu.

Right now when I boot the flash drive I have a desk top. It has Firefox, LibreOffice, etc. Are you saying that is not the full version of Ubuntu? In other words, 14.04 Live is not a full version? Would not 14.04.1 LTS be a different full version of Ubuntu and if this is the case can I not just click on that desktop icon and it will upgrade 14.04 Live to 14.04.1 LTS?

> 2. What do you mean? Your unetbootin install won't be erased if you install ubuntu to another flash drive. You can install to as many flash drives as you want.

I just want to drag the files from one flash drive to a different flash drive so I will have a backup copy. Will this not work? If I just do a new install to a flash drive I won't have the saved information I created on the original flash drive. Is this not possible?

Please forgive me. English is my second language and I hope my questions make sense.

Kind regards,
yeto

---

### Post by nerdtron on 2015-01-11
> In other words, 14.04 Live is not a full version? Would not 14.04.1 LTS  be a different full version of Ubuntu and if this is the case can I not  just click on that desktop icon and it will upgrade 14.04 Live to  14.04.1 LTS?
A Live version is running only on a virtual filesystem on the flash drive (it will be slower). If you did not configured persistence, you changes to the OS will not be saved when you reboot, If you configured persistence, the max is 4GB. This type of install is designed mainly for testing and to start the Full Install.
A Full install of Ubuntu does not have the above limitations, it runs like a normal Operating System, you can install and update and upgrade as usual. You can upgrade to 14.04.1 LTS.

> I just want to drag the files from one flash drive to a different flash  drive so I will have a backup copy. Will this not work? If I just do a  new install to a flash drive I won't have the saved information I  created on the original flash drive. Is this not possible? 

I don't think so as things can get complicated. Also, are we talking about the Live install here or the Full install?

---

### Post by yeto on 2015-01-11
> A Live version is running only on a virtual filesystem on the flash  drive (it will be slower). If you did not configured persistence, you  changes to the OS will not be saved when you reboot, If you configured  persistence, the max is 4GB. This type of install is designed mainly for  testing and to start the Full Install.
A Full install of Ubuntu does not have the above limitations, it runs  like a normal Operating System, you can install and update and upgrade  as usual. You can upgrade to 14.04.1 LTS.

So if I click on the "Install Ubuntu 14.04.1 LTS Icon" will I get the option to install on a different flash drive? I do not want to install anything on my internal hard drive. Also, how is 14.04.1 LTS different versus 14.04 Live? What will I get with 14.04.1 LTS that I am not getting with 14.04 Live?


> I don't think so as things can get complicated. Also, are we talking about the Live install here or the Full install?

It is a little disconcerting related to all the warnings to disconnect the internal hard drive before attempting any type of backup. Would it be best to just drag and drop, say for example, like word doc files and the such and don't worry about backing up the OS as I guess it can always be re-downloaded? Also, what would be the difference backing up the Live install versus the Full install?

Again, sorry for all the questions and bad English. I hope you can understand what I am asking as I am really confused. Live "seems" to be accomplishing what I am trying to do but I don't want to miss out on advantages that the full install could deliver.
yeto

---

### Post by oldfred on 2015-01-11
Some more explanation of the difference between a live install vs. a full install.

 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by efflandt on 2015-01-11
Note that a live/install installation like you had done so far has absolutely no security, since anyone could boot it and do things as root (superuser) if they know how to use sudo. So even if you have persistence and add a user with a password, they could still start it as user "ubuntu" without any password. So that type of live/install system is for trying out Ubuntu, using it to do a regular install to a different device, or using it in a pinch if you need it temporarily to fix something on an installed system. With persistence you can add programs to it, however you cannot install specific video drivers, update the kernal, or anything that happens initially during boot because that is all stored on a fixed squashfs (compressed) file system that cannot be changed without remastering the original iso file.

If you install it to another USB flash device, it should be at least 8 GB, but that would not leave you much room, so at least 16 GB would be better. That can be a USB memory stick, SD/microSD on a USB card reader, etc. However, it usually will not work in a laptop SD card slot, because unless that is internally USB connected, it is a different type of block device that the laptop cannot boot from. Although, I do have an Acer W500P tablet PC (which only has internal Win7 Pro on internal SSD) that is able to boot from its USB connected card slot. For that I have 64-bit Ubuntu and Lubuntu 12.04 partitions with common /home partition on 32 GB SDHC (no swap).

The reason that people recommend unplugging your internal hard drive if you do not know what you are doing yet is so you do not accidentally write anything to it or wipe out Windows. Even if you pick the correct device to install to, by default grub might be installed to your main drive, unless you know how to set the install otherwise. And if you installed Ubuntu on the other USB, but ended up with grub on your hard drive instead, your computer would not boot without the Ubuntu USB inserted. Unplugging your internal drive prevents you from accidentally doing that.

---

### Post by yeto on 2015-01-11
> **efflandt said:**
> Note that a live/install installation like you had done so far has absolutely no security, since anyone could boot it and do things as root (superuser) if they know how to use sudo. So even if you have persistence and add a user with a password, they could still start it as user "ubuntu" without any password. So that type of live/install system is for trying out Ubuntu, using it to do a regular install to a different device, or using it in a pinch if you need it temporarily to fix something on an installed system. With persistence you can add programs to it, however you cannot install specific video drivers, update the kernal, or anything that happens initially during boot because that is all stored on a fixed squashfs (compressed) file system that cannot be changed without remastering the original iso file.

If you install it to another USB flash device, it should be at least 8 GB, but that would not leave you much room, so at least 16 GB would be better. That can be a USB memory stick, SD/microSD on a USB card reader, etc. However, it usually will not work in a laptop SD card slot, because unless that is internally USB connected, it is a different type of block device that the laptop cannot boot from. Although, I do have an Acer W500P tablet PC (which only has internal Win7 Pro on internal SSD) that is able to boot from its USB connected card slot. For that I have 64-bit Ubuntu and Lubuntu 12.04 partitions with common /home partition on 32 GB SDHC (no swap).

The reason that people recommend unplugging your internal hard drive if you do not know what you are doing yet is so you do not accidentally write anything to it or wipe out Windows. Even if you pick the correct device to install to, by default grub might be installed to your main drive, unless you know how to set the install otherwise. And if you installed Ubuntu on the other USB, but ended up with grub on your hard drive instead, your computer would not boot without the Ubuntu USB inserted. Unplugging your internal drive prevents you from accidentally doing that.

Wow, thank you for taking time to reply, teach and explain.

I am not concerned about security as I will not be doing anything important on this particular computer and I don't want to take a chance of "installing" on my internal hard drive so I think I will stick with what I have for now.

One final question if you will allow. If and when I do decide to install the full version by clicking on "Install Ubuntu 14.04.1 LTS" will it give me the option to install to a different flash drive or will I have to do something complicated to install to a different flash drive? I understand that it could inadvertently install to the internal hard drive but will I at least see the option to install to the flash drive? 

Again, thank you for taking time out of your day to help,
yeto

---

### Post by sudodus on 2015-01-11
*Yes* you will have the option to select which drive will be the target drive. But the bootloader is treated separately, and you may forget about it and by mistake install it into the internal drive, even if you install the rest of the system to a USB pendrive. This is why it is good to disconnect the internal drive.

---

### Post by oldfred on 2015-01-11
You have to use the Something Else install option and choose the second flash drive which may be sdc or sdf or whatever. No different than any install to a second drive.
Bit more complex as you do have to create your own partition, assign it as / (root), and what format like ext4. On a flash drive you may not want swap, if you have a fair amount of RAM.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not highlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

### Post by yeto on 2015-01-11
> **oldfred said:**
> You have to use the Something Else install option and choose the second flash drive which may be sdc or sdf or whatever. No different than any install to a second drive.
Bit more complex as you do have to create your own partition, assign it as / (root), and what format like ext4. On a flash drive you may not want swap, if you have a fair amount of RAM.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not highlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

Thank you. Thank you. Thank you. A million times thank you.

All of this is very helpful.

Kind regards,
yeto

---

