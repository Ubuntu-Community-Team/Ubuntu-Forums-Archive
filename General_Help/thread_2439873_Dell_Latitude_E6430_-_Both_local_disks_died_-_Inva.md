---
title: "Dell Latitude E6430 - Both local disks died - Invalid partition table!"
date: 2020-04-02
forum: General Help
---

### Post by ase62 on 2020-04-02
Hi there! I hope that anyone might help me! I have a Dell Latitude E6430. The local disk has dead and, as I need to buy a new one but the world has stopped during coronavirus crisis, I managed to use the /dev/sdb partition of 16 Gbytes to install a simple Linux Ubuntu or a Linux Mint from a USB. I don't need more that a firefox and LibreOffice so maybe I could install the OS and try.

I had forgotten that /dev/sdb must be the local internal disk of 16Gb that Dell uses to install a boot partition, so I committed a big mistake. Now my laptop cannot even start from a Linux Live USB. Options:

1) UEFI mode:  Message is: No bootable devices--strike F1 to retry boot, F2 for setup utility. If I try to start from F12 => USB (Linux Live) the message is "Invalid partition table!". If I use another USB stick with the BIOS downloaded from dell site the message is different: "Loading DRMK Version 8.0... Can't load kernel file".

2) Legacy mode: When trying to start the message is: "No Boot Device Found. Press any key to reboot the machine. When rebooting with Linux USB stick, the message is "Invalid partition table!" again, and when using USB Dell Flash drive the message is again: "Loading DRMK 8.0...". Can't Load kernel file.

I don't have the Windows DVD so I really don't know how to, at least, manage to reboot with a Live CD until I manage to buy a new TOSHIBA disk (120 or 350 Gbytes).

Any ideas to solve this issue? 

Thanks in advance!

---

### Post by lvm on 2020-04-02
If it says "Invalid partition table" chances are that it is indeed invalid. Are you sure your flash drive works? Can you boot from it on another PC or at least mount it?

---

### Post by ase62 on 2020-04-02
Thanks for your answer ;). The USB key is perfect. In fact, I used gparted from it and that's how I deleted /dev/sdb, the partition that is needed on DELL computers. I don't know how to recover it...

---

### Post by lvm on 2020-04-02
Something doesn't add up here: /dev/sdb is not a partition, it's a device and it cannot be deleted. Partitions should have names like /dev/sdb1. And if your disk has failed and the recovery partition was on it, it should be lost with the disk unless Dell installs a small second flash drive for recovery, but I never heard of such thing. Well, anyway Dell provides OS recovery tool which can be used to recover the recovery partition in case of disk failure, you can get it from their site. But it is also a bootable flash drive.

---

### Post by ajgreeny on 2020-04-02
I am wondering if you can boot to your live USB, install gnome-disk-utility if it's not a default application, and using that run the SMART disk tests from it; click on the cog top right and choose to run it and it should tell you more about the disk.

---

### Post by ase62 on 2020-04-03
> **ajgreeny said:**
> I am wondering if you can boot to your live USB, install gnome-disk-utility if it's not a default application, and using that run the SMART disk tests from it; click on the cog top right and choose to run it and it should tell you more about the disk.
Thanks for your post, ajgreeny. As I explained, there's no way to start with the USB key since I deleted the internal /dev/sdb disk that many DELL servers have, and the main disk /dev/sda is dead :(

> **lvm said:**
> Something doesn't add up here: /dev/sdb is not a partition, it's a device and it cannot be deleted. Partitions should have names like /dev/sdb1. And if your disk has failed and the recovery partition was on it, it should be lost with the disk unless Dell installs a small second flash drive for recovery, but I never heard of such thing. Well, anyway Dell provides OS recovery tool which can be used to recover the recovery partition in case of disk failure, you can get it from their site. But it is also a bootable flash drive.
Sorry, I will better explain: /dev/sdb is a disk, sure, and it had many partitions. I remove all of them to perform a full format of the disk to be able to install a Linux over that small disk (16Gbytes). I have deleted all data and partitions and since then there's no way to start the live OS, even with the same USB key I used to delete them via gparted.

