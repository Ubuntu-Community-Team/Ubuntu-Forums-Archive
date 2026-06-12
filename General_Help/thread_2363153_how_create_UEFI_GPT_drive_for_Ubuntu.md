---
title: "how create UEFI GPT drive for Ubuntu"
date: 2017-06-06
forum: General Help
---

### Post by Kris_M on 2017-06-06
Using offline Gparted.
I can make it gpt.
I can put a 512MB fat32 Partition at the front and flag it esp,boot - 
I can put a 10MB unformatted partition flagged bios-grub, use rescatux to redo grub and boot to my Ubuntu 16.04.2

---

### Post by Kris_M on 2017-06-06
EDIT - Okay, if I create that 256MB partition as fat32 flagged esp,boot, my mobo bios does indeed see it
It doesn't see anything bootable on it (when I switch CSM off).
Can I convert Ubuntu or do I have to rebuild it?

---

### Post by oldfred on 2017-06-06
Posted in your other thread.

 			 				[INDENT] 					You have to install the version of grub for UEFI boot.
That is grub-efi-amd64. 
Since booting in BIOS mode now, you have grub-pc.

 But you need the full uninstall/reinstall of grub if using Boot-Repair.
I think since you can boot, you just can from command line uninstall grub-pc and install grub-efi-amd64. 				
[/INDENT]

---

### Post by Kris_M on 2017-06-07
Thanks!!!
My search had led me right back to you (one of your pages) and I was prepping to do the Boot-Repair method when I heard your emails come in, so stopped and tried that.

> **oldfred said:**
> Posted in your other thread.[INDENT]                     You have to install the version of grub for UEFI boot.
That is grub-efi-amd64. 
Since booting in BIOS mode now, you have grub-pc.

 But you need the full uninstall/reinstall of grub if using Boot-Repair.
I think since you can boot, you just can from command line uninstall grub-pc and install grub-efi-amd64.                 
[/INDENT]


I don't understand why I need whole uninstall reinstall of Ubuntu if I go the Boot-Repair route.


See code below.
When I rebooted (it would only reboot in CSM mode) I was staring at a grub prompt.
I didn't know what to do so Clonezilla'ed SSD back to right before.

I need to uninstall, install efi,
But then I need to update the config or something and I don't know the commands.  <--- help!
And then reboot.
I'll stop for tonight anyway and check in tomorrow.

```
kris@kris-Z97X-UD3H:~$ sudo apt-get purge grub-pcReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.8.0-52 linux-headers-4.8.0-52-generic
  linux-image-4.8.0-52-generic linux-image-extra-4.8.0-52-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  grub-gfxpayload-lists* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 605 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 307303 files and directories currently installed.)
Removing grub-gfxpayload-lists (0.7) ...
Removing grub-pc (2.02~beta2-36ubuntu3.9) ...
Purging configuration files for grub-pc (2.02~beta2-36ubuntu3.9) ...
Processing triggers for man-db (2.7.5-1) ...
kris@kris-Z97X-UD3H:~$ sudo apt-get install grub-efi-amd64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.8.0-52 linux-headers-4.8.0-52-generic
  linux-image-4.8.0-52-generic linux-image-extra-4.8.0-52-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  grub-efi-amd64-bin
The following NEW packages will be installed:
  grub-efi-amd64 grub-efi-amd64-bin
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 724 kB of archives.
After this operation, 3,031 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 grub-efi-amd64-bin amd64 2.02~beta2-36ubuntu3.9 [658 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 grub-efi-amd64 amd64 2.02~beta2-36ubuntu3.9 [65.8 kB]
Fetched 724 kB in 0s (3,491 kB/s)        
Preconfiguring packages ...
Selecting previously unselected package grub-efi-amd64-bin.
(Reading database ... 307281 files and directories currently installed.)
Preparing to unpack .../grub-efi-amd64-bin_2.02~beta2-36ubuntu3.9_amd64.deb ...
Unpacking grub-efi-amd64-bin (2.02~beta2-36ubuntu3.9) ...
Selecting previously unselected package grub-efi-amd64.
Preparing to unpack .../grub-efi-amd64_2.02~beta2-36ubuntu3.9_amd64.deb ...
Unpacking grub-efi-amd64 (2.02~beta2-36ubuntu3.9) ...
Setting up grub-efi-amd64-bin (2.02~beta2-36ubuntu3.9) ...
Setting up grub-efi-amd64 (2.02~beta2-36ubuntu3.9) ...


Creating config file /etc/default/grub with new version
kris@kris-Z97X-UD3H:~$ 



```

---

