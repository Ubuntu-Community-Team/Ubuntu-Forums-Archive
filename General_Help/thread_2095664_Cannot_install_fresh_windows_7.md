---
title: "Cannot install fresh windows 7"
date: 2012-12-17
forum: General Help
---

### Post by Imh0tep on 2012-12-17
Hello everyone,):P

I recently installed Ubuntu via bootable flash over my Windows 7 just to get a fresh install and I was going to full time convert to Ubuntu. But now I want to do a fresh Windows 7 install via flashdrive because I have no dvd player and I just always boot into Ubuntu.  I have tried WintoFlash, Ubootin, The windows 7 official bootable usb maker that I made on a friends Windows and every time it just boots into Ubuntu.  I have tried making the USB as first boot in bios, used F12(My boot menu) to try and boot it from there and I even reformatted the usb to Fat32 and tried NTFS.  I am really confused on what to do here.  Like I said I want to just wipe the whole thing and reinstall a windows. Any help is very appreciated, thank you.

I use the most recent version of Ubuntu and AMD64 version.

---

### Post by Mark Phelps on 2012-12-17
The Windows USB boot tool is generally reliable -- so I would first, try the bootable USB on your friend's Windows PC to confirm that it boots there.

If you don't want to do that, then disconnect the hard drive from your PC, stick in the USB -- and confirm it boots.  

IF it does, your PC is NOT reading the USB stick when the hard drive is connected -- which will require more fiddling with the BIOS settings to try to fix that.

---

### Post by Imh0tep on 2012-12-17
I just tried the USB without the HD and it booted to windows install just fine.  I have a Gigabyte EP43-DS3L if that helps because you mentioned Bios. So its not the flashdrive.

---

### Post by oldfred on 2012-12-17
Do you have a primary NTFS formatted partition with the boot flag (active partition in Windows) for Windows to install into? It needs the active partition, a totally blank drive or enough unallocated to create primary partitions for its install. It often works better if first partition sda1, but should install to any primary sda1 thru sda4 if MBR.

If UEFI with gpt partitioning, its all different.

Post this in code tags to preserve formatting:
       sudo parted /dev/sda unit s print

---

### Post by Imh0tep on 2012-12-17
All I have is one partition as my whole HD. Isnt there a way where I can just install over that?  I think their is one way where I can use a Live Ubuntu USB to wipe it?

---

### Post by oldfred on 2012-12-17
You can just use gparted from LiveCD to erase partition. Or any other partition tools. 
But Windows does not see Linux partitions so I do not know if it will even work unless you erase in advance.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Imh0tep on 2012-12-18
Im on a live cd now. I tried to just format the whole HD to just NTFS and now it says it cannot recognize the file type, then below it says GRUB rescue.

---

### Post by oldfred on 2012-12-18
Grub rescue is from Hard drive.

Did you format to NTFS and put boot flag on the partition. But gparted may format it as XP NTFS which may then need reformatting by Windows 7.

Are you sure your Windows 7 is a full valid install DVD or flash drive installer? If BIOS is not booting it and going to hard drive to boot, then your Windows does not seem like it is bootable.

---

### Post by Imh0tep on 2012-12-18
I formatted it to NTFS.  I am using a flash drive. If the hard drive is disconnected from my computer, then the Windows installer will start. Other wise I get that grub error. I have no data on the Hard Drive for I reformatted the whole thing.

Edit: Yes the boot flag is on it.

---

### Post by Imh0tep on 2012-12-18
[http://paste.ubuntu.com/1446885/](http://paste.ubuntu.com/1446885/)

From when  I tried to fix the boot.

---

### Post by oldfred on 2012-12-18
The only other alternative is to totally erase drive. From gparted just delete sda1. 

Otherwise some in BIOS is ignoring USB boot and booting hard drive first. Some computers require both BIOS change of boot order and one time key (f12 on my system) to choose USB. Also some computers boot USB flash drives as another hard drive, choose hard drive not as USB device.

---

### Post by Imh0tep on 2012-12-18
I deleted everything and reformatted as ntfs, still the same thing happened with the grub.  I made sure my bios is set to boot from USB and I used f12 to boot from usb, still I cannot install windows.

---

### Post by oldfred on 2012-12-18
Then it seems your Windows disk is not a full install disk?

---

### Post by churchy d on 2012-12-18
just want to verify...

you have a ubuntu usb flash drive  and a windows installer usb flash drive .  you are currently using the ubuntu usb flash drive to post on the forums as you have already reformatted your computers hard drive and it starts up just fine each time.  when you try to boot the windows installer usb flash drive, it just pops up with a grub error if the hard drive is left in, if the hard drive is removed, then the installer starts right up.  

my thinking is that the windows installer usb flash drive is detecting the hard drive and trying to boot that.  usually windows disks pop up with a message and offer you a few seconds at the beginning in which you need to press any key to boot off the disk or in this case flash drive. by the way always press space bar, some of the keys dont work here if i remember right, such as shift or control or escape. if you dont press a key, then it boots off other media in the computer if available. if nothings available, then it should boot off the windows installer.  Next time you try, keep pressing space bar while as the computer leaves the bios screen.  It should boot the installer.  If not, then I have another idea.

Next I would try zeroing out the first portion of your hard drive which would erase the partition table completely.   Which would mean the installer would not recognize that hard drive as bootable and should default back to booting itself as the only option.  the windows installer is completely capable of partitioning and formatting the hard drive on its own.  Load up the ubuntu flash drive and figure out which device is the hard drive.  should be /dev/sdb or something like that.  /dev/sda would likely be the flash drive its running off of.

THIS WILL EFFECTIVELY ERASE ALL DATA ON WHATEVER DEVICE YOU TELL IT TOO.
Just to make sure, there is no data on this drive at all that you want to save, right?
If you have any other hard drives, disconnect them if you are in the least unsure as to which drive you should zero.

replace sdX in the following command with your device.  After you hit enter, count to 10 and press CTRL-C.  All we are trying to do here is zero out the partition table which is at the beginning of the disk.  The counting to 10 allows for the hard drive to spin up in case it had gone to sleep

```
sudo dd if=/dev/zero of=/dev/sdX
```

good luck.

---

### Post by Imh0tep on 2012-12-18
Thank you everyone! I finally fixed it.  My BIOS wasnt saving the settings for when I tried to make the flash drive as the first boot.  I changed the battery on my MB and now it works.  Thank you!!!!

---