---

### Post by lvm on 2020-04-03
So if you could delete partitions from the disk it is means that it was not quite dead after all? Well, anyway if you are quite sure about your bootable USB stick and yet your laptop won't boot even with secure boot disabled it is clearly a Dell-specific issue and should be addressed to their support. As I said, I would've started by using Dell OS recovery tool. There is also a small chance that resetting BIOS (UEFI) setting would help. Or make things worse.

---

### Post by ase62 on 2020-04-03
> **lvm said:**
> So if you could delete partitions from the disk it is means that it was not quite dead after all? Well, anyway if you are quite sure about your bootable USB stick and yet your laptop won't boot even with secure boot disabled it is clearly a Dell-specific issue and should be addressed to their support. As I said, I would've started by using Dell OS recovery tool. There is also a small chance that resetting BIOS (UEFI) setting would help. Or make things worse.
I will try to explain: the disk that was dead was /dev/sda. It was recongnised by Ubuntu Live OS, but I could not perform an installation over it through Live OS. It hanged on third step (after having selected wifi and language). Scan of the disk reported physical errors. So I tried to use the small one (also internal), /dev/sdb, by formatting the disk and trying over it the installation. But after having removed partitions and formatted the disk, something went wrong and I did not manage to reboot again, appearing mentioned errors.

I tried disabling secure boot also, yes, but as I have deleted that internal disk (sdb) it seems that we need to restore someway. Yes, it seems a problem more with DELL, but the laptop has no warranty and currently I'm isolated at home by Coronavirus crisis and I was trying to solve by myself (if someone else knew about this problem). OK, I think I have lost the laptop. Thanks anyway ;)

---

### Post by ajgreeny on 2020-04-03
So it sounds as if you can still boot to the live system; you do not need a hard disk in the machine to do that so I am mystified by your comment in post #6.

So I repeat; boot to the live USB and choose to run the live system, not install it.
Install gnome-disk-utilities if necessary asnd check the SMART status of the hard disk from that.
A simple task and it may help a great deal.

---

### Post by dragonfly41 on 2020-04-03
[From what I read here]("https://www.dell.com/community/Latitude/HDD-or-SSD-for-Latitude-E6430/td-p/5894146") it seems that your laptop might have two internal drives.
The main drive /dev/sda and a second drive, an SSD, /dev/sdb (which you refer to).

I would have another go installing Ubuntu in (internal) /dev/sdb or if you have an external USB drive in /dev/sdx.
Note if you are using LiveUSB this will show in sequence  as /dev/sdc after the first two internal drives.

I have a Dell tower PC with internal HDD (Windows 10 and Ubuntu) and external USB 3.0 SSD with Ubuntu.
I use rEFInd as main boot loader and this works nicely.

Another thing I would try (just being curious) would be to manually remove /dev/sda (if it is suspect) and using LiveUSB attempt to install Ubuntu into the internal SSD (which will now be /dev/sda).  Using LiveUSB GParted ensure that the first partition of the SSD is ESP (500mb) fat with boot flags for installing rEFInd boot.

[Guide on rEFInd.]("https://www.rodsbooks.com/refind/installing.html")

---

### Post by ase62 on 2020-04-03
> **ajgreeny said:**
> So it sounds as if you can still boot to the live system; you do not need a hard disk in the machine to do that so I am mystified by your comment in post #6.

So I repeat; boot to the live USB and choose to run the live system, not install it.
Install gnome-disk-utilities if necessary asnd check the SMART status of the hard disk from that.
A simple task and it may help a great deal.
Thank you, ajgreeny. I'm afraid it seems I'm not able to make understand. I'm very sorry as english is not my native language. Both disks: SDA and SDB are lost. SDA is broken and SDB is DELETED by myself. SDB contained useful DELL information that avoids to restart the server with LIVE USB Ubuntu since I deleted it. No way. I can access BIOS, I can reboot, select Live USB, but always same error already reported. So no: I'm afraid I cannot install anything at all as I cannot even boot anymore (I cannot even run the live system). That's my problem.

