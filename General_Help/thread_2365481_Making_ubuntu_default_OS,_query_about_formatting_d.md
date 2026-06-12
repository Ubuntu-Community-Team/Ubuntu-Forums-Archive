---
title: "Making ubuntu default OS, query about formatting dev/sda2"
date: 2017-07-07
forum: General Help
---

### Post by plopmon on 2017-07-07
i have dual booted ubuntu with windows. but to boot ubuntu i have to go to boot device options at startup (F9). if i dont do anything (dont press esc) hp logo shows up then windows. i have formatted the windows C: drive and merged it with ubuntu. heres my partion table

NAME   FSTYPE     SIZE MOUNTPOINT               LABEL
loop1  squashfs  79.5M /snap/core/1689          
sr0              1024M                          
loop2  squashfs  79.5M /snap/core/2312          
loop0  squashfs     4K /snap/anbox-installer/17 
sda             465.8G                          
&#9500;&#9472;sda2 vfat       100M /boot/efi                
&#9500;&#9472;sda9 ext4         1M                          
&#9500;&#9472;sda7 ext4       267G /                        
&#9500;&#9472;sda5 ext4       940M                          
&#9500;&#9472;sda3 ext4        16M                          
&#9500;&#9472;sda1 ntfs       450M                          Recovery
&#9500;&#9472;sda8 swap       5.9G [SWAP]                   
&#9492;&#9472;sda6 ntfs     191.4G                          New Volume
**i**** want to get rid of windows TOTALLY**. is it safe to formtat dev/sda2 ? if no then please suggest other ways. and how i can make ubuntu my default os. (I DONT WANT TO PERFOMR A CLEAN INSTALL)

---

### Post by RobGoss on 2017-07-07
Hello and welcome to the forum, At this point I would have to say a clean installation would be the best option, but that's just my recommendation. I still see a few Windows partitions, **ntfs 450M** Recovery, **ntfs 191.4G New Volume**. I am certain if you delete sda2 vfat 100M /boot/efi  you will have problems booting in to your system.

A clean installation would be best to do and should be straight forward. Make a full backup of any important data and just use the entire disk for your new install

---

### Post by yancek on 2017-07-07
sda2 is the EFI partitiion with boot files so deleting it will render the system unbootable.  Post some info starting with booting Ubuntu and opening a terminal and running the command below and posting the output here:

```
sudo efibootmgr
```

The above output should tell us whether you have an entry for ubuntu and should also show the boot options as well as the priority which you can change with the proper parameter using that command.

---

### Post by oldfred on 2017-07-07
UEFI has NVRAM so it remembers settings and the ESP - efi system partition (your sda2) has boot files for both Windows & Ubuntu. 
So you need to remove the Windows entries from NVRAM and remove the /EFI/Microsoft folder from the ESP. You probably need to use live installer in live mode to edit the ESP as install has settings in fstab that prevent editing.

What brand/model system?
Some computers only boot the Windows entry. The violate UEFI standard and use description as part of boot. But since using description, we can change the description of the grub/Ubuntu boot (ubuntu entry) to "Windows Boot Manager" and boot Ubuntu using Windows description. They do not check actual boot file.

---

### Post by plopmon on 2017-07-07
> **yancek said:**
> sda2 is the EFI partitiion with boot files so deleting it will render the system unbootable. Post some info starting with booting Ubuntu and opening a terminal and running the command below and posting the output here:

```
sudo efibootmgr
```

The above output should tell us whether you have an entry for ubuntu and should also show the boot options as well as the priority which you can change with the proper parameter using that command.

Here's the result


BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 3003,3001,3004,2001,2002,2003
Boot0000* Notebook Hard Drive
Boot0001* Ubuntu
Boot0003* Windows Boot Manager
Boot0004* ubuntu
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3001* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk
Boot3004* Internal Hard Disk or Solid State Disk

> **oldfred said:**
> UEFI has NVRAM so it remembers settings and the ESP - efi system partition (your sda2) has boot files for both Windows & Ubuntu. 
So you need to remove the Windows entries from NVRAM and remove the /EFI/Microsoft folder from the ESP. You probably need to use live installer in live mode to edit the ESP as install has settings in fstab that prevent editing.

