---
title: "Creating a multi-boot-USB &gt; What programme to use ?"
date: 2022-06-06
forum: General Help
---

### Post by GeordieJedi on 2022-06-06
Hi there guys.

I was wondering if you could help me out with a little project I'm working on.

**Background / situation:**
I'd very much like to create a multi boot USB stick for system rescue
and anti-malware scanning.

1. I'd like to use a few different "live-USB-rescue disks" from various
companies, e.g. ESET, Kaspersky, Avira, etc, etc.

2. All of these different ISO's & IMG files on the same USB stick
with a grub style menu to chose between each different OS / rescue prorgramme.

3. Have the ability to update the definiations for each of the programmes
(So that I dont have to re-download them each time).

**Questions:**

1. What (preferably - linux based, and GUI) apps can do this ?
(Create the multi boot USB)

2. Do I need to create a seperate partiton for each OS/rescue programme ?
Or will the USB creation programme do this for me ?

3. Is there anything else that Im missing ?

TIA for any help or advice

---

### Post by Rex Bouwense on 2022-06-06
Try Ventoy.  [https://www.ventoy.net/en/index.html](https://www.ventoy.net/en/index.html)  You can add and/or subtract the operating systems from the drive.  There is a boot partition which will give you the menu of all the OSs that you have on the stick and you choose which one you want at boot.

---

### Post by grahammechanical on 2022-06-06
A quick internet search reveals that large SSD USB sticks start at 128 GB and go up in stages to 1 TB. You need to treat the SSD as if it was a hard drive and install the operating systems on to it in partitions that you create.

An installation of Ubuntu or its flavours will install the Grub boot loader that will produce a boot menu. Then after each OS is installed load into Ubuntu and run in a terminal

```
sudo update-grub
```

and Grub will search the drive for the new operating systems and put them in the boot menu. There is something that you must watch out for. You must create an EFI boot partition on the SSD and make sure that each OS you install puts its boot files in that EFI boot partition and not the EFI partition on the machine's main drive. Otherwise the SSD USB drive will not be portable.

Regards

---

### Post by oldfred on 2022-06-06
I prefer to create my own.
I use grub2's loopback to boot ISO directly. Only a few systems do not work with loopback.
With smaller flash drives I would just install grub & several ISOs. And create my own boot stanzas.
Now with larger drives, I do a full install of Kubuntu, but many would suggest Lubuntu as lighter weight. I know Kubuntu & it is more middle weight. I do not install all the programs I normally use to keep it smaller.
Then in 40_custom add boot stanza for many ISO. Or now configfile to text file, see below.

[https://www.supergrubdisk.org/wiki/Loopback.cfg](https://www.supergrubdisk.org/wiki/Loopback.cfg)
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive#GParted_Live](https://wiki.archlinux.org/index.php/Multiboot_USB_drive#GParted_Live)
more examples
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

I only use gpt partitioning and now UEFI boot, but did use gpt with old BIOS boot systems.
I also regularly forgot to update grub when updating ISO. So I changed to use a configfile to a text file in my /ISO folder. Then grub does not need update every time ISO & text file get changed.
Example
Configfile example
[https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835](https://ubuntuforums.org/showthread.php?t=2076205&p=13787835#post13787835)

I now also have an external SSD and find it almost as fast as internal SSD. The flash drives were always really slow installing & writing. Once in memory flash drive speed does not matter. I have lots of flash drives, one 256MB that I retired as too small, but then found I could install rEFInd on it and have used it for emergency boot. SSD have dropped so much in price, I may buy another before adding to all my flash drives.

---