I hope is clear now ;)

> **dragonfly41 said:**
> [From what I read here]("https://www.dell.com/community/Latitude/HDD-or-SSD-for-Latitude-E6430/td-p/5894146") it seems that your laptop might have two internal drives.
The main drive /dev/sda and a second drive, an SSD, /dev/sdb (which you refer to).

I would have another go installing Ubuntu in (internal) /dev/sdb or if you have an external USB drive in /dev/sdx.
Note if you are using LiveUSB this will show in sequence as /dev/sdc after the first two internal drives.

I have a Dell tower PC with internal HDD (Windows 10 and Ubuntu) and external USB 3.0 SSD with Ubuntu.
I use rEFInd as main boot loader and this works nicely.

Another thing I would try (just being curious) would be to manually remove /dev/sda (if it is suspect) and using LiveUSB attempt to install Ubuntu into the internal SSD (which will now be /dev/sda). Using LiveUSB GParted ensure that the first partition of the SSD is ESP (500mb) fat with boot flags for installing rEFInd boot.

[Guide on rEFInd.]("https://www.rodsbooks.com/refind/installing.html")
Yes, you are right, dragonfly41: my laptop has a 320 Gbytes (aprox.) - SDA and a 16 Gbytes disk (SDB that never must be overwritten, also internal, from DELL). What you are suggesting is my goal since the very beginning: installing Ubuntu in internal /dev/sdb, but the installation menu is not working anymore since I deleted that disk. So I'm not able to install Ubuntu even on an external disk. I would like to be able to do that using the small disk to install GruB, but it seems that SDB disk had something that, if is deleted is not allowing me to start anymore. 

**The solution should be to re-flash /dev/sdb partition** to it's original state. In fact, I downloaded from DELL a tool to do that. Using another USB stick I managed to install an image on it from DELL to recover it, but it didn't work. It's in spanish, but this is the link:

[https://www.dell.com/support/article/es-es/sln133635/c%C3%B3mo-corregir-un-error-de-partici%C3%B3n-invalida-en-un-sistema-con-una-unidad-de-estado-s%C3%B3lido?lang=es](https://www.dell.com/support/article/es-es/sln133635/c%C3%B3mo-corregir-un-error-de-partici%C3%B3n-invalida-en-un-sistema-con-una-unidad-de-estado-s%C3%B3lido?lang=es)

I also find the DELL web to download BIOS updates:

[https://www.dell.com/support/home/es/es/esbsdt1/product-support/product/latitude-e6430/drivers](https://www.dell.com/support/home/es/es/esbsdt1/product-support/product/latitude-e6430/drivers)

So currently I don't know what else to do. I guess I need to buy a new laptop once the crisis ends.

---

### Post by dragonfly41 on 2020-04-03
The above link (in Spanish) you posted is readable in English using Google Translate in my Chromium Browser,

[h=1][SIZE=4]How to fix an invalid partition error on a system with a Solid State Drive[/SIZE][/h]That seems to be the way forward to restore your SSD (/dev/sdb). Then I would focus on installing Ubuntu on an external drive through USB port if you possibly can (you might need to order an external drive to place in a container), Unless of course you wish to try adding Ubuntu to your Windows partition as dual boot. This would result in /dev/sda, /dev/sdb/ and /dev/sdc in your internal (but I don't know if adding dual boot would break your setup). My inclination would be to stick Ubuntu on an external drive thus preserving the order of partitions..
Using LiveUSB "Try Ubuntu" I would also install testdisk on LiveUSB and analyse state of laptop /dev/sda.

[Here is an example of a portable SSD (but check port requirements - you might need USB 3.0).]("https://uk.crucial.com/products/ssd/x8-portable-ssd")

I use Crucial SSD in a docking station.

---

### Post by ase62 on 2020-04-03
> **dragonfly41 said:**
> The above link (in Spanish) you posted is readable in English using Google Translate in my Chromium Browser,

**[SIZE=4]How to fix an invalid partition error on a system with a Solid State Drive[/SIZE]**

That seems to be the way forward to restore your SSD (/dev/sdb). Then I would focus on installing Ubuntu on an external drive through USB port if you possibly can (you might need to order an external drive to place in a container), Unless of course you wish to try adding Ubuntu to your Windows partition as dual boot. This would result in /dev/sda, /dev/sdb/ and /dev/sdc in your internal (but I don't know if adding dual boot would break your setup). My inclination would be to stick Ubuntu on an external drive thus preserving the order of partitions..
Using LiveUSB "Try Ubuntu" I would also install testdisk on LiveUSB and analyse state of laptop /dev/sda.

[Here is an example of a portable SSD (but check port requirements - you might need USB 3.0).]("https://uk.crucial.com/products/ssd/x8-portable-ssd")

I use Crucial SSD in a docking station.
I followed all the steps:

1) Format the USB stick
2) Downloaded the last BIOS for my system
3) Put the .exe file (E6430A24.exe) in the stick
4) I eject the stick and connect it via USB to the broken DELL
5) Reboot and F12 to open the Boot Device
6) I select USB and press ENTER
7) Appears the following message:"Remove disc/media. Press a key to go on"
8) After pressing a key appears: "Selected boot device failed. Press any key to reboot the system