What brand/model system?
Some computers only boot the Windows entry. The violate UEFI standard and use description as part of boot. But since using description, we can change the description of the grub/Ubuntu boot (ubuntu entry) to "Windows Boot Manager" and boot Ubuntu using Windows description. They do not check actual boot file.

My computer model is HP 2000 Notebook in which i installed Windows 10. and hard disk has also been changed.

> **RobGoss said:**
> Hello and welcome to the forum, At this point I would have to say a clean installation would be the best option, but that's just my recommendation. I still see a few Windows partitions, **ntfs 450M** Recovery, **ntfs 191.4G New Volume**. I am certain if you delete sda2 vfat 100M /boot/efi you will have problems booting in to your system.

A clean installation would be best to do and should be straight forward. Make a full backup of any important data and just use the entire disk for your new install

I don't want to do a clean install because i don't have time to do that. and **New Volume **is my apparent Windows E: Drive in which my precious data is there but i cant access it because my windows is unable to boot leading to no proper shutdown of hard drvie (the windows part) again leading to :[I]

Error mounting /dev/sda6 at /media/[/I]*jayant**/New Volume: Command-line `mount -t "**ntfs**" -o "uhelper=udisks2,**nodev**,**nosuid**,uid=1000,gid=1000" "/dev/sda6" "/media/**jayant**/New Volume"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).**Metadata kept in Windows cache, refused to mount.*
*Failed to mount '/dev/sda6': Operation not permitted*
*The NTFS partition is in an unsafe state. Please resume and shutdown*
*Windows fully (no hibernation or fast restarting), or mount the volume*
*read-only with the '**ro**' mount option*


i would appreciate if you can also help with it....

---

### Post by oldfred on 2017-07-07
When Windows fast boot or hibernation is on, then all NTFS partitions are always mounted even when shutdown. Linux will not mount read/write a hibernated NTFS partition since it may damage it or data disappears as hibernation will not see new data.

You may be able to mount read only. But better to use Windows and turn off the hibernation.
If not keeping Windows best not to use NTFS as you need Windows to do maintenance on NTFS partitions.

       Read only mount of Windows may work if corrupted or hibernated replace sda# with correct drive.
sudo mkdir /mnt/win
sudo mount -o ro /dev/sda# /mnt/win
gksu nautilus /mnt/win 

You may have to install gksu.

---

### Post by RobGoss on 2017-07-07
> I don't want to do a clean install because i don't have time to do that. and New Volume is my apparent Windows E: Drive in which my precious data is there but i cant access it because my windows is unable to boot leading to no proper shutdown of hard drvie (the windows part) again leading to :

Do you still have a Windows recovery disk for reinstalling Windows? and what version of Windows did you have installed on your machine. This may help you recover your data and if you don't want Windows after that you can just use the Windows partition space for Ubuntu

The MS website should have a Windows ISO file that you can download, I'm almost certain you will need to have a valid registered Windows licence to use it

---

### Post by yancek on 2017-07-07
The following command should put Ubuntu first in boot priority although following the advice by oldfred and others above will probably be necessary to get rid of the windows entries.

```
sudo efibootmgr -o 0001
```

You can then put the other entries on that line in the order you want them, comma separated list of 4 digit codes.  I just noticed a potential problem in that you have two ubuntu entries (0001 and 0004)?

---

### Post by plopmon on 2017-07-08
> **oldfred said:**
> When Windows fast boot or hibernation is on, then all NTFS partitions are always mounted even when shutdown. Linux will not mount read/write a hibernated NTFS partition since it may damage it or data disappears as hibernation will not see new data.

You may be able to mount read only. But better to use Windows and turn off the hibernation.
If not keeping Windows best not to use NTFS as you need Windows to do maintenance on NTFS partitions.

Read only mount of Windows may work if corrupted or hibernated replace sda# with correct drive.
sudo mkdir /mnt/win
sudo mount -o ro /dev/sda# /mnt/win
gksu nautilus /mnt/win 

You may have to install gksu.

before installing Ubuntu, i somehow managed to log in to windows and disable fast startup. its disabled even in BIOS

> **RobGoss said:**
> Do you still have a Windows recovery disk for reinstalling Windows? and what version of Windows did you have installed on your machine. This may help you recover your data and if you don't want Windows after that you can just use the Windows partition space for Ubuntu

The MS website should have a Windows ISO file that you can download, I'm almost certain you will need to have a valid registered Windows licence to use it

so you mean to say that i should reinstall windows and then extract data from New VOlume?

---

### Post by johndough2 on 2017-07-08
Hi

My experience with HP is that the boot areas are accessed alphabetically.

Boot0000* Notebook Hard Drive
Boot0001* Ubuntu
Boot0003* Windows Boot Manager
Boot0004* ubuntu

Therefore I name mine to suit, so renaming the Windows Boot Manager to Microsoft Boot Manager moves it up the batting order, ahead of Ubuntu.

Equally things like zzzdebian puts them last.

So Gparted and rename the appropriate areas should yield results.

---

### Post by plopmon on 2017-07-08
> **yancek said:**
> The following command should put Ubuntu first in boot priority although following the advice by oldfred and others above will probably be necessary to get rid of the windows entries.

```
sudo efibootmgr -o 0001
```

You can then put the other entries on that line in the order you want them, comma separated list of 4 digit codes. I just noticed a potential problem in that you have two ubuntu entries (0001 and 0004)?


this command worked but after i installed ubuntu even i was wondering why there were 2 ubuntu entries. one had Ubuntu and the other was ubuntu.

---

### Post by RobGoss on 2017-07-08
> i have dual booted ubuntu with windows. but to boot ubuntu i have to go to boot device options at startup (F9). if i dont do anything (dont press esc) hp logo shows up then windows. i have formatted the windows C: drive and merged it with ubuntu. heres my partion table

In your first post I'm a bit lost, what are you trying to accomplish here?

Are you having trouble dual booting your system?

Are you not seeing the Grub menu at startup to choose between the two operation systems?

---

### Post by yancek on 2017-07-08
> this command worked but after i installed ubuntu even i was wondering  why there were 2 ubuntu entries. one had Ubuntu and the other was  ubuntu. 				

I would expect multiple attempts to install or make modifications in the EFI partition.  You can probably delete one, most likely the one with the uppercase Ubuntu as you indicate you used the lower case 0001 to boot.  The link below gives an example of deleting an entry with an explanation of the parameters used.

[https://wiki.gentoo.org/wiki/Efibootmgr#Deleting_a_boot_entry](https://wiki.gentoo.org/wiki/Efibootmgr#Deleting_a_boot_entry)

---

### Post by Dennis N on 2017-07-08
> I would expect multiple attempts to install or make modifications in the EFI partition. You can probably delete one, most likely the one with the uppercase Ubuntu as you indicate you used the lower case 0001 to boot.

You get two from the installer. I've read that shimx64.efi (for secure boot policy) will utilize grubx64.efi (grub2 boot loader), so I keep them as created by the installer. The folders are the same to the EFI boot manager since it is not case sensitive.

```
dmn@Zotac:~$ sudo efibootmgr -v | grep ubuntu
Boot0000* ubuntu	HD(1,800,28000,adf95091-cfe2-4af6-a0e0-9df450300d37)File(\EFI\ubuntu\shimx64.efi)
Boot0002* ubuntu	HD(1,800,28000,adf95091-cfe2-4af6-a0e0-9df450300d37)File(\EFI\Ubuntu\grubx64.efi)

