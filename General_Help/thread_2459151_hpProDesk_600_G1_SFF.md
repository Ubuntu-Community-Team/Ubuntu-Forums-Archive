---
title: "hpProDesk 600 G1 SFF"
date: 2021-03-11
forum: General Help
---

### Post by grey1beard on 2021-03-11
The above desktop, with a 0.5T HDD and a 1T SSD, now has ubuntu 16.04 installed to replace win 10, installed from an .iso disk of 64 bit ubuntu 16.04.

1. Had several issues, but the current one is that I can't get it to use my usb webcam, (Gensys Logic, HD-smart MIC) though it's correctly identified in **lsusb**.

2. I've started to explore the computer using terminal, typed in **lshw**, which correctly found the camera, but I noticed the storage identification was not as expected.

```
/0/1           scsi0            storage        
/0/1/0.0.0     /dev/sda         disk           480GB BTO-480GB
/0/1/0.0.0/1                    volume         511MiB Windows FAT volume
/0/1/0.0.0/2   /dev/sda2        volume         430GiB EXT4 volume
/0/1/0.0.0/3   /dev/sda3        volume         15GiB Linux swap volume
/0/2           scsi1            storage        
/0/2/0.0.0     /dev/sdb         disk           1TB WDC WD10EURX-63C
/0/2/0.0.0/1   /dev/sdb1        volume         15MiB reserved partition
/0/2/0.0.0/2   /dev/sdb2        volume         931GiB Windows NTFS volume
```

The SDD seems to be invisible to my file system, so I suspect that my original installation ignored it. Should that have been formatted before I started the installation ?
If this is so, and I'd be grateful for guidance, and solving the first problem can wait till I've sorted the second one !

John

---

### Post by CelticWarrior on 2021-03-11
Ubuntu 16.04 will be out of support next month.
You SDD is sdb. Why do you think it's invisible? It contains Windows partitions.

---

### Post by grey1beard on 2021-03-11
Why do I think it's invisible ?
Because there is no component in my file system that shows it, and if I look at 'Properties' of my 'Computer' it shows the total capacity as 455.1 GB.
Perhaps I need to look elsewhere to find/use its storage capacity ?
That sort of information might have been helpful.

> Ubuntu 16.04 will be out of support next month. is well known to me, but thank you.

---

### Post by CelticWarrior on 2021-03-11
I know it is well know to you because this is the second time I'm telling you this, other might have as well. Because of that there NO POINT in troubleshooting it.
Regarding the the SSD, as it still contains Windows, its partitions won't be automatically mounted and if you didn't disable Windows 10 Fast Startup then at best they can be mounted read-only. Of course, you can at any time delete those partitions a format the drive. That said it makes no sense to have OSes installed in the HDD and a data partition on a SSD, it should be the other way around.

I suggest you do yourself a favor and stop wasting time with what you have currently. If you want to replace Windows then boot Ubuntu 20.04 LTS > Try Ubuntu. Then backup all the personal files you need to an external storage if you haven't done that already (you definitely should've). Then open GParted and cleanup everything: Device > Create partition table... > choose GPT for both drives. Reboot into UEFI ("BIOS") and assure the drives boot order has the SSD as the first priority (that's where the installer will create the ESP -and- the root file system for Ubuntu). Boot Ubuntu 20.04 and install. Finally create one (or more) partition in the HDD in order to use it for data storage, NOT for the OS. This can be done during the installation but doesn't have to be. Better focus on correctly install a supported version going forward.

---

### Post by grey1beard on 2021-03-11
I'm sorry to have caused you any pain, but thank you for your second paragraph advice, which I have pasted onto this desktop, in order to keep going.
I may only have a few years left, but after 80 years I've just got into the habit of sticking to what I am familiar with.
I hope I don't have to bother you again.
John

---

### Post by CelticWarrior on 2021-03-11
Yes, I understand the appeal of familiarity but in an online world things are always moving on, fast.
Please understand that even for-profit OSes don't have lifetime support and when it ends you're on your own with those.
Ubuntu provides a very generous extended support - 5 years - for long term support releases such as 16.04, 18.04 and the current 20.04 (the next will be 22.04, expected to be released during April 2022). Ubuntu 16.04 (April 2016) is now coming to its planned end and it's time to move on to newer releases that, unlike what happens with a certain proprietary OS, aren't even that different although some workflow adjust is required. The current and the previous LTS releases now run a modified Gnome DE made to look like the old Unity in 16.04 but in some aspects different.

---

### Post by grey1beard on 2021-03-13
The only remaining problem I have is that in the reboot/bios menus, there is no clear indication of the identity of the two disk drives.
The order shown is -
[B]UEFI Boot Sources
         ATAPI CD/DVD Drive
         USB Floppy/CD
         USB Hard Drive
         IP4 Intel(R)Ethernet Connection I217-LM 
         IP6 Intel(R)Ethernet Connection I217-LM[/B]
*Legacy Boot Sources : Disabled*

Can I choose which drive to load the 'ESP' and 'the root file system' in during the installation process ?
The only alternative I can think of is to disconnect the HDD first, then add it in as a new drive after installation of the OS.

---

### Post by CelticWarrior on 2021-03-13
At "UEFI boot sources" you should find the HDD and the SSD. The one added later will likely not be the first priority so if the HDD is the first that's exactly what you should change and make it the first in the boot order.

Then you may follow the rest of the suggestions above: Boot Ubuntu live session (Try Ubuntu), open Gparted and cleanup everything with menu Device > Create new partition table > GPT. Repeat for the second drive. 

Then start the installer and let it do its thing automatically (Erase and install..), just make sure the correct drive (SSD) is selected (it should be but check anyway). After installing Ubuntu you can easily format the HDD.

---

### Post by grey1beard on 2021-03-13
Oddly, the hdd and ssd are not separately mentioned in the UEFI boot source.

So, I've used the gparted tool to get the requisite partitions in the required drives, and installation is now ongoing.
If anything is amiss, at least I'm now familiar with gparted !
Thanks for your help,
John

---