No way...

There was an additional message on instructions: "If BIOS file does not execute automatically, then you must write the command E:\XXXXX.exe (using the name of the USB letter and XXXX the name of the file on USB (E6430A24.exe on our case). And press ENTER. But as I cannot type anything, I cannot try that last posibility :(

---

### Post by dragonfly41 on 2020-04-03
I am totally guessing here but instead of trying to run E6430A24.exe directly in the stick could you use instead a bash script which runs it indirectly?
This might overcome the need to type the command and then press ENTER.
But again this is guesswork.

**[Later Edit]**
Is it possible in Boot Options to boot from your USB containing E6430A24.exe  to update your BIOS?
Your USB will need boot flags set.
This might be done by first launching LiveUSB Try Ubuntu.
Then plug in your *second USB containing E6430A24.exe.*
In LiveUSB Ubuntu launch GParted and scan the second USB containing E6430A24.exe.
Add boot flags to that USB partition.
Shutdown and remove only LiveUSB leaving USB with E6430A24.exe plugged in.
Boot up Dell and change boot options to run the USB first.

This workflow assumes that you have two USB ports.

---

### Post by ase62 on 2020-04-04
> **dragonfly41 said:**
> 
**[Later Edit]**
Is it possible in Boot Options to boot from your USB containing E6430A24.exe  to update your BIOS?
Your USB will need boot flags set.
This might be done by first launching LiveUSB Try Ubuntu.
Then plug in your *second USB containing E6430A24.exe.*
In LiveUSB Ubuntu launch GParted and scan the second USB containing E6430A24.exe.
Add boot flags to that USB partition.
Shutdown and remove only LiveUSB leaving USB with E6430A24.exe plugged in.
Boot up Dell and change boot options to run the USB first.

This workflow assumes that you have two USB ports.
Thanks so much, dragonfly41. As I have commented and explained, the Live USB Ubuntu stopped working after I deleted the /dev/sdb partition. Now is useless as boot sequence on my DELL laptop depends on something that was written on that disk and I deleted.