```

---

### Post by yancek on 2017-07-08
Interesting.  Running the command above shows only one ubuntu directory in the efi partition with both those files as well as others.  Maybe because I had Secure Boot off during the install?

> ls ubuntu/
bootx64.efi*  fbx64.efi*  fw/  fwupx64.efi*  grub.cfg*  grubx64.efi*  mmx64.efi*  shimx64.efi*


---

### Post by Dennis N on 2017-07-08
> **yancek said:**
> Interesting.  Running the command above shows only one ubuntu directory in the efi partition with both those files as well as others.  Maybe because I had Secure Boot off during the install?

I have only one ubuntu directory as well, with those two targets both in there. 'Ubuntu' and 'ubuntu' are the same directory to the EFI boot manager.

My EFI system partition on this machine:

```
dmn@Sydney:/boot/efi/EFI$ tree
.
&#9500;&#9472;&#9472; boot
&#9474;** &#9492;&#9472;&#9472; grubx64.efi
&#9500;&#9472;&#9472; Manjaro
&#9474;** &#9492;&#9472;&#9472; grubx64.efi
&#9492;&#9472;&#9472; ubuntu
    &#9500;&#9472;&#9472; fw
    &#9500;&#9472;&#9472; fwupx64.efi
    &#9500;&#9472;&#9472; grub.cfg
    &#9500;&#9472;&#9472; grubx64.efi
    &#9500;&#9472;&#9472; mmx64.efi
    &#9500;&#9472;&#9472; MokManager.efi
    &#9492;&#9472;&#9472; shimx64.efi

