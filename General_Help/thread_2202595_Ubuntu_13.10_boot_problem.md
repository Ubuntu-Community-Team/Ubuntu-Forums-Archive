---
title: "Ubuntu 13.10 boot problem"
date: 2014-01-30
forum: General Help
---

### Post by paradox716 on 2014-01-30
Hi, some basic info before I start. Laptop is an HP G62. Factory Windows 7. I fresh installed a Windows 8 on it so I don't think there's any UEFI or anything like that to tweak. I ran the 13.10 CD and it had an option to install inside of Windows 8. Nifty? I picked that and proceeded to do what was needed. Upon restarting, there's zero evidence of my Windows ever existing. And now with Linux installed my "F9" key that normally gives me my boot menu to boot to CDs, doesn't work. F1 and F10 do though. I ran that boot repair thing and this is the URL it supplied to me. 
[http://paste.ubuntu.com/6841828/](http://paste.ubuntu.com/6841828/)

The GRUB boot menu doesn't show windows at all anymore. Pretty sure instead of installing inside my Windows 8, it wiped it. Meh. Any ideas?

---

### Post by jeanjd63 on 2014-01-30
Hello 
In your boot-info, there is no trace of windows8. Ubuntu as overwrite him.

Good luck

---

### Post by claracc on 2014-01-30
What ubuntu 13.10 CD have you used to install ubuntu "inside windows"?, as far as I know, there is not an officially supported wubi (software to install ubuntu inside windows) installer.

As this link says, [http://www.ubuntu.com/download/desktop/install-desktop-latest](http://www.ubuntu.com/download/desktop/install-desktop-latest) ,you can install ubuntu 13.10 from DVD or USB and in anycase, there is not a possibility of installing ubuntu inside windows, see attached image.

The only eay, I think is to install virtualbox inside windows, and then install ubuntu inside virtualbox.

---

### Post by paradox716 on 2014-01-30
I'm 100% sure it's the 13.10 Ubuntu Linux from here. [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop). My install looked nothing like that thumbnail. It did say the same similar stuff. The first option I know said something about KEEPING windows 8. I remember cuz it didn't say the warning like the second one and it said that all my files would be kept. I just wanted to dual boot this. :(

Slight edit. My disk has a wubi.exe file on it?

---

### Post by sudodus on 2014-01-30
I think your problem is caused by encrypting the drive, as seen from **crypto_LUKS** in the following output.

```
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 1cc93310-50c1-40df-8976-0e0709555560   swap       
/dev/mapper/sda5_crypt CA0YmD-ayLk-ERmd-1bXK-dUHD-wQFN-oKO7G1 LVM2_member 
/dev/mapper/ubuntu--vg-root d7549bf7-b077-4b87-b8de-13759844ef7a   ext4       
/dev/sda1        de99f566-347f-4db4-a6e8-b89da9990fac   ext2       
/dev/sda5        f8ccf83c-f5d7-48e0-b9c2-c1bfb5411108   crypto_LUKS
```

If you want to encrypt Ubuntu side by side with Windows, you can use 'encrypted home', which does not grab the whole drive.

---

### Post by paradox716 on 2014-01-30
I guess I'll just reinstall both OS's again, no worries. Thank you guys for the valuable info. :)

---

### Post by sudodus on 2014-01-30
> **paradox716 said:**
> I guess I'll just reinstall both OS's again, no worries. Thank you guys for the valuable info. :)

Good idea. I suggest that you

0. Edit the partitions with ***gparted*** (when booted from the Ubuntu install drive).

1. 'Start with the least intelligent system first' to avoid having to rewrite the bootloader ;-)

2. Install Ubuntu (and let it create a grub menu). Select '***Something else***' at the partitioning page. This way you can know what you are doing. Install the bootloader to the head of the drive [most of the time /dev/sda (without any partition number) if there is only one internal drive].

---