So, answering your suggestion: Yes, it's possible on boot options (F12) to force the start from a USB containing the E6430A24.exe file. In fact that's why I tried yesterday many times to try to update my BIOS. Message was: "[COLOR=#000000]Remove disc/media. Press a key to go on" and, after pressing any key[/COLOR][COLOR=#000000] appears another message: "Selected boot device failed. Press any key to reboot the system.

[/COLOR]I created a script, as you suggested wisely to launch/force that .exe file, but the result was the same. Live USB Ubuntu reports the errors I explained on my very first post. So no way to launch gparted anymore (last time I used it was when I use it to delete partitions on /dev/sdb and then I formated that internal disk. On BIOS it's also configured the USB as the first boot option.

Thanks again for helping ;)

EDIT: OK. I catch you: do you mean to launch Live USB Ubuntu ON A DIFFERENT LAPTOP, right? Sorry I did not understand from the beginning. OK. I may try on another laptop. Maybe we can force the .exe USB the boot flags...

---

### Post by dragonfly41 on 2020-04-04
You should be able to boot up your LiveUSB even with your internal /dev/sdb dead.
Provided of course that it was created as bootable.
I would try to use LiveUSB to somehow populate your internal /dev/sdb / BIOS.
Perhaps some form of basic DOS in USB might be needed to execute [COLOR=#000000][I]E6430A24.exe?

[/I][I study here]("https://www.dell.com/support/home/uk/en/ukdhs1/drivers/driversdetails?driverid=ng6cn&oscode=w764&productcode=latitude-e6430-atg").

[And here]("https://www.acronis.com/en-us/articles/usb-boot/").

[P.S.] [Here is account of another "bricked laptop"]("https://www.dell.com/community/Laptops-General-Read-Only/Dell-Latitude-E6430-bios-settings-reset/td-p/4784611").  Try the idea to reset BIOS to factory default?[/COLOR]

---

### Post by ase62 on 2020-04-04
> **dragonfly41 said:**
> You should be able to boot up your LiveUSB even with your internal /dev/sdb dead.
Provided of course that it was created as bootable.
I would try to use LiveUSB to somehow populate your internal /dev/sdb / BIOS.
Perhaps some form of basic DOS in USB might be needed to execute [COLOR=#000000][I]E6430A24.exe?

[/I][I study here]("https://www.dell.com/support/home/uk/en/ukdhs1/drivers/driversdetails?driverid=ng6cn&oscode=w764&productcode=latitude-e6430-atg").

[And here]("https://www.acronis.com/en-us/articles/usb-boot/").

[P.S.] [Here is account of another "bricked laptop"]("https://www.dell.com/community/Laptops-General-Read-Only/Dell-Latitude-E6430-bios-settings-reset/td-p/4784611").  Try the idea to reset BIOS to factory default?[/COLOR]
OK. I have a jetson-nano (a sort of Raspberry Pi, probably you know). I have used it to check with fdisk that the USB stick had the bootable flag active (there's an * on it). I forced again with a letter to active the flag and retried, but unfortunately no success. In fact, my USB stick has a LED that flashes when I reboot on the broken laptop, which means that is being read, and then I get the error: "Quite el disco/medio. Pulse una tecla para continuar" ("Remove disk/media. Press any key to continue" in english). 

I will check the links you have posted and will back to you if I got extra news. Thanks again for the support.

---

### Post by dragonfly41 on 2020-04-04
[Here is a follow up on my earlier thought.]("https://www.thomas-krenn.com/en/wiki/Creating_a_Bootable_DOS_USB_Stick")

The idea is to make your external USB containing your E6430A24.exe a bit more intelligent by executing it through DOS
when it is booted, and then repopulate your BIOS. DOS would need to run E6430A24.exe without keyboard intervention (which is the problem you cite).

This is an extract from above link ...


> Creating a DOS Stick with Unetbootin
1. In Ubuntu, the code is installed via apt using apt-get install unetbootin&#8226; Or download UNetbootin from UNetbootin downloads (unetbootin.net).

&#8226; A download of FreeDOS is not necessary as Unetbootin distributions can independently download and install the program.

Now the theory is if you boot up LiveUSB Ubuntu you can install unetbootin in Ubuntu and then use unetbootin to create a second bootable DOS USB, containing E6430A24.exe and a startup script to run it. Unless there is a much easier way to reset boot to factory settings by unplugging the battery!


[Later Edit][ Found this thread ]("https://stackoverflow.com/questions/20206609/make-a-auto-run-file-with-free-dos")on creating an "auto run" script in FreeDOS.

---

### Post by ase62 on 2020-04-04
Thanks again. I managed to install the file following these steps:

1) Downloaded Rufus portable app on a windows (if possible). Probably there are other options in Linux but for me this was too easy because Rufus allows directly to create a DOS bootable USB:

[https://www.howtogeek.com/136987/how-to-create-a-bootable-dos-usb-drive/](https://www.howtogeek.com/136987/how-to-create-a-bootable-dos-usb-drive/)

2) Once the process ends, I just copied the  E60430A24.exe file.
3) Reboot with USB as first option
4) Select the option 1) "Spanish keyboard" (option 2) allows to select english keyboard).
5) Accessed finally to a C:\ promt, from where I managed to launch the .exe file.
6) The process flashes the BIOS, but it seems that it has not repaired the /dev/sdb as the result is the same: no way to start with Ubuntu Live USB :(. Same error.

Any hint?

It seems that it just re-flash the BIOS, but it does not modify local disks. Probably I should buy a new /dev/sda disk so Ubuntu Live USB might start. No idea.Is there a way to launch the Ubuntu Live from the DOS promt :D :D?

---

### Post by dragonfly41 on 2020-04-04
[All I can suggest reading is this for now.]("https://community.spiceworks.com/topic/2004952-how-can-i-make-a-usb-drive-that-boots-to-a-command-prompt")    WinPE?

---

### Post by ase62 on 2020-04-04
This was the big mistake:

[https://www.dell.com/community/Laptops-General-Read-Only/Latitude-Recovery-Partitions-can-I-delete-them/td-p/4155755](https://www.dell.com/community/Laptops-General-Read-Only/Latitude-Recovery-Partitions-can-I-delete-them/td-p/4155755)

Don't know how to recover them... :(

---

### Post by dragonfly41 on 2020-04-04
I would dig around for help in Dell forums.

[https://www.dell.com/community/Storage-Drives-Media/How-do-I-re-create-the-Dell-Diagnostic-Utility-Partition/td-p/1003743](https://www.dell.com/community/Storage-Drives-Media/How-do-I-re-create-the-Dell-Diagnostic-Utility-Partition/td-p/1003743)

---

### Post by Yellow Pasque on 2020-04-04
> **ase62 said:**
> This was the big mistake

I think people understand what happened.  What they are trying to tell you is that you should be able to start the LiveUSB regardless of whether there are unpartitioned drives in your system (or even if there are no drives installed in the system).
There are only a few thing that I can think of in the BIOS settings:
1. Make sure the USB comes first in the boot sequence.
2. Make sure SecureBoot is disabled.
3. If you are going to use Linux, make sure the SATA controller is in AHCI (not RAID) mode.
4. You can try disabling the SATA controller entirely. That way, the internal disks won't be recognized (assuming the SSD is an mSATA drive). In fact, you should probably do this until you can get the LiveUSB to boot to rule out interference from the disks. 

> Don't know how to recover them...

You need the LiveUSB to boot. Once you've done that, you can recreate the EFI boot partition using gparted: 
1. Select the disk you want and create a new GPT partition table.
2. Make a small (350-500MB) FAT32 partition.
3. Set the boot flag on the new partition.

As for the other partitions you deleted, you probably can't get the original contents of them back, especially the two Windows8 partitions (but if you're trying to run Linux on a 16GB drive, you probably don't have room for Windows anyway). I don't know too much about the Dell diagnostic partition.

---

### Post by dragonfly41 on 2020-04-04
> [color=#000000]i think people understand what happened. What they are trying to tell you is that you should be able to start the liveusb regardless of whether there are unpartitioned drives in your system (or even if there are no drives installed in the system).

[size=3]**+1**[/size][/color]

---

### Post by ase62 on 2020-04-04
I must apologize you guys. This was so weird that I decided to test the Live USB, that had worked two days ago, on a different healthy laptop and... oh surprise! It didn't worked :(

So I decided to re-flash the USB with Linux Mint and it worked from the very beginning. You told me many times to be sure that the Live USB was ok and I couldn't believe that it had remain corrupted.

So, ok. I now have managed to reboot with Ubuntu live USB. The next step, knowing that I can install the operative system is to buy a new Toshiba disk (I have seen many for about 20 euros) and then I could reinstall over that disk. I have started the gparted. I'm sorry for having make you waste time, but I guess that we have learned something else about DELL BIOS (specially me). In fact, now I see on gparted that it was myself the one who deleted the USB-stick, as it appears as sdb. 

Conclusion:

- There's no /dev/sdb disk, but the USB-stick itself, and it seems I deleted it.
- I can buy a new SDA disk to reinstall the operative system on it correctly.
- Question: Can I install Ubuntu on an external USB disk? Do you recommend me to do that, at least for the next 30 days that we will be in Spain isolated (unable to buy the hard disk)? Will the performance be very poor with a normal USB disk?

Thanks in advance!

---

### Post by CelticWarrior on 2020-04-04
> - Question: Can I install Ubuntu on an external USB disk? Do you  recommend me to do that, at least for the next 30 days that we will be  in Spain isolated (unable to buy the hard disk)? Will the performance be  very poor with a normal USB disk?

Yes, you can install Ubuntu in an external drive. The performance depends on many factors. USB3.x drives will be better than USB2.0 ones, obviously but it should also be factored in the speed of the actual drive. A traditional HDD will be much slower than a new SSD in an external case/adapter.

But the good news is both Amazon and Aliexpress (via Correos) will still deliver goods, it just take a few days longer than it used to. Other local online stores like the Galician [O Pirata]("https://www.opirata.com/") also deliver to your home anywhere in Spain or Portugal.

---

### Post by ase62 on 2020-04-04
Thank you so much, CelticWarrior. I will try to get the proper Toshiba Dell disk to avoid having external disk if the delivery takes just a few days.

I am posting now from the Live USB Mint. Unbelievable the power of Linux (Gimp included on the stick itself and possibility to quickly install any input language) and the wisdom of this forum and its contributors. Thanks so much for having helped to solve this issue. I am a happy man now. 

By the way: this is the picture of gparted taken form the broken laptop. You can see the for partitions that puzzled me, as I wondered that it was an internal disk... 13 Gbytes free... unallocated. Where are those 13 Gbytes?

[[IMG]http://thumbs.subefotos.com/bdd753474d541011537a534b208795e0o.jpg[/IMG]]("https://subefotos.com/ver/?bdd753474d541011537a534b208795e0o.jpg")

And this is the lsblk output:

mint log # lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdb      8:16   1   3.8G  0 disk /cdrom
&#9500;&#9472;sdb2   8:18   1   2.3M  0 part 
&#9492;&#9472;sdb1   8:17   1   1.8G  0 part 
sr0     11:0    1  1024M  0 rom  
loop0    7:0    0   1.7G  1 loop /rofs
sda      8:0    0 298.1G  0 disk 

Which is also confusing, as USB is not mentioned as SDB, but the CDROM.

---

### Post by oldfred on 2020-04-04
That is your  USB flash drive.
It looks like a 16 GB drive with the size of the ISO used.
Depending on how you make installer, it is configured as a hybrid DVD/flash drive. So partitions on drive may not even exist as it really looks like a DVD/CD. That is why you normally have to erase the beginning of a hybrid flash drive to reuse as standard partitioned drive.

You show a 298GB drive also as sda.
Is it just not partitioned & formatted? 
Perhaps you wrote the hybrid ISO using dd or similar tools which destroys partition table like it does on flash drives.
Then you only need to zero out the beginning of drive to be able to write a new partition table.

What does this show as it may read a backup gpt partition table at end of drive.

sudo gdisk -l /dev/sda

---

### Post by ase62 on 2020-04-04
> **oldfred said:**
> 
You show a 298GB drive also as sda.
Is it just not partitioned & formatted? 
Perhaps you wrote the hybrid ISO using dd or similar tools which destroys partition table like it does on flash drives.
Then you only need to zero out the beginning of drive to be able to write a new partition table.

What does this show as it may read a backup gpt partition table at end of drive.

sudo gdisk -l /dev/sda
Thank you oldfred. Yes, the SDA is the broken disk. It has many many physical errors, and the scan of DELL also confirms that there is a physical issue. This is the output of the command requested:

sda      8:0    0 298.1G  0 disk 
mint log # sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.1


Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sda: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): D3E4AFD2-EE9E-48AC-B58D-70D956799F33
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 2048-sector boundaries
Total free space is 625142381 sectors (298.1 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name

I have just acquired a new disk and I will receive it in 10 days. Same size (320 Gbytes).

---

### Post by Yellow Pasque on 2020-04-04
>  I will try to get the proper Toshiba Dell disk

The replacement doesn't need to be the exact same model. If you have the money, an SSD would be a nice upgrade. Maybe something like this: [https://www.opirata.com/p/disco-duro-ssd-240gb-sandisk-plus-sdssda-240g-g26](https://www.opirata.com/p/disco-duro-ssd-240gb-sandisk-plus-sdssda-240g-g26)
EDIT: And if you're going to use a mechanical hard disk, I'd highly recommend a 7,200RPM model. 5,400 RPM is okay for music/video storage and such, but 7,200RPM will give you a nice speed boost if you use the disk to run the OS.

---

### Post by ase62 on 2020-04-04
> **Yellow Pasque said:**
> The replacement doesn't need to be the exact same model. If you have the money, an SSD would be a nice upgrade. Maybe something like this: [https://www.opirata.com/p/disco-duro-ssd-240gb-sandisk-plus-sdssda-240g-g26](https://www.opirata.com/p/disco-duro-ssd-240gb-sandisk-plus-sdssda-240g-g26)
EDIT: And if you're going to use a mechanical hard disk, I'd highly recommend a 7,200RPM model. 5,400 RPM is okay for music/video storage and such, but 7,200RPM will give you a nice speed boost if you use the disk to run the OS.
I had already ordered the disk and it costed half of that cost. But 45 $ is not very expensive. I should have thought twice... My brother made this same comment after I told him about the problem. Is is possible to insert that disk exactly on a DELL Latitude E6430? My broken disk was a HDD2F23 disk (Toshiba). It has 4 pins to connect it to the laptop. Are the SSD similar?

---

### Post by Yellow Pasque on 2020-04-04
Yes, SSD's can be used in the SATA slot. If using a 7mm disk, you may run into a problem, but it can be solved by buying an adapter (or making your own): [https://www.dell.com/community/Laptops-General-Read-Only/SSD-disk-upgrade-compatibility-with-Latitude-E6420-E6430/td-p/4509043](https://www.dell.com/community/Laptops-General-Read-Only/SSD-disk-upgrade-compatibility-with-Latitude-E6420-E6430/td-p/4509043)

---

### Post by Yellow Pasque on 2020-04-04
Oh, and I guess I should give a warning about electrostatic discharge (ESD). Make sure you are properly grounded when handling parts.

---

### Post by ase62 on 2020-04-04
> **Yellow Pasque said:**
> Yes, SSD's can be used in the SATA slot. If using a 7mm disk, you may run into a problem, but it can be solved by buying an adapter (or making your own): [https://www.dell.com/community/Laptops-General-Read-Only/SSD-disk-upgrade-compatibility-with-Latitude-E6420-E6430/td-p/4509043](https://www.dell.com/community/Laptops-General-Read-Only/SSD-disk-upgrade-compatibility-with-Latitude-E6420-E6430/td-p/4509043)
OK. Thanks for the info.By now I will not cancel the order. Just 22 euros for 320 Gbytes is ok for me by now. But I don't discarg the SSD option in the future.

Once I receive the disk I will go back to this thread to comment :KS. Thanks a lot to all of you for the support. I really appreciate it.

---

### Post by Yellow Pasque on 2020-04-04
You're welcome. Keep us updated.

---

### Post by ase62 on 2020-04-13
Happy ending ;) I have received the disk today. I replaced it and installed a Linux Mint via USB and it works like a charm. The first thing I've done is to connect to this web to thank you all for helping me to solve and better understand the issue. I can't live without Linux!

---

