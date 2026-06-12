---
title: "Finding Grub boot files on multiple boot systems ?"
date: 2017-04-29
forum: General Help
---

### Post by garyed on 2017-04-29
I've been trying to find the answer myself to this question for a long time & have not found a good way to do it. When you have multiple versions of Linux that use Grub whether it be different Ubuntu versions or other distributions, finding where the actual partition where the grub boot files are stored can get complicated. I've tried using bootinfoscript & maybe I'm missing something but i don't see where it tells you. The only thing I've been able to come up with is to actually view all grub.cfg files in every partition & see which one looks like the correct boot screen you see on start up.  That may be OK for preparation but if you couldn't view the start up screen how would you know which partition held the grub files used to bot up? It seems there should be a simple way to do it that I'm just missing. Am I?

---

### Post by Dennis N on 2017-04-29
General rule: The last OS you installed is the one that generates and displays the grub menu. After you make a selection from the grub menu, is starts the kernel in the selected OS and transfers control to it to complete the startup.

The grub files being used to boot to the menu are in the file system of that last-installed OS*, or if UEFI, some files will also be in the EFI system partition.

*and some code in the MBR to point to the location of that OS.

---

### Post by garyed on 2017-04-29
I understand that but sometimes you don't always remember when you have a bunch of OS's which one was the last. I like to make a totally custom grub menu & change things around every once in a while so i thought it would be nice if there was a command that would tell you the partition where the actual grub files are that are used to boot the system.

---

### Post by Dennis N on 2017-04-29
It's a good idea to create labels when you install each OS. If you have multiple computers around, and several OS on each, it is easy to lose track. gparted run from any OS on the computer will display the labels, or from the terminal where this command displays the partitions and OSes on sda (in this example):

```
dmn@Sydney:~$ sudo blkid | grep sda
/dev/sda1: LABEL="EFI" UUID="1291-ACCB" TYPE="vfat" PARTLABEL="EFI-System-Partition" PARTUUID="a1e435e2-5bbe-47f1-af26-a8efc2b58fd1"
/dev/sda2: LABEL="Xubuntu-1404" UUID="297ecb14-ecb9-4ddb-8331-0f6c6cb9342f" TYPE="ext4" PARTLABEL="Xubuntu-1404" PARTUUID="088e3b72-11c5-408f-b3dd-b55f8c8875c4"
/dev/sda3: UUID="391dcd7b-ca92-4cfb-98e4-4619ea27aa96" TYPE="swap" PARTUUID="5688bc18-12b6-48ac-ae27-fba81e600e58"
/dev/sda4: LABEL="Common-Files" UUID="d97e2feb-1bf6-429b-bba5-943264ec1474" TYPE="ext4" PARTLABEL="Common-Files" PARTUUID="8437389c-d640-4a69-a337-e87e5ed68346"
/dev/sda5: LABEL="Xubuntu-1604" UUID="8ff61c40-2fa7-4789-8021-ae85bf7b4834" TYPE="ext4" PARTLABEL="Xubuntu-1604" PARTUUID="041d0530-56bd-44c5-9ddd-a01e6f2d03e7"
/dev/sda6: LABEL="Lubuntu-1704" UUID="b63ed986-c740-4eff-ac69-5d1c109d335f" TYPE="ext4" PARTLABEL="Lubuntu-1704" PARTUUID="25b6c226-b520-46be-88e1-ef730d47ae79"
```

I have been using custom menu entries for a long time. The method to make a custom grub menu is explained here:

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by Bashing-om on 2017-04-29
garyed; Hello;

How about:
> 
 a command that would tell you the partition where the actual grub files are that are used to boot the system.

```

sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub
sudo grub-probe -t fs_uuid /boot/grub
sudo lshw -C Disk -short
sudo debconf-show grub-pc # will show you full details.

```
Take your pick for what works for the use case - there are many other ways to see what grub has set .

[INDENT][INDENT]all in how you ask the system
[/INDENT][/INDENT]

---

### Post by garyed on 2017-04-29
I like that idea.
I never thought of it before but I guess the only true way to know where the actual grub boot files are located would be for a command to actually read the MBR or EFI  boot sector & get it from there. That would be a pretty neat command to come up with.

---