4 directories, 8 files
```

Ubuntu is set up to handle secure boot if it is on because of shimx64.efi. Manjaro does not have secure boot.

---

### Post by plopmon on 2017-07-09
> **yancek said:**
> The following command should put Ubuntu first in boot priority although following the advice by oldfred and others above will probably be necessary to get rid of the windows entries.

```
sudo efibootmgr -o 0001
```

You can then put the other entries on that line in the order you want them, comma separated list of 4 digit codes. I just noticed a potential problem in that you have two ubuntu entries (0001 and 0004)?

this command did worked but heres the result:

BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 3003,3001,3004,2001,2002,2003
Boot0000* Notebook Hard Drive
Boot0001* Ubuntu
Boot0003* Windows Boot Manager
Boot0004* ubuntu
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3001* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk
Boot3004* Internal Hard Disk or Solid State Disk


in BIOS boot menu it shows number 1 : OS Boot Manager
number 2: Ubuntu


should i use that code again and instead of 0001 i should rather do 0000?

---

### Post by plopmon on 2017-07-09
> **RobGoss said:**
> In your first post I'm a bit lost, what are you trying to accomplish here?

Are you having trouble dual booting your system?

Are you not seeing the Grub menu at startup to choose between the two operation systems?

You can say that im having trouble dual booting my PC **coz i am not seeing GRUB menu at startup.  to boot to ubuntu i have to do the F9 thingy. by default windows is loaded **

---

### Post by RobGoss on 2017-07-09
So you no longer have Windows on this machine correct?

It sounds to me like you've installed Ubuntu is **Legacy **mode and Windows is installed in **UEFI**, if this is the case then that would explain why you're are not able to dual boot correctly. I have linked two community pages that may be of help understanding how dual booting and installing Ubuntu in UEFI mode works

I've posted something that might help with future installations

Using UEFI Mode
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Dual booting Windows and Ubuntu 
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

You can also run the **boot repair **script in my signature and post back the results with the link that's provided this will help others trouble shoot your

---

### Post by yancek on 2017-07-09
In post # 17, you have the output of your efibootmgr command as below:

```
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 3003,3001,3004,2001,2002,2003
Boot0000* Notebook Hard Drive
Boot0001* Ubuntu
Boot0003* Windows Boot Manager
Boot0004* ubuntu
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3001* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk
Boot3004* Internal Hard Disk or Solid State Disk
```

Notice that it shows BootCurrent:0001 but on the BootOrder line you do not have either Ubuntu(0001) or ubuntu(0004) but have 3003 which is one of the SSD drives which I expect is you windows so it doesn't appear that any change was made.  Running that command on my laptop I see the following:

```
efibootmgr
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0002,3002,0004,0000,2001,2002,2004
Boot0000* Notebook Hard Drive - TOSHIBA MQ01ABD100
Boot0002* ubuntu

```

The difference you can see is that BootCurrent is 0002 and that BootOrder shows 0002 as the first entry.  Have you tried setting 0004 as first with the efibootmgr command?  You might try that and then run just efibootmgr immediately after to see if you get a change on the BootOrder line. No need to reboot to test if there is no change.  Also, have you mounted the EFI partition to see what you have there for Ubuntu?  Have you tried the suggestions above by oldfred?  If none of this works, you may need to run the boot repair software and select the option to Create BootInfo Summary and post a link to the output here to get help.

---

