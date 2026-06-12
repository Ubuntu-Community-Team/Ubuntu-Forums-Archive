---
title: "isolinux.bin missing or corrupt"
date: 2016-12-23
forum: General Help
---

### Post by richard7893 on 2016-12-23
Hello,

For some reason I have suddenly run into problems with booting up and accessing the Ubuntu OS. I have an Ubuntu 16.04.1 LTS running on a Toshiba Satellite A215. What I was trying to do was copy the Ubuntu OS ISO file onto a USB, and then next thing you know I ran into this mess. 

When I tried turning on the Toshiba computer I first got this message:

```
ERROR:UNKNOWN FILESYSTEM
```

And I googled what to do when this message shows up and got nowhere.

Anyway, I copied an Ubuntu OS ISO file onto a USB from a Mac and I can access the Ubuntu OS thru the live USB on my Toshiba. I attempted some troubleshooting, but still I am unable to access the Ubuntu OS (unless I use the USB). I now get this message when I boot up the computer without the USB:

```
isolinux.binmissing or corrupt
```

The previous ERROR:UNKNOWN FILESYSTEM message does not come up anymore. I don’t want to have to reinstall a new Ubuntu on my Toshiba, because I will lose all of my files I have on it. Does anyone know how I can get this back to normal?

---

### Post by yancek on 2016-12-23
An actual installed Ubuntu system will not have an isolinux.bin file nor will it look for it.  An Ubuntu Live DVD/flash drive will.  Did you write to the wrong drive when copying the iso?

Can you boot the installed Ubuntu or are you just able to view directories/files from the flash drive?

More information will probably be needed.  I would suggest you boot the Ubuntu on the flash drive and get the boot repair software and run it so we can see some details on your boot files.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If Ubuntu is the only OS and you have only one harddrive, you might just try re-installing Grub to the MBR, that is, if it is an MBR system?

---

### Post by richard7893 on 2016-12-24
yancek,

> 
[COLOR=#000000]An actual installed Ubuntu system will not have an isolinux.bin file nor will it look for it. An Ubuntu Live DVD/flash drive will. Did you write to the wrong drive when copying the iso?[/COLOR]

I am sure I wrote the iso file to the correct drive, that is the drive where my USB was on. I knew I copied the iso file to the right drive, otherwise I would not have been able to do a Live USB connection on my Toshiba.

> [COLOR=#000000]Can you boot the installed Ubuntu or are you just able to view directories/files from the flash drive?[/COLOR]

I am unable to boot the installed Ubuntu. When I go to the live USB, I cannot view any of my old files. It is like starting from fresh. All my old files and programs are not accessible. Further I uploaded the Boot-Repair and performed Option-1 (from the link you provided), which put the Boot-Repair directly on my USB. What I think this did was wipe out the existing iso file on my USB (Ubunu 16.04.1 LTS). So when I access Boot repair off my USB, once again it is like I am starting from fresh. All my old files and programs are not accessible.

> [COLOR=#000000]If Ubuntu is the only OS and you have only one harddrive, you might just try re-installing Grub to the MBR, that is, if it is an MBR system?[/COLOR]

Ubuntu is the only OS I have on my Toshiba. After looking into what MBR is, I'm not sure if my system is or isn't (MBR).

So after I ran Boot-Repair according to the link you provided, once it was complete a text file came up that I've attached in this post. I restarted my computer once the Boot-Repair said it was successful and I tried to boot into the installed Ubuntu (ie without the USB) but I still run into the same problem...  isolinux.bin missing or corrupt

Any help would be appreciated

---

### Post by Autodave on 2016-12-24
Ddi you just copy the file(s) onto the USB stick or did you burn them as a bootable disc/drive?  You cannot merely copy the file and boot to it: it has to be made bootable.

---

### Post by richard7893 on 2016-12-24
Autodave,

I added the Boot-Repair & Ubuntu Live onto my USB via UNETBOOTIN.

---

### Post by richard7893 on 2016-12-26
Got it to work guys. Heres a useful link:

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

I did did a Boot-Repair from the LiveUSB then did Purging & Reinstalling Grub2 as instructed from the link

---