### Post by oldfred on 2017-04-29
If MBR, Boot-Repair shows the MBR and which partition it the MBR looks to for rest of grub.

If UEFI, there is a grub.cfg in the ESP - efi system partition and that is a configfile 3 line set of command that refer to the UUID & partition of the grub used to boot.

But I turn off os-prober, make sure the version of Ubuntu I mostly boot is default and add the other entries with my own descriptions into 40_custom.
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by Dennis N on 2017-04-29
> **garyed said:**
> I like that idea.
I never thought of it before but I guess the only true way to know where the actual grub boot files are located would be for a command to actually read the MBR or EFI  boot sector & get it from there. That would be a pretty neat command to come up with.

Since you mentioned "different Ubuntu versions or other distributions" in the first post, it's probably worth noting that once you leave Ubuntu Land and its Debian base, commands can vary. Also, EFI system partition files help find the OS partition with Ubuntu, but may not for other distros. For example, on my current machine is Manjaro, a Linux distro based on Arch Linux. It has only two files in the EFI system partition: grubx64.efi, and bootx64.efi. Neither is readable, so no help there.

---

### Post by ajgreeny on 2017-04-29
One possible way to see which OS is managing grub would also be to make sure that you edit the line in /etc/default/grub 
```
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
```
and change it to the appropriate named version of *ubuntu for each OS that you use, ie in my case
```
GRUB_DISTRIBUTOR="Xubuntu-16.04"
```
I always use the double quote marks as shown but I am not sure if that is needed; the single quotes as shown in the original line may also work but I've never tried.

Now run ```
sudo update-grub
``` and the next time you see the grub menu at boot it will show the Xubuntu-16.04 line and not the usual same line for all *ubuntu based family OSs, so will be able to see immediately which OS is managing the grub you are actually using.

It is too long since I used a non-ubuntu OS now so I am uncertain how other distros might deal with this naming procedure, but it may work for all; I simply do not know.
However they will certainly all name the first OS in the menu as, for example, Suse, manjaro etc etc, so only if you have more than one version of Suse or manjaro will this cause a problem, as that will immediately tell you which is managing grub.

---

### Post by Dennis N on 2017-04-29
> It is too long since I used a non-ubuntu OS now so I am uncertain how other distros might deal with this naming procedure, but it may work for all; I simply do not know.

I looked, and the same method is used by Manjaro and Fedora to identify itself - the two non-Debian based distros that I have installed. So that is a good way to sort out what any grub entry will boot if you aren't going for the custom menu setup. I also include the partition in my descriptions:

"Xubuntu 16.04 on sda6" for example.

---

### Post by garyed on 2017-04-29
> **oldfred said:**
> If MBR, Boot-Repair shows the MBR and which partition it the MBR looks to for rest of grub.

If UEFI, there is a grub.cfg in the ESP - efi system partition and that is a configfile 3 line set of command that refer to the UUID & partition of the grub used to boot.

But I turn off os-prober, make sure the version of Ubuntu I mostly boot is default and add the other entries with my own descriptions into 40_custom.
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

I looked in my EFI system partition but couldn't find any grub.cfg file.
All i could find was a Recycle.bin  & a System Volume information folder containing a tracking.log

---

### Post by garyed on 2017-04-29
> **Bashing-om said:**
> garyed; Hello;

How about:

```

sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub
sudo grub-probe -t fs_uuid /boot/grub
sudo lshw -C Disk -short
sudo debconf-show grub-pc # will show you full details.

```
Take your pick for what works for the use case - there are many other ways to see what grub has set .

[INDENT][INDENT]all in how you ask the system
[/INDENT][/INDENT]

I tried all of those commands & they just showed where the grub files were of the current partition I had booted into not which partition held the actual grub files that was being used to boot.

---

### Post by Bashing-om on 2017-04-29
garyed; Humm.

> **garyed said:**
> I tried all of those commands & they just showed where the grub files were of the current partition I had booted into not which partition held the actual grub files that was being used to boot.

```

sysop@x1604:~$ sudo grub-probe -t device /boot/grub
/dev/sda1
sysop@x1604:~$ 

```
where the sda1 partition -in my case - holds /boot ->
```

ls -al /boot/

```
contains /grub
```

ls -al /boot/grub/

```
contains grub's 2nd stage files.

So, I guess I need to ask you to clarify my miss-understanding of what you seek .

