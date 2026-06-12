---
title: "How to dual boot ubuntu 16.04 with windows 10 previously installed on dell 5577"
date: 2018-05-30
forum: General Help
---

### Post by neo-atul45 on 2018-05-30
hey 
I am having dell 5577 128 SSD + 1 TB HDD and windows 10 previously installed on SSD plz also tell me how to install  ubuntu on 1 TB HDD
I have windows 10 in leagcy mode in 128 gb-ssd and i want to have ubuntu in 1TB harddrive in legacy mode
i also tried it firstly i booted live usb in legacy mode by putiing secure boot and fast boot off ,,
When i clicked on try ubuntu is just freezes ,,and i googled and found a  way using nomodeset parameter ,,firstly when the pink screen with mouse  and keyboard on bottom i clicked any key and then selected language and  then the screen appears which shows option of "Try ubuntu" "Install  Ubuntu" and many others then i clicked F6 and set nomodeset parameter  and then click on install ubuntu
After this the purple screen doesn't freeze for me and i tried install ubuntu ..
I follow the few steps but i had a doubt that in installation type of  ubuntu i was not getting an option of install ubuntu alongside windows  10 while i have windows 10 OS ...
I was confused and thus choose something else option..
In that i initially through a partition of Harddisk (1 TB) of 200 gb so i  had that amount of free space and now i created partitions from  sdb(Harddrive)
I made the following partitions:

S.No.      SiZE       MOUNT POINT    USE AS
1.            55GB            /                        Ext4
2.            16GB                                    Swap
3.            30MB                                    Reserved Bios Area
4.            500MB          /boot                 Ext4
5.        around 143GB   /home Ext4
i made all this partitions from free space which i created 
Now after this i also had a doubt that "device for bootloader" i don't  know what to choose so remained it as by default sda(my ssd) ..
In the further steps of installing i got this error:
Unable to install GRUB in /dev/sda
Executing `grub-install /dev/sda` failed.
This is a fatal error.

I dont knew what to do so i shutdown my laptop and again proceeded the same way as above just this time i changed
the "device for bootloader" to sdb(1 TB harddrive) ,,now the installation process gets completed...
so I booted in legacy mode and ubuntu purple screen starts loading and got freeze ..
I rebooted my laptop and press esc and found grub there on Ubuntu i pressed e and add nomodeset in the line which
has "quiet splash" and then F10 to reboot
I loaded in ubuntu but its lagging i thought it may be because of some video drivers so i installed the lastest 
nvidia 390 driver on it and when i rebooted but now i am not able to login the ubuntu ..
I just fill the passwaord then a black screen appear and then again login screen appear ...
I am trapped in here Please hElp me,,,,
Or please tell me another way to dual boot my ubuntu 16.04LTS 
PLZ PLZ help me out..

---

### Post by QIII on 2018-05-30
Moved to General Help

---

### Post by oldfred on 2018-05-31
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Do not run auto fix with Boot-Repair, only use advanced mode where you can choose an install and drive to install boot loader into.

If BIOS installs, you want Windows boot loader on Windows drive and Ubuntu/grub boot loader on Ubuntu drive (not partitions).
Also if Ubuntu on gpt partitioned drive and BIOS/Legacy install, you need a 1 or 2MB unformatted space with the bios_grub flag. If UEFI you need an ESP - efi system partition. I typically used both when still using BIOS and knew I soon would be converting to UEFI. Then I did not have to totally reconfigure drive for UEFI boot.

---

