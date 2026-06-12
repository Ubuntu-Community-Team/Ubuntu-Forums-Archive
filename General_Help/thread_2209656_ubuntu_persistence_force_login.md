---
title: "ubuntu persistence force login"
date: 2014-03-06
forum: General Help
---

### Post by jj4 on 2014-03-06
How can I force an ubuntu persistence to have a login user? I added my username and pw but it doesn;t ask for it when starting.
Also, how am I supposed to sudo if I didn't create an account when setting up the computer?

---

### Post by oldfred on 2014-03-06
The live installer with persistence is not inteneded for that. You cannot change any of the system. Persistence does  give you to chance to download some additions, but you cannot update system.

       Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by jj4 on 2014-03-07
> **oldfred said:**
> The live installer with persistence is not inteneded for that. You cannot change any of the system. Persistence does  give you to chance to download some additions, but you cannot update system.

       Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

That's what I used to have but when I used the ubuntu startup disk it just created a sort of liveCD on te USB drive.
How am I supposed to install the full version onto the USB stick?

---

### Post by oldfred on 2014-03-07
To install the full version it is just like any install to a hard drive, but you need to use Something Else or manual install as on partition screen is the option to change where grub boot loader is installed. The default install of grub is always sda, but when installing to any second drive or external drive you want to specify the MBR of that drive or sdb, sdc etc.

Is system BIOS or a new UEFI, that makes a big difference. With UEFI you can boot in either mode and it installs in the mode you booted with. With BIOS you only have the BIOS choice.

       Install to external drive. Also any second drive.
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

If you also want space to share data with Windows you have to make the very first partition NTFS as Windows only sees the first partition on flash drives. You then should manually partition in advance as the installer will not create NTFS partitions during install. You still have to use Something Else to tell install which partition is / etc.

---

### Post by C.S.Cameron on 2014-03-07
You can add yourself as a user in a persistent install using users and groups.

You can remove Try/Install by going to the root folder of your Live USB
Enter the syslinux directory
Make the syslinux.cfg file writeable

Replace the contents of the file syslinux.cfg with:

```
    default Persistent
    label Persistent
      say Booting an Ubuntu Persistent session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash noprompt --
```

Following is step by step for doing a Full install of 12.04 on a 8GB flash drive on an Intel machine. It is not much different than a regular install to internal HDD.

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system".
And "Mount point" = /windows.
Select "OK"

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4000 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hibernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.

Click "Install Now".
Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.

Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can revise grub later, if you wish.

---

### Post by jj4 on 2014-03-08
> **C.S.Cameron said:**
> You can add yourself as a user in a persistent install using users and groups.

You can remove Try/Install by going to the root folder of your Live USB
Enter the syslinux directory
Make the syslinux.cfg file writeable

Replace the contents of the file syslinux.cfg with:

```
    default Persistent
    label Persistent
      say Booting an Ubuntu Persistent session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash noprompt --
```

.

permission denied to enter root directory?

---

### Post by C.S.Cameron on 2014-03-08
I usually edit syslinux.cfg booted from another session of Ubuntu.
If you are booting from the Persistent USB you can find syslinux.cfg in filesystem/cdrom, you need to be root to edit it.

for 64bit use vmlinuz.efi not vmlinuz

Edit;
for a persistent system add persistent thus:

[CODE]    default live
    label live
      say Booting an Ubuntu Live session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --[CODE]

---