[INDENT][INDENT]one of those times
[/INDENT][/INDENT]

---

### Post by garyed on 2017-04-29
> **Bashing-om said:**
> garyed; Humm.



```

sysop@x1604:~$ sudo grub-probe -t device /boot/grub
/dev/sda1
sysop@x1604:~$ 

```
where the sda1 partition -in my case - holds /boot ->
```

ls -al /boot/

```
contains /grub
```

ls -al /boot/grub/

```
contains grub's 2nd stage files.

So, I guess I need to ask you to clarify my miss-understanding of what you seek .

[INDENT][INDENT]one of those times
[/INDENT][/INDENT]
I'm trying to find out what partition holds the grub files that are actually used at bootup when you have multiple grub installs since each install can change the actual partition that's used.
If you look at the commands I ran from booting two different Ubuntu versions on the same machine you'll see that /dev/sda4 changes to /dev/sda7 depending the version being used. 
> /////////////////////////////////////////////////
/////////////////////////////////////////////////
Booting From Ubuntu Studio Install:
/////////////////////////////////////////////////
////////////////////////////////////////////////


gary@gary-gig:~$ sudo debconf-show grub-pc
  grub-pc/install_devices_failed: false
  grub2/device_map_regenerated:
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/install_devices:
  grub2/kfreebsd_cmdline:
  grub2/kfreebsd_cmdline_default: quiet splash
  grub-pc/disk_description:
  grub2/linux_cmdline_default: quiet splash
  grub2/linux_cmdline:
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/partition_description:
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/timeout: 10
  grub-pc/hidden_timeout: true
  grub-pc/install_devices_disks_changed:
  grub-pc/install_devices_empty: false
  grub-pc/kopt_extracted: false
  grub-pc/chainload_from_menu.lst: true
gary@gary-gig:~$ sudo lshw -C Disk -short
H/W path         Device      Class          Description
=======================================================
/0/1/0.0.0       /dev/sda    disk           1TB ST1000DM003-1ER1
/0/2/0.0.0       /dev/sdb    disk           1TB ST1000DM003-1ER1
/0/3/0.0.0       /dev/sdc    disk           1TB ST1000DM003-1ER1
/0/4/0.0.0       /dev/cdrom  disk           iHAS124   E
gary@gary-gig:~$ sudo grub-probe -t fs_uuid /boot/grub
d0adf9b8-7949-4171-ac5a-eba15b50c06c
gary@gary-gig:~$ sudo grub-probe -t device /boot/grub
/dev/sda4

-------------------------------------------------------------------------------
////////////////////////////////////////////////////////
////////////////////////////////////////////////////////

Booting From Ubuntu 16.04 install:
//////////////////////////////////////////////////
//////////////////////////////////////////////////

gary@gary-U16:~$ sudo debconf-show grub-pc #
  grub-pc/disk_description:
  grub2/linux_cmdline:
  grub2/kfreebsd_cmdline_default: quiet splash
  grub2/device_map_regenerated:
  grub-pc/hidden_timeout: true
  grub-pc/timeout: 10
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/partition_description:
  grub-pc/chainload_from_menu.lst: true
  grub2/kfreebsd_cmdline:
  grub-pc/install_devices_failed_upgrade: true
  grub2/force_efi_extra_removable: false
  grub-pc/install_devices_empty: false
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
  grub-pc/install_devices:
  grub2/linux_cmdline_default: quiet splash
  grub-pc/kopt_extracted: false
gary@gary-U16:~$ sudo lshw -C Disk -short
H/W path         Device      Class          Description
=======================================================
/0/1/0.0.0       /dev/sda    disk           1TB ST1000DM003-1ER1
/0/2/0.0.0       /dev/sdb    disk           1TB ST1000DM003-1ER1
/0/3/0.0.0       /dev/sdc    disk           1TB ST1000DM003-1ER1
/0/4/0.0.0       /dev/cdrom  disk           iHAS124   E
gary@gary-U16:~$ sudo grub-probe -t fs_uuid /boot/grub
f4573cde-18ed-4af3-9834-6743cb02f272
gary@gary-U16:~$ sudo grub-probe -t device /boot/grub
/dev/sda7
gary@gary-U16:~$ 



---

