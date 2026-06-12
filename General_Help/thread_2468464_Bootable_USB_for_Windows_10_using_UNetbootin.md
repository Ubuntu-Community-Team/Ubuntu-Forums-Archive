---
title: "Bootable USB for Windows 10 using UNetbootin"
date: 2021-10-30
forum: General Help
---

### Post by angel mike on 2021-10-30
I am using Ubuntu 21.04 and have found a suggested method from Stackexchange - see below. 
The iso file size is greater than 4GB which means the files have to be split. None of the other options like Rufus etc do not work or no longer supported.
Is this the best method?

For all the poor Linux admins without a Windows computer like me, who need to help relatives installing Windows 10 (sigh). This is the way under Linux (in my case Ubuntu Bionic).
Use UNetbootin to create an USB-Stick from the Windows ISO. Unfortunately there will be no message, that it truncated the install.wim (in case it is larger than 4G). At least UNetbooin creates a bootable USB-Stick.
Now, use 7zip (apt-get install p7zip) to extract the ISO (it is enough to extract the install.wim file. Do not use the broken install.wim from the created USB-Stick !!). Or alternatively mount the Windows-ISO if you are a more advanced Linux user.
Next use wimexport (apt-get install wimtools) to extract and compress the Windows type needed from original install.wim. With wiminfo you can list all included Windows types.
In my case I ran (see man wimexport): wimexport install.wim 1 home.wim --compress=LZX:100
The previous step created a small (<4G) wim-file which I copied into the sources directory of the UNetbootin created USB-Stick overwriting the broken install.wim (e.g. cp home.wim /mnt/sources/install.wim).
With this I could successfully boot the Windows 10 installer and do the install.

---

### Post by oldfred on 2021-10-30
The Windows install tools split the .wim file.
I just do not understand why Microsoft does not make the ISO have the split .wim file as it has to be in a FAT32 partition for UEFI boot.
But it must just what everyone to use Windows tools or assumes everyone has Windows.

Some more info just to have it in one thread.
Split .wim with Linux tools.
[https://www.dedoimedo.com/computers/windows-10-usb-media-linux.html](https://www.dedoimedo.com/computers/windows-10-usb-media-linux.html)
The .wim too large, Windows commands to split
[https://www.dell.com/support/article/en-us/sln313422/windows-10-iso-contains-wim-file-that-is-big-for-fat32-file-system?lang=en](https://www.dell.com/support/article/en-us/sln313422/windows-10-iso-contains-wim-file-that-is-big-for-fat32-file-system?lang=en)

---

### Post by sudodus on 2021-10-30
In Ubuntu 21.04 you can install mkusb, which can create a Windows installer into a USB drive of at least 8 GB. See this link

[mkusb - tool to create boot drives](https://help.ubuntu.com/community/mkusb)

It works will all current versions of Windows including Windows 11.

---

### Post by angel mike on 2021-10-30
Thanks oldfred and sudodus - will have another go with suggestions.

---

### Post by sgage on 2021-10-30
You might want to try Ventoy - it handles every Linux and Window iso I've thrown at it. You install it on your USB stick, and then just copy iso files to it. When you boot it, it gives a menu of all the things you've put on it. I have one USB stick with several distros and Windows versions on it. Almost like magic...

---

### Post by C.S.Cameron on 2021-11-01
Maybe I was doing something wrong with **Ventoy**, but the Windows installers I create will only install Windows for UEFI mode. They will not install for legacy, (BIOS), mode.
If you need Legacy Windows use **mkusb**.

---

### Post by angel mike on 2021-11-01
Thanks again everyone for contributions.

I tried mkusb and have a bootable Windows 10 USB but when loading I get to page asking where I want to install Windows It says the existing partitions are of an recolonized type and need to be . formatted as NTFS. How do I achieve that? 
There is a format option - does this mean it will format the hard drive and create partitions to suit ?

---

### Post by angel mike on 2021-11-01
OK found a useful link ' [https://www.groovypost.com/howto/clean-install-Windows-10](https://www.groovypost.com/howto/clean-install-Windows-10)' that explains what to do with web pictures.

Also use this as an alternative guide to mkusb manual which can be confusing. This link shows how to use mkusb with web pictures showing which of the options to use
[https://bnhr.xyz/2017/04/03/create-a-bootable-windows-10-usb-in-xubuntu-16.04-using-mkusb.html](https://bnhr.xyz/2017/04/03/create-a-bootable-windows-10-usb-in-xubuntu-16.04-using-mkusb.html)

---