### Post by oldfred on 2017-06-07
It looks like you have converted to UEFI boot.
You have to change in UEFI from CSM/BIOS/Legacy to UEFI. But need to have UEFI Secure Boot or perhaps "Windows" mode off. Use "Other" if that is an option.

If you want UEFI secure boot, you have to then install the signed versions of grub & kernel. And with Secure boot you cannot dual boot Windows, nor install any proprietary drivers which are binary blobs that Ubuntu then cannot sign and include in boot.

If you look at fstab it updated to add a mount of /boot/efi. 

cat /etc/fstab # only showing new entries
       16.04 fstab entry umask=0077
#UUID=D966-440A   /boot/efi       vfat    [COLOR=#ff0000]umask=0077[/COLOR]      0       1 
# Boot-Repair will do this, and I manually do this, comment out one above & add new below.
UUID=D966-440A    /boot/efi    vfat    [COLOR=#ff0000]defaults[/COLOR]    0    1

Ubuntu thru about 14.04 used defaults to mount ESP. But they now use umask=0077 which equals no permissions at all.

If you run Boot-Repair to convert, you have to use the advanced mode when booted in UEFI mode & check the full uninstall & reinstall of grub.  It then does the same as what you have just done. Then running Boot-Repair again would update fstab as then it sees you are in UEFI mode. And some have had issues running from inside system, so Boot-Repair needs to be from Ubuntu live installer.
It may be for security, so you did allow a rogue process it still could not write into the ESP and modify boot.
But I want to be able to edit, copy & backup the ESP, so I change it. Not sure how system does updates as even changing it back to defaults & remounting does not work. I have to reboot after changing to defaults to be able to see my ESP. I now change before rebooting after new install.

---

### Post by Kris_M on 2017-06-07
no, I must be missing something.
I did set mobo bios Win8 to "other", CSM support "always", Boot Mode "UEFI and legacy"

I ran
[FONT=Liberation Mono]sudoapt-get purge grub-pc[/FONT]
[FONT=Liberation Mono]sudoapt-get install grub-efi-amd64
and this time ran Grub Customizer to set up the menu, but when I booted it set me on memory test every time. If Boot Mode was set to UEFI only, it just said there was nothing to boot.

So again I Clonezilla'ed back to before.

```
[/FONT]# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=14f8bc13-3090-4bbf-96c0-1f30ea3ec99a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=81063bf1-430e-444b-bc48-c5e43a873ab3 none            swap    sw              0       0
# UUID=bfeeb626-5855-44d9-b91d-2c7a1ac72e4d /work ext4 defaults,noatime 0 2

UUID=01D195FDD65B0990 /media/E ntfs-3g defaults,noatime,windows_names,locale=en_US.utf8 0 0[FONT=Liberation Mono]
```
[/FONT]

---

### Post by oldfred on 2017-06-07
I have never used grub-customizer. I prefer to do whatever changes I want myself.
Customizer modifies grub scripts, which can cause some issues.

Before you restored with Clonezilla, it would have been good to see the full report from Boot-Repair. (and before any modification by Customizer).
When you installed grub-efi-amd64 did you get any errors?

On my system I have to set to UEFI only and make sure Secure boot is off. 

Since uninstalling grub-pc does not erase gpt's protective MBR, system may try to boot that in BIOS mode, but it then is misconfigured so would not work. Only UEFI boot would work correctly.

You should have been able to boot Boot-Repair in BIOS mode and reinstall grub-pc and boot without using Clonezilla.

---

### Post by Kris_M on 2017-06-07
On the previous attempt I did not use Grub Customized and booted to grub prompt - I have no real idea what to type there.  I believe it was booting in bios mode anyway.  I have never booted in UEFI mode

How does one set Secure mode to off?

No errors on grub install - code is embeded 5 posts back.

I just tried running BootRepair but it told me I had no EFI partition. pic attached.

Yeah I probably could have used Rescatux to fix the grub since Boot repair is complaining about the efi.

---

### Post by Kris_M on 2017-06-07
Okay - redid uninstall, install, grub config and selected correct switches and it booted fine.
However it is booting as bios.
It will not boot as UEFI (see pic)
Ubuntu says it's bios.

I think I have to mount it and then add a line to fstab but can't find how to mount it.


```
kris@kris-Z97X-UD3H:~$ cat /boot/config-4.8.0.53-generic | grep EFIcat: /boot/config-4.8.0.53-generic: No such file or directory
kris@kris-Z97X-UD3H:~$ cat /boot/config-4.8.0-53-generic | grep EFI
CONFIG_MODULE_SIG_UEFI=y
CONFIG_EFI_PARTITION=y
CONFIG_EFI=y
CONFIG_EFI_STUB=y
CONFIG_EFI_MIXED=y
CONFIG_EFI_SECURE_BOOT_SIG_ENFORCE=y
CONFIG_FB_EFI=y
CONFIG_XEN_EFI=y
CONFIG_DMI_SCAN_MACHINE_NON_EFI_FALLBACK=y
# EFI (Extensible Firmware Interface) Support
CONFIG_EFI_VARS=y
CONFIG_EFI_ESRT=y
CONFIG_EFI_VARS_PSTORE=m
# CONFIG_EFI_VARS_PSTORE_DEFAULT_DISABLE is not set
CONFIG_EFI_RUNTIME_MAP=y
# CONFIG_EFI_FAKE_MEMMAP is not set
CONFIG_EFI_RUNTIME_WRAPPERS=y
CONFIG_EFI_BOOTLOADER_CONTROL=m
CONFIG_EFI_CAPSULE_LOADER=m
CONFIG_EFI_TEST=m
CONFIG_UEFI_CPER=y
CONFIG_CACHEFILES=m
# CONFIG_CACHEFILES_DEBUG is not set
# CONFIG_CACHEFILES_HISTOGRAM is not set
CONFIG_EFIVAR_FS=y
CONFIG_EARLY_PRINTK_EFI=y
# CONFIG_EFI_PGT_DUMP is not set
CONFIG_EFI_SIGNATURE_LIST_PARSER=y
kris@kris-Z97X-UD3H:~$ 
kris@kris-Z97X-UD3H:~$ sudo fdisk -l /dev/sda
[sudo] password for kris: 
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: D4A450BA-6E94-404E-BB54-BF0E3BBBCAB9


Device         Start       End   Sectors  Size Type
/dev/sda1    2048000 106495999 104448000 49.8G Linux filesystem
/dev/sda2       2048     22527     20480   10M BIOS boot
/dev/sda3      22528    546815    524288  256M EFI System
/dev/sda4  233472000 241663999   8192000  3.9G Linux swap


Partition table entries are not in disk order.
kris@kris-Z97X-UD3H:~$                                                    
kris@kris-Z97X-UD3H:~$ sudo parted /dev/sda print
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name  Flags
 2      1049kB  11.5MB  10.5MB                        bios_grub
 3      11.5MB  280MB   268MB   fat32                 boot, esp
 1      1049MB  54.5GB  53.5GB  ext4
 4      120GB   124GB   4194MB  linux-swap(v1)


kris@kris-Z97X-UD3H:~$ 



```

---

### Post by oldfred on 2017-06-07
It seems like both Boot-Repair & UEFI are not correctly seeing your ESP. But it looks correct.
Gparted shows it as FAT32 and boot,esp flags.

You can try this, best from live installer.
 Must be unmounted
sudo dosfsck -t -a -w /dev/sda3
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

Some systems clearly say UEFI secure boot on/off. But it now seems many say "Windows" or "Other" And you have to use "Other" for Windows 7 as Windows 7 does not support UEFI Secure boot mode. Or that really is the Secure Boot on/off switch.
You may still have to say UEFI or UEFI only in another setting.

On my one motherboard it had the Windows & Other. And separate setting for UEFI boot of flash drive. Even UEFI or BIOS/CSM with UEFI as first did not boot flash drive in UEFI mode. Only a setting that said UEFI only would boot flash drive in UEFI. And then settings in UEFI to make sure UEFI on and CSM off.
       
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by Kris_M on 2017-06-07
Thanks
ran this
[COLOR=#000000]sudo dosfsck -t -a -w /dev/sda3

reboot
set to Other.
If set to UEFI only it gives message above.
Have to set boot mode to uefi and legacy. 
Ubuntu still bios.

Nope I think I have to mount it I try something recommended but get error
```
[/COLOR]kris@kris-Z97X-UD3H:~$ sudo mount -t auto /dev/sdb3 /mnt/test[sudo] password for kris: 
mount: mount point /mnt/test does not exist
kris@kris-Z97X-UD3H:~$ 


[COLOR=#000000]
```

also tried /boot/efi but same error, because of course there is no test or efi.

[/COLOR]

---

### Post by Kris_M on 2017-06-07
Okay, here I did a mkdir and then mounted sda3 - I wonder if I should put sda3 info in fstab?

/dev/sda3: UUID="4B38-0B85" TYPE="vfat" PARTUUID="68134018-e933-4790-af3e-12234f1eb69b"

UUID=4B38-0B85 /mnt/testefi vfat defaults 0 1





```
kris@kris-Z97X-UD3H:~$ sudo mkdir /mnt/testefi[sudo] password for kris: 
kris@kris-Z97X-UD3H:~$ sudo mount /dev/sda3 /mnt/testefi
kris@kris-Z97X-UD3H:~$ cd /mnt/testefi
kris@kris-Z97X-UD3H:/mnt/testefi$ l
kris@kris-Z97X-UD3H:/mnt/testefi$ sudo fdisk -l /dev/sda
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: D4A450BA-6E94-404E-BB54-BF0E3BBBCAB9




Device         Start       End   Sectors  Size Type
/dev/sda1    2048000 106495999 104448000 49.8G Linux filesystem
/dev/sda2       2048     22527     20480   10M BIOS boot
/dev/sda3      22528    546815    524288  256M EFI System
/dev/sda4  233472000 241663999   8192000  3.9G Linux swap




Partition table entries are not in disk order.
kris@kris-Z97X-UD3H:/mnt/testefi$ sudo parted /dev/sda print
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 




Number  Start   End     Size    File system     Name  Flags
 2      1049kB  11.5MB  10.5MB                        bios_grub
 3      11.5MB  280MB   268MB   fat32                 boot, esp
 1      1049MB  54.5GB  53.5GB  ext4
 4      120GB   124GB   4194MB  linux-swap(v1)




kris@kris-Z97X-UD3H:/mnt/testefi$ 
kris@kris-Z97X-UD3H:/mnt/testefi$ sudo blkid
/dev/sda1: UUID="14f8bc13-3090-4bbf-96c0-1f30ea3ec99a" TYPE="ext4" PARTUUID="8c17438a-3e18-498b-a37a-5bfe23a38f46"
/dev/sda3: UUID="4B38-0B85" TYPE="vfat" PARTUUID="68134018-e933-4790-af3e-12234f1eb69b"
/dev/sda4: UUID="81063bf1-430e-444b-bc48-c5e43a873ab3" TYPE="swap" PARTUUID="f2348f75-24b2-4dd8-9da4-3b8b93aa99ad"
/dev/sdb5: LABEL="ext600GB" UUID="295C8FD65351B20D" TYPE="ntfs" PARTUUID="655272b9-05"
/dev/sdb6: LABEL="E" UUID="01D195FDD65B0990" TYPE="ntfs" PARTUUID="655272b9-06"
/dev/sdb7: LABEL="PHONES" UUID="01D23D016F18BEC0" TYPE="ntfs" PARTUUID="655272b9-07"
/dev/sdc1: LABEL="extHG1T" UUID="01D1550FFBB41AD0" TYPE="ntfs" PARTUUID="000bba90-01"
/dev/sda2: PARTUUID="920ff280-dcf9-4a8c-80c3-58061e2c584d"
kris@kris-Z97X-UD3H:/mnt/testefi$ 





```

---

### Post by Kris_M on 2017-06-07
Okay, added that to fstab but ubuntu still says it's bios and it won't boot as UEFI.

[COLOR=#000000]UUID=4B38-0B85 /mnt/testefi vfat defaults 0 1[/COLOR]

---

### Post by oldfred on 2017-06-07
If you correctly installed grub-efi-amd64, it will automatically add the  mount of the efi partition. And you cannot have duplicate mounts, so do not add it again.

Is it showing /efi/ubuntu folder when seen from a live installer or BIOS boot?

My Asus had these UEFI settings:
 Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by oldfred on 2017-06-07
I just saw some info on another thread that is vital.
[https://askubuntu.com/questions/659988/how-do-i-install-grub-for-uefi-in-legacy-mode](https://askubuntu.com/questions/659988/how-do-i-install-grub-for-uefi-in-legacy-mode)
To get grub-efi-amd64 to correctly install, you must have the ESP mounted.
This may be why Boot-Repair is better as it is automatically doing the mount in background.

sudo mkdir /boot/efi
sudo mount /dev/sda3 /boot/efi

sudo grub-install --target=x86_64-efi /boot/efi
 Verify that there is a grubx64.efi somewhere in /boot/efi/ (eg. /boot/efi/ubuntu/grubx64.efi).  
sudo umount /dev/sda3/
Otherwise it cannot find location to install .efi boot files.

Also it should add an entry into UEFI, but I think you have to boot in UEFI mode to have efibootmgr.
To see UEFI boot entries.
sudo efibootmgr -v

---

### Post by Kris_M on 2017-06-07
YES - good catch!  That was what I was missing - mounting it and putting something in "there".  
My chain is /boot/efi/EFI/ubuntu with grubx64.efi

I then re-ran the install of efi grub which didn't do much.

I rebooted and changed mobo to boot to UEFI only and voila!  I also found "secure boot options will be shown when windows 8 is selected" - and since I selected "other" I'm fine.
Ubuntu now says "efi".

Interestingly it does NOT put anything in fstab.

Huge thanks for all your time and help!!!

Now off to try to document all this!


```
kris@kris-Z97X-UD3H:~$ sudo efibootmgr -v[sudo] password for kris: 
BootCurrent: 0026
Timeout: 1 seconds
BootOrder: 0020,0026
Boot0020* UEFI: Samsung SSD 840 EVO 250GB	PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,65535,0)/HD(3,GPT,68134018-e933-4790-af3e-12234f1eb69b,0x5800,0x80000)AMBO
Boot0026* ubuntu	HD(3,GPT,68134018-e933-4790-af3e-12234f1eb69b,0x5800,0x80000)/File(\EFI\UBUNTU\GRUBX64.EFI)
kris@kris-Z97X-UD3H:~$ 



```

---

### Post by Kris_M on 2017-06-07
[SIZE=3][FONT=garamond][COLOR=#222222]Summary:[/COLOR]
**[COLOR=#222222]_CHANGE FROM bios/mbr to UEFI/GPT_[/COLOR]**


**[COLOR=#222222]MBR to GPT and re-org drive:[/COLOR]**
[COLOR=#222222]#Clonezilla partition [/COLOR]**[COLOR=#222222]backup[/COLOR]**
[COLOR=#222222]#Gparted change to GPT (lose everything), [/COLOR]
[COLOR=#222222]-1GB space, 52GB ext4, 64GB space, 4GB swap (or whatever you want).[/COLOR]
[COLOR=#222222]in 1GB space put:[/COLOR]
[COLOR=#222222]-10MB unformatted flagged as bios-grub. [/COLOR]
[COLOR=#222222]-256MB FAT32 flagged as esp,boot (for efi).(sda3 in this example)[/COLOR]
[COLOR=#222222]#Clonezilla [/COLOR]**[COLOR=#222222]restore[/COLOR]**[COLOR=#222222] part.
[/COLOR]#Rescatux or Boot Repair - "easy" grub fix.
[COLOR=#222222]First boot is slow &#8211; sudo blkid to get UUID for swap and sudo gedit /etc/fstab and fix. Reboot.[/COLOR]


[COLOR=#222222]Assure mobo bios &#8220;other&#8221;(ie no secure boot).[/COLOR]


**[COLOR=#222222]Bios to UEFI:[/COLOR]**
[COLOR=#222222]oldfred: To get grub-efi-amd64 to correctly install, you must have the ESP mounted.[/COLOR]
[COLOR=#222222]This may be why Boot-Repair is better as it is automatically doing the mount in background.[/COLOR]

[COLOR=#222222]sudo mkdir /boot/efi[/COLOR]
[COLOR=#222222]sudo mount /dev/sda3  /boot/efi[/COLOR]

[COLOR=#222222]sudo grub-install --target=x86_64-efi  /boot/efi[/COLOR]
[COLOR=#222222]Verify that there is a grubx64.efi somewhere in /boot/efi/ (eg./boot/efi/ubuntu/grubx64.efi). [/COLOR]
[COLOR=#222222]sudo umount /dev/sda3/[/COLOR]
[COLOR=#222222]Otherwise it can not find location to install .efi boot files.[/COLOR]

[COLOR=#222222]Also it should add an entry into UEFI, but I think you have to boot in UEFI mode to have efibootmgr.[/COLOR]
[COLOR=#222222]To see UEFI boot entries.[/COLOR]
[COLOR=#222222]sudo efibootmgr -v  <- After you&#8217;ve booted UEFI[/COLOR]
[COLOR=#000000]-- -
[/COLOR][COLOR=#222222]Change the grub from bios to uefi:[/COLOR]
[COLOR=#222222]sudo apt-get purge grub-pc[/COLOR]
[COLOR=#222222]sudo apt-get install grub-efi-amd64[/COLOR]
[COLOR=#222222]Then I used grub customizer to set up the menu.[/COLOR]
[COLOR=#222222]Reboot and set mobo stuff: "Boot only UEFI".[/COLOR][/FONT][/SIZE]

---

### Post by oldfred on 2017-06-07
Glad you got it working. :)

---

### Post by Kris_M on 2017-06-08
Wouldn't have been possible without tons of help from you! Thanks!!! :D

---