### Post by oldfred on 2017-04-29
Your ESP may be mounted with umask=0077in fstab. That prevents you from seeing anything.
Boot-Repair automatically reset that to defaults which 14.04 & before used. They may have changed it for security reasons, but many changes/fixes require access.

This says I am booting the second partition on first drive. UUID also matches. Path is if it is mounted. If from live installer you have to mount the ESP.
```

fred@Z170N:~$ cat /boot/efi/EFI/ubuntu/grub.cfg 
search.fs_uuid 5c1e1a3f-261f-4da5-a0c2-8f479b3039de root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

---

### Post by garyed on 2017-04-29
> **oldfred said:**
> Your ESP may be mounted with umask=0077in fstab. That prevents you from seeing anything.
Boot-Repair automatically reset that to defaults which 14.04 & before used. They may have changed it for security reasons, but many changes/fixes require access.

This says I am booting the second partition on first drive. UUID also matches. Path is if it is mounted. If from live installer you have to mount the ESP.
```

fred@Z170N:~$ cat /boot/efi/EFI/ubuntu/grub.cfg 
search.fs_uuid 5c1e1a3f-261f-4da5-a0c2-8f479b3039de root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

You're correct about the mounting in fstab being 0077 
I don't think I want to change that just for security or accidental screw up reasons but I assume I could just issue a manual mount command with the correct permissions to just test it.

---

### Post by oldfred on 2017-04-30
Even when I change fstab & remount, it does not work in Nautilus. I have to reboot. Have not tried manual mount.
Do not think you can mount it twice.

Not sure how Boot-Repair does it but it comments out standard 0077 and adds new defaults. Do not know if then it works in Boot-Repair or not as that would be a manual mount.

---

### Post by garyed on 2017-04-30
> **oldfred said:**
> Even when I change fstab & remount, it does not work in Nautilus. I have to reboot. Have not tried manual mount.
Do not think you can mount it twice.

Not sure how Boot-Repair does it but it comments out standard 0077 and adds new defaults. Do not know if then it works in Boot-Repair or not as that would be a manual mount.

I actually found the grub.cfg file you were talking about & you were right it tells you exactly where the grub boot partition files are:
> 
$ sudo cat /boot/efi/EFI/ubuntu/grub.cfg
search.fs_uuid f4573cde-18ed-4af3-9834-6743cb02f272 root hd0,gpt7 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
  

Even being mounted with 0077 in fstab you can still access it being root.
I was looking at the wrong EFI partition (Reserve partition) & that's why I couldn't find the files.

---

### Post by oldfred on 2017-04-30
Glad that worked.

I back up my ESP as I have multiple Ubuntu installs and each new install over writes the /EFI/ubuntu and I want to keep main working install as the  one that boots by default. I have learned it is easier to restore from backup while still in installer as then you have full access.

---

### Post by garyed on 2017-04-30
> **oldfred said:**
> Glad that worked.

I back up my ESP as I have multiple Ubuntu installs and each new install over writes the /EFI/ubuntu and I want to keep main working install as the  one that boots by default. I have learned it is easier to restore from backup while still in installer as then you have full access.

That sounds like a good idea. Would you mind posting how you actually backup & restore those files on the EFI boot partition.

---

### Post by oldfred on 2017-04-30
I cheat and use gksudo with Naulitus. They do not install gksudo anymore as not recommended.
Live installer often works better.

But have converted to just using sudo rsync or sudo cp with parameters which may not matter with FAT32 as it does not support Linux style parameters.

I do not have history of original copy.

I did install Mate. And it overwrote my main /EFI/ubuntu. So I copied to another folder in /EFI. I already had a copy of working version in /EFI/xenial.
From working system so mounted at /boot/efi.
mkdir /boot/efi/EFI/mate
sudo cp -a /boot/efi/EFI/ubuntu/* /boot/efi/EFI/mate
sudo cp -a /boot/efi/EFI/xenial/grub.cfg /boot/efi/EFI/ubuntu

I think those were the commands that  worked. I am no expert on cp & rsync and often have to experiment to get what I want copied.
I also have copies on other drives and on flash drives as backups.

---

### Post by garyed on 2017-04-30
As long as it works that's what counts.  I haven't had to repair grub in a while so I'm pretty rusty & if i could just copy the boot files that would make things easy if the need arose.

---

