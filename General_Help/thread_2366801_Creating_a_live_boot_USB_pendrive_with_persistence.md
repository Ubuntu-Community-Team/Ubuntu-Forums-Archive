---
title: "Creating a live boot USB pendrive with persistence for secure use of public WiFi"
date: 2017-07-21
forum: General Help
---

### Post by AbleTassie on 2017-07-21
**I want to make a USB thumb drive with live boot capability,  persistence and data storage/transfer between computers in as simple a  way as possible. Can anybody, especially the developer of mkusb, Sudodus, briefly tell me what to do in mkusb?**

**I want to do this so that I can sign onto public wifi with my  laptop in as secure a way as possible, but also use the thumb drive for  standard storage and transfer of files, perhaps to a library PC as well.**  I may also want to use a VPN, the "Firejail" sandboxing application and  a service like OpenDNS for interacting with the internet when on public  wifi.
I have two thumb drives, and 8GB and a 16 GB, but could buy larger ones, e.g., 32GB.** Is there a preferred size?**

I plan to be careful, I understand it is very important that you allow the system to reboot and  shutdown  completely, give it time to flush the buffers in other words  write the  data to the 'casper-rw' partition completely. I understand that if I unplug  the USB  pendrive too early, the system will be damaged.

 In a straight live boot without persistence,  nothing can be written to the thumb drive, so I assume there is some  increased risk of errant code, viruses, malware being written to the  thumb drive when it is set up for persistence. **Is this correct? ** 

I will only update manually a few apps,  like Firefox and Libre Office and infrequently. I can understand that it is  the kernel that is unchanged on the thumb drive, even if it is set up  for persistence. Only the data in a partition for persistence can be  changed. (And, of course, data in a partition that is set up for regular  data storage and transfer, e.g in both Linux and Windows) can be also  changed.) 

Thanks,

A.

---

### Post by wildmanne39 on 2017-07-22
I recommend that you remove all the references to this being a continuation of the other thread and from the other two as well, so a moderator does not think it is about the same topic and close your new thread like I almost did if I had not read the other thread all the way through.

Thanks

---

### Post by sudodus on 2017-07-22
> **AbleTassie said:**
> **I want to make a USB thumb drive with live boot capability,  persistence and data storage/transfer between computers in as simple a  way as possible. Can anybody, especially the developer of mkusb, Sudodus, briefly tell me what to do in mkusb?**

The specific questions concerning mkusb can be discussed in the old thread.
> 
**I want to do this so that I can sign onto public wifi with my  laptop in as secure a way as possible, but also use the thumb drive for  standard storage and transfer of files, perhaps to a library PC as well.**  I may also want to use a VPN, the "Firejail" sandboxing application and  a service like OpenDNS for interacting with the internet when on public  wifi.
I have two thumb drives, and 8GB and a 16 GB, but could buy larger ones, e.g., 32GB.** Is there a preferred size?**

Other people know better than I how to manage wifi and security. So let us hope that somebody who knows and has the time to help will see this thread :-)

-o-

Maybe there is no preferred size. It depends of how much programs you intend to install and how much data you intend to store. Look for a **fast USB 3 pendrive**. I think the size of such drives is at least 16 GB. See this link and links from it,

[help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed)

-o-

Finally, if security is very important, it might be better with an **installed system** (like installed into an internal drive, but into a USB 3 pendrive) that uses **LVM with encryption** and can be kept completely up to date with all program packages including the kernel and all tools concerning security.

Such a system can be rather portable between computers, if you avoid proprietary drivers, but it is not as portable as a [persistent] live system. See this link, [help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS) (You cannot use the compressed image file, if you want LVM with encryption. Borrow some ideas and make the installation yourself 'from scratch'. But it is more difficult to make compared to a persistent live system.

---

### Post by AbleTassie on 2017-07-22
Thanks Sudodus, 

I will look into the suggestions you have made above. 

I understand that you wrote the [mkusb quick start manual]("https://help.ubuntu.com/community/mkusb?action=AttachFile&do=view&target=mkUSB-quick-start-manual-12.pdf") for the purpose of a quick and easy creation of a live boot with persistence, particularly the pages 23-25.

And I understand that the "full description" is at the following links  [help.ubuntu.com/community/mkusb]("https://help.ubuntu.com/community/mkusb") and [help.ubuntu.com/community/mkusb/persistent]("https://help.ubuntu.com/community/mkusb/persistent")

I'll ask specific questions, if I need more help.

I will welcome comments from anybody on the security issues surrounding the use of a laptop with public WiFi, including how to be more secure using a live USB pen drive with or without persistence or a USB pen drive with a full install of Lubuntu/Ubuntu and also the possibility of using an encrypted LVM.  And I will also welcome comments from anybody on how to create such USB pen drives.

As noted above I may also want to use a VPN, the "Firejail" sandboxing application and   a service like OpenDNS for interacting with the internet when on  public  wifi and any comments on using these as it relates to a pen drive will be appreciated.

Thanks again,

A.

---

### Post by AbleTassie on 2017-07-23
> **AbleTassie said:**
> Thanks Sudodus, 


I will welcome comments from anybody on the security issues surrounding the use of a laptop with public WiFi, including how to be more secure using a live USB pen drive with or without persistence or a USB pen drive with a full install of Lubuntu/Ubuntu and also the possibility of using an encrypted LVM.  And I will also welcome comments from anybody on how to create such USB pen drives.

As noted above I may also want to use a VPN, the "Firejail" sandboxing application and   a service like OpenDNS for interacting with the internet when on  public  wifi and any comments on using these as it relates to a pen drive will be appreciated.

Thanks again,

A.

Some people on various Linux (including Ubuntu) forums have told me that a fully installed version of Linux on a pen drive that is used in a boot off a USB is more secure than a live boot with a Linux iso image that is not a full install. I understand that a fully installed version of Linux is more secure because it (including the kernel) can be updated.

 I understand, however,  that a Linux (e.g., Ubuntu) iso image is read only and that even when the iso image is on a pen drive with a partition for persistence (casper-rw)  the Linux kernel cannot be changed. 

I understand that for both cases (full install or iso image) malicious code such as malware or viruses can be written onto the pendrive if there is **(1)** a partition for persistence (casper-rw) or **(2)** a partition for storing regular data on the pen drive as though it is a regular pen drive. 

In more typical usage of a fully installed Linux (e.g., Ubuntu) OS on a hard drive, malicious code such as malware or viruses can also be written onto the hard drive as well.

So it seems to me that the main reason a fully installed bootable version of Linux (e.g., Ubuntu) on a USB is more secure that on a hard drive, _**is simply because the hard drive cannot be  compromised (i.e., written on with malicious code) during a boot off the USB**_. That is, security of the hard drive is more important (than the USB), because the hard drive is larger, has more data, is used more often, and is more securely protected because it is generally used in a private network. **Is this surmise of mine [B]in this paragraph **about keeping the hard drive secure by booting off the USB  correct?[/B]   


Thank you,

A.

---

### Post by C.S.Cameron on 2017-07-23
One good reason a Full install is more secure than a Persistent install is that you can encrypt home.
I have not found a way to make a casper-rw file or folder very secure.

---

### Post by AbleTassie on 2017-07-25
Thanks Cameron,

If you encrypt the Home Folder on a Full Install on a USB, does that mean nothing can be written to the Home folder without asking your permission?

Also, I am just trying to double-check, about protecting the hard drive by booting off a USB, because the answer seems to be an obvious "yes," but do you have any thoughts on my question above: [I]

"So it seems to me that the main reason a fully installed bootable  version of Linux (e.g., Ubuntu) on a USB is more secure that on a hard  drive, _**is simply because the hard drive cannot be  compromised (i.e., written on with malicious code) during a boot off the USB**_.  That is, security of the hard drive is more important (than the USB),  because the hard drive is larger, has more data, is used more often, and  is more securely protected because it is generally used in a private  network. **Is this surmise of mine [B]in this paragraph **about keeping the hard drive secure by booting off the USB  correct?[/B]" 
[/I]
Thanks,

A.

---

### Post by C.S.Cameron on 2017-07-25
If you encrypt the Home Folder on a Full Install on a USB, nothing can be read from or written to the Home folder without asking your permission at login, (via password).

Many people use bootable pen drives for the purpose of repairing and modifying hard drives. A pendrive controlled by SSH can modify the HDD from a distance. 

You can even put an ext partition on the HDD, label it "casper-rw" and a persistent pendrive will use it for persistence when booting from that computer.

The HDD, if used for data, can be encrypted or have encrypted partitions.

With a persistent install made using mkusb, the OS is located on a read only ISO9660 partition. Boot, Persistence and Data partitions are read/write, however the Data partition can be encrypted.

---

### Post by AbleTassie on 2017-07-26
> **C.S.Cameron said:**
> If you encrypt the Home Folder on a Full Install on a USB, nothing can be read from or written to the Home folder without asking your permission at login, (via password).

Many people use bootable pen drives for the purpose of repairing and modifying hard drives. A pendrive controlled by SSH can modify the HDD from a distance. 

You can even put an ext partition on the HDD, label it "casper-rw" and a persistent pendrive will use it for persistence when booting from that computer.

The HDD, if used for data, can be encrypted or have encrypted partitions.

With a persistent install made using mkusb, the OS is located on a read only ISO9660 partition. Boot, Persistence and Data partitions are read/write, however the Data partition can be encrypted.

Thanks Cameron,

I did some reading to support my understanding of your post and that makes sense. I don't want to modify a hard drive either locally or from a distance. I just want to be able to boot my own laptop off my own usb pen drive to allow surfing the internet as securely as possible. I just plan to check and write email, and visit sites that may be sensitive and require a username & personal password in as secure a way as possible, So I am interested in SSHs & VPNs for securely visiting sites, and I can see the security advantages of encrypting the Home folder on the USB with the  fully installed Lubuntu. And I can see that there is a security advantage to encrypting a data partition of a persistent install on a USB where the OS is located on a read only ISO9660 partition. I can also see that encrypting partitions on the laptop HDD might also add and extra layer of security too.

Any other comments, including about using a VPN, the "Firejail" sandboxing application and  using a service like  OpenDNS for interacting with the internet when on public  wifi by you or others will be appreciated.

Thanks,

A.

---

### Post by C.S.Cameron on 2017-07-26
Some ramblings on Bootable Pendrive Security:

Logging into the flash drive as guest should prevent modifications to the internal drive, however this is basically a Live boot without persistence.

Creating a new "Standard" user, should allow persistence and access to encrypted partitions, while preventing access to the internal HDD.

You can make a mkusb persistent install quite secure by encrypting the Data partition, creating a "standard" user and overwriting the Persistent partition or file after each use.

A mkusb install to SD card can be locked using the lock switch on the card, however it will only boot Live in this state, trying to boot Persistent will result in Busy Box.

A Full install should be secure if you specify full disk encryption plus home folder encryption, (overkill?), and create a "Standard" user.

Some BIOS allows disabling of hard drives.

---

### Post by AbleTassie on 2017-07-26
Thank you Cameron,

Since this is a new endeavour for me, I will study your comments closely. Any other comments, including about using a VPN, the "Firejail"  sandboxing application and  using a service like  OpenDNS for  interacting with the internet when on public  wifi by you or others will  be welcomed & appreciated.

A.

---

### Post by rschanzenbacher on 2017-07-26
I am in the same boat as you, here is what I am doing. It can be very complicated but it provides a USB drive with space for general USB use, and a full encrypted partition with a full usable Linux install. For whom it may entertain, here is how to do it.

If you are already running a linux distribution, good job! Step one is done then. If not, just use a small usb to make a Live USB to work with.

You need to install the package qemu-system-x86_64 is you are intending to use this on a 64 bit computer. If on 32 bit, qemu-system-i386. I will use qemu-system-x86_64 for the tutorial

We are setting this up on qemu instead of natively because the installer will probe your HDD in the computer you set it up in, and we don't want that.

We will now find a place to put an img file. The location has to have a space greater than the size of the USB, we will use all of it.

Now that you are where you want to put the img file. Insert your USB drive and run the command** "sudo fdisk -l" **to get a fdisk reading of your systems drive. Here is mine as an example.

```


Disk /dev/loop0: 57.9 GiB, 62109253632 bytes, 121307136 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xc2a68cf4


Device       Boot    Start       End  Sectors  Size Id Type
/dev/loop0p1          2048  59746188 59744141 28.5G  7 HPFS/NTFS/exFAT
/dev/loop0p2 *    59746304  60794879  1048576  512M 83 Linux
/dev/loop0p3      60794880 121307136 60512257 28.9G 83 Linux




Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: B7FF52B4-74EA-4496-8B9A-C7EDEABF6FA6


Device         Start       End   Sectors   Size Type
/dev/sda1       2048    534527    532480   260M EFI System
/dev/sda2     534528    567295     32768    16M Microsoft reserved
/dev/sda3     567296 328249343 327682048 156.3G Microsoft basic data
/dev/sda4  389689344 390711295   1021952   499M Windows recovery environment
/dev/sda5  390711296 652576767 261865472 124.9G Microsoft basic data
/dev/sda6  686940160 974819327 287879168 137.3G Linux filesystem
/dev/sda7  328249344 389688797  61439454  29.3G Linux filesystem
/dev/sda8  974819328 976773119   1953792   954M Linux swap
/dev/sda9  652576768 686940159  34363392  16.4G Linux filesystem


Partition table entries are not in disk order.








Disk /dev/sdb: 57.9 GiB, 62109253632 bytes, 121307136 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xf6004ba7


Device     Boot    Start       End  Sectors  Size Id Type
/dev/sdb1  *        2048  60656344 60654297 57.8G  7 HPFS/NTFS/exFAT


```

Now we will look for your usb drive, we can easily find it by finding the entry with the corresponding size of your USB drive

```




Disk /dev/sdb: 57.9 GiB, 62109253632 bytes, 121307136 sectors


```

My USB is a 64GB USB**3.0 **Thumb drive. You want USB 3.0 for performance to be remotely acceptable.

Now pay attention to the number right before bytes on the line above. My usb stick is 62109253632 bytes. Yours may be different. You want to use your number.

We will now run the dd command to make the "HDD" for qemu which we will put on the USB when we are done.

Now run:

```

sudo dd if=/dev/zero of=usbdrive.img count=(Your byte count here) seek=1 bs=1

```

You should now have a file the size of your USB drive.

Now download a live cd image of the distro you would like to use.

I will use ubuntu-gnome-17.04-i386.iso in this example.

Once downloaded, put the iso in the same folder as your img file you created with the dd command.

After you do that, run this command:


If you are using x86_64 qemu:

```

qemu-system-x86_64 --enable-kvm -m 1024 -hda usbdrive.img -cdrom (Name of iso you downloaded) -localtime

```

This will start a VM, once it starts select "Try out *Ubuntu*"

Now we can go one of two ways, I will describe the easier way here, which will make a Swapfile in the root partition. Please reply to this if you want a seperate Swap partition.

Start the installer. Go through the prompts until it asks where to install the OS. Choose "Let me partition myself"

Once you do that, click "Create Partition Table" Next, Create a new partition, set the size whatever you want to be accessible from any computer as a general usb drive. I reccommend leaving 10GB for the system though. The size has to be expressed in MB so 1GB = 1000MB. I usually go with half the drive allocated to USB storage.

Set use this partition as "NTFS journaling filesystem"

Set mountpoint as /windows

Click OK

Make another new partition with these specifications. This will be your boot drive. Size=512MB  Use as "ext2 filesystem" Mount point as /boot

Click OK

Finally make a final partition with the remaining space and set it's use as "Physical partition/drive for encryption" Then enter a password to enter at boot. This will encrypt the system that runs in the USB.

Once it's created, a new entry will appear above "/dev/sda" I am writing this by memory so I am unsure what it will be called.

Whatever it is, it should be set as ext4, this is good but click the entry and click "Edit Partition" and set the mount point as "/"

Click "OK" 

Now make sure the boot drive installation location is set to "/dev/sda"

Go through the rest of the installation process. When it is done, shutdown the VM.

Now on your host machine again, we need to remember the drive mapping for the USB drive. If you forget, run 

```

sudo fdisk -l

```

again, and find the drive with the same size as your USB. Mine was "/dev/sdb" so I will use that as the example. To put the img file we just setup on the USB, run:

```


sudo dd if=usbdrive.img of=/dev/sdb bs=8M status=progress


```

Where /dev/sdb is whatever your USB is. Let this process finish. Mine took 1 hour. You know its done when you see the command entry prompt again. If you get a Disk full error at the end, just ignore it it means your maybe one or two bytes off, as long as it works don't worry about it.

Almost done :D

Reboot your computer and select the USB as the boot device and boot it up. It should ask for the password you set at the prompt to setup the partition for physical encryption. Enter it and you system will continue booting. When you get to the login screen, login and the when you get to the Desktop. Open a terminal by searching for it in the menu or if you are running ubuntu, press CTRL+ALT+T. In the terminal, type these commands:

```


cd /
cd etc
sudo nano fstab


```

Now you are in a text editor editing a file. Find where the entry that has "/windows" is. Change "/windows" to "/media/(the username you set)/USBDRIVE" This will allow you to access the USB Data partition in the actual system. If there is any entry with "fd0" delete those lines unless you have a floppy drive. Once done, press CTRL+X. It will ask if you want to save the buffer, tap on 'y' on your keyboard and it will ask for a name of the file. DO NOT CHANGE THIS. IT WILL ALREADY HAVE "fstab" or "/etc/fstab" JUST PRESS ENTER. AGAIN, 'y' then ENTER.

Now reboot the system, when done you have a fully encrypted Linux install on a USB you can install any package on. If you insert it into a windows pc, it will show up as a regular USB drive and when you boot into the Linux install in it and go into the file manager, the USB partiton should be accessible there as well.

Man, that was a lot of typing, hopefully this will help. If you have any questions or get stuck, just ask. I will keep an eye on this post. Good Luck!

Disclaimer: I am a 15 year old Ubuntu user. I have no idea how secure this actually is. If someone knows security, please feel free to criticize/suggest things for me to do better to make the USB more secure. 

-Ryan

---

### Post by sudodus on 2017-07-27
I have looked into persistent live drives with encrypted home, and I have found a method to create a system that I think works well for your purposes.

Have a look at this link, [Persistent live drive with a standard user and a user with administration permissions](https://ubuntuforums.org/showthread.php?t=1958073&page=36&p=13670206#post13670206)

You may want to try how such a system will work for you.

Advantage:

- more portable (than an installed system).

Disadvantages:

- less stable (than an installed system).

- less secure (encrypted home is less secure than encrypted disk, which is possible with an installed system). But it might be secure enough, particularly if you turn off swapping, if there is a linux swap partition in an internal drive in the computer, where you are running the system.

---

### Post by AbleTassie on 2017-07-27
Thank you Ryan and Sudodus for your recent posts,

I will study your posts carefully.

A.

---

### Post by AbleTassie on 2017-07-28
> **C.S.Cameron said:**
> Some ramblings on Bootable Pendrive Security:
..........

A Full install should be secure if you specify full disk encryption plus home folder encryption, (overkill?), and create a "Standard" user.


Cameron,

When you say specify "full disk encryption," above, do you mean encryption of the HDD of the laptop that is using the bootable USB pen drive OS to surf the internet over public wireless?

 **If "yes," what is the simplest way to do this?** 

**As an aside,** I have been experimenting and have made a full install of Lubuntu 16.04.2 LTS on an old pen drive starting with a second live pen drive of Lubuntu 16.04.2 LTS. While I was making this full install I think was given the option to encrypt the Home Folder, but I don't think there was an option to encrypt the pen drive (or, say, most of the partitions thereon). 

Or do you mean encrypt the full pen drive itself? , assuming there some way to encrypt the USB pen drive itself?

BTW, I also added, after I created the full install of Lubuntu on the  pen drive, I then created, formatted and labelled a Data file on the USB  using Gparted and the Disks utility. This, of course, allows me to use the pen  drive like a regular pen drive that is not used as an OS.

Thanks,

A.

---

### Post by sudodus on 2017-07-28
See this link with instructions how to create LVM with encryption alias encrypted disk with Lubuntu,

[Alternate Install (Unencrypted home) in Lubuntu Alternate i386 in Xenial Daily](http://iso.qa.ubuntu.com/qatracker/milestones/363/builds/126343/testcases/1660/results)

'Unencrypted home' actually means 'LVM with encryption'. You can select to encrypt the home partition in addition to this (by responding differently when asked in one of the dialogue screens).

-o-

There are problems due to zram to do the corresponding things with the Lubuntu desktop iso files, but if you turn off zram, it will work too.

---

### Post by C.S.Cameron on 2017-07-28
I just noticed that Firewalls still have not yet been mentioned in this thread: [https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall) I have no experience with them myself.
Same goes for VPN's and Tor [https://www.torproject.org/](https://www.torproject.org/) [https://motherboard.vice.com/en_us/article/kb7kza/the-fbi-used-a-non-public-vulnerability-to-hack-suspects-on-tor](https://motherboard.vice.com/en_us/article/kb7kza/the-fbi-used-a-non-public-vulnerability-to-hack-suspects-on-tor).

---

### Post by AbleTassie on 2017-07-28
> **sudodus said:**
> See this link with instructions how to create LVM with encryption alias encrypted disk with Lubuntu,

[Alternate Install (Unencrypted home) in Lubuntu Alternate i386 in Xenial Daily]("http://iso.qa.ubuntu.com/qatracker/milestones/363/builds/126343/testcases/1660/results")

'Unencrypted home' actually means 'LVM with encryption'. You can select to encrypt the home partition in addition to this (by responding differently when asked in one of the dialogue screens).

-o-

There are problems due to zram to do the corresponding things with the Lubuntu desktop iso files, but if you turn off zram, it will work too.

Thanks Sudodus & Cameron,

Sudodus,

I installed my present Lubuntu on my HDD months ago. If I was going to do a new installation, I would probably encrypt the entire HDD, but it looks like it is risky and a lot of work with a lot of opportunity for error after installation. Also I'm not sure my machine really has the firepower for it; it was built in 2008. 

On the other hand, encryption of the Home folder after installation looks doable. I will have physical control of the laptop, since I will be booting it off a pen drive with Lubuntu thereon and using public wireless to access the internet. So I just want to try to limit accessing the HDD either by accident or by some malicious script or code or something. So at this point, it looks like encryption of the Home folder is a good option for me. 

I have made both a Lubuntu Live USB pen drive (without persistence) and a full install of Lubuntu on a USB as well. I may try to make a Lubuntu Live USB pen drive with persistence eventually. At this point I am inclined to just use a full install of Lubuntu on a pen drive that also includes a partition for storing data formatted to a file system that will work on my lap top, but also a Windows machine as well. Which file system should I use? I tried this with FAT32 & it did not seem to work with a Windows XP PC I have. Would FAT32 be too old for a local library's Windows PCs--maybe.   Maybe I should use NTFS? 

Cameron,

The firewall is a good reminder: I just enabled the UFW on my full install Lubuntu on the pen drive. I don't know much about VPNs either, but will learn.

A.

---

### Post by sudodus on 2017-07-29
> Which file system should I use?

I suggest NTFS if you want access from Windows and linux, and FAT32 if you want access from MacOS too. It is important that it is partition #1 for Windows to see it, when on a USB drive.

Such an NTFS partition is created automatically, if you make a persistent live drive with mkusb. You can do it yourself with **gparted**, before you create a system with an installed Lubuntu system.

---

### Post by C.S.Cameron on 2017-07-29
Following is step by step for installing 16.04 on a 16GB flash drive on an Intel machine. Start with NTFS format if you want a NTFS Windows partition, The Windows partition must be the first partition.

Turn off and unplug the computer. (See note at bottom)
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install third-party software.
Continue.

At "Installation type" select "Something else".
Continue

Confirm Device is correct.
Select "New Partition Table".
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "+".
Make "Size:" about 1000 MB.
Select "Primary".
Location for the new partition = "Beginning of this space".
"Use as:" = "FAT32 file system". (or leave as NTFS).
And Mount point = "/windows".
Select "OK"

Click "free space" and then "+".
Select "Size:" = 5000 to 7000 megabytes, "Primary", "Beginning of this space", Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "+".
Select "Size:" = 1000 to 4000 MB, "Primary", Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hibernation)
Click "free space" and then "+".
Select "Size:" = remaining space, (1000 to 2000 megabytes, or same size as RAM), "Primary", "Beginning of this space" and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".

Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, computer name, username, password and select if you want to log in automatically or require a password.
Requiring a password to log in and selecting "Encrypt my home folder" are good options if you are worried about loosing your USB drive.
Select Continue.

Wait until install is complete.
Turn off computer and plug in the HDD.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can revise grub later, if you wish.

---

### Post by AbleTassie on 2017-07-29
Thanks Sudodus and Cameron,

**Is there any way to create the additional data partition on the pen drive that can be accessed by Windows AFTER creation of a fully installed Ubuntu the drive using GParted?** I did this very thing, and my data partition was mountable and worked fine in Lubuntu, but apparently could not be mounted by Windows XP. I thought perhaps if I modified the procedure I used to make the data partition with GParted, that I might get it to work with Windows too. Is it essential that the data partition be created first, before the creation of the full install of Ubuntu? 

I actually have already created a full install of Lubuntu on a Pen drive by following the instructions at the link below, which has a YouTube video. Start at about 3:35, which is after the Ubuntu iso file has been downloaded from the internet using Windows. (The MD5SUM of the downloaded file could be done as well). 
[SIZE=1][FONT=arial][COLOR=black][h=1][SIZE=2]How to Install FULL Ubuntu on a Flash Drive:[/SIZE][/h][/COLOR][/FONT][/SIZE][SIZE=2][URL="https://www.youtube.com/watch?v=fLYBXOVn6ow"]https://www.youtube.com/watch?v=fLYBXOVn6ow
[COLOR=#000000]
Thanks,

A.[/COLOR]
[/URL][/SIZE]

---

### Post by sudodus on 2017-07-29
Yes, it is essential that the data partition be created first, before the creation of the full install of Ubuntu.

You might find a tool, that can rearrange the partition numbers, but I don't know, and **I think it will be easier with a fresh installation, where you start with the data partition**.

Maybe it will work to

1. Use **gparted** and create a partition in the beginning of the drive (at the left end as seen in gparted). You may have to reinstall grub (if the start of the boot/root partition is moved), which is a complication.

2. If there is an MSDOS partition table: Use **fixparts**, which comes with the package **gdisk**.

According to the manual ```
man fixparts
``` you can re-number the partitions to the order they reside on the drive (with the function **s**). So this way the partition in the beginning of the drive should become #1.

---

### Post by AbleTassie on 2017-07-29
Thanks Sudodus,

I will have to erase the full install of Lubuntu on my pen drive. I have done this before recently by using the "Format Disk" option in the Disks utility supplied by default in Lubuntu. There are two options: (1) don't overwrite existing data (quick) or (2) overwrite existing data with all zeroes (slow). I know that the slow/all zeroes option will decrease the life span of the drive. I have only used the drive one day or so and it is brand new. 

Do you recommend option (1) or (2)?

Is it possible to encrypt the data partition, so that the data partition cannot be accessed without the password when the fully installed Lubuntu on the pen drive has been booted into and is up & running?

Thanks,

A.

---

### Post by sudodus on 2017-07-29
0. Boot from another drive (not the one you intend to modify). Unmount all partitions (and swap off the swap partition if there is one) on the drive you intend to modify.

1. Try to create a new partition table with **gparted** (without wiping the drive at all with Disks).

Select [to look at] the correct drive, the one you intend to modify.

Use the pulldown menu in gparted:

*Device -- Create partition table...*

and then create partitions. Start with the data partition, that should be seen by Windows.

2. If this does not work, use **Disks**: '(1) don't overwrite existing data (quick)' and after that use gparted.

3. If this does not work, install and use **mkusb**: wipe the first mibibyte and after that use gparted.

-o-

Exception: If there are secret data on the drive, and you want to wipe all traces of them, you had better '(2) overwrite existing data with all zeroes (slow)' with Disks or 'overwrite the whole device' with mkusb.

-o-

***Edit:*** It is possible to encrypt the data partition. If you want access from both Lubuntu and Windows, you must use some kind of encryption, that works in both operating systems. I have no experience of that, so I will not recommend anything, you need help from other people, or maybe you can find tips directly via the internet.

---

### Post by C.S.Cameron on 2017-07-30
Following post #20 above will make a Full install flash drive with FAT32 Windows/Linux data partition, ext4 / (OS) partition ext2 home partition and swap.
Some people prefer FAT32 partitions for drives <32GB, however prior to 17.04, you need to start with a NTFS formatted drive. 
When partitioning, click change, specify new partition size, select use as - do not use the partition.
For 17.04 and later NTFS can be selected from the drop down while partitioning with "Something else".

I have not been able to open a  LUKS + Ext4 partition in Windows.
A Windows BitLocker partition in Ubuntu can be open using dislocker: [https://askubuntu.com/questions/617950/use-windows-bitlocker-encrypted-drive-on-ubuntu-14-04-lts](https://askubuntu.com/questions/617950/use-windows-bitlocker-encrypted-drive-on-ubuntu-14-04-lts)

Cross platform encryption programs include VeraCrypt and 7zip.

---

### Post by AbleTassie on 2017-08-01
Sudodus and Cameron,

Thanks to both of you for your recent detailed replies. I am experimenting with an old pen drive and I used the procedure in your post #20 Cameron, creating the data partition first (as both of you said to do), then creating the full install of Lubuntu on the pen drive. The data partition is formatted as FAT32. The full install seems to boot up and work fine and the data partition mounts and works in both Lubuntu and Windows XP. 

I am interested in encrypting partitions, and it appears that 7zip can encrypt folders, but not partitions. On the other hand, VeraCrypt appears to be able to encrypt partitions or even whole drives, but the installation of VeraCrypt seems to require familiarity with PGP signatures, not just SHA256SUMS. See [https://www.veracrypt.fr/en/Downloads.html](https://www.veracrypt.fr/en/Downloads.html) and 
[https://www.veracrypt.fr/en/Digital%20Signatures.html](https://www.veracrypt.fr/en/Digital%20Signatures.html)  . It looks like you have to download and verify various keys. 

I have little familiarity with PGP signatures. I found this write-up: [https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto) which allowed me to install gpa and I found KGpg in the Lubuntu Software center.


QUESTION(S): Is KGpg or gpa adequate to use for installation of VeraCrypt? Or do I need some other kind of software?

Thank you again,

A.

BTW, the procedure in your post #20 is similar to the one online that I have used at [https://www.youtube.com/watch?v=fLYBXOVn6ow](https://www.youtube.com/watch?v=fLYBXOVn6ow) -- they did not unplug the HDD, but warn repeatedly about not  using the hard drive as "The Device for boot loader Installation" at the bottom of the Dialogue box (at about 10:09 in the video), but rather using the drop down menu to select the pen drive you are installing Ubuntu on.

 If the boot loader is written to the HDD, is the HDD "bricked" or can it be recovered with a "Rescue" Disc or PenDrive?

---

### Post by sudodus on 2017-08-01
> If the boot loader is written to the HDD, is the HDD "bricked" or can it be recovered with a "Rescue" Disc or PenDrive? 

The HDD is ***not*** bricked by writing a bootloader to it. The booting might be changed to something you don't want (or damaged) but it can be repaired, when booted from another drive. But things are easier to manage, when you have removed the internal drive.

---

### Post by C.S.Cameron on 2017-08-01
These are the instructions I used to install VeraCrypt: [http://www.linuxandubuntu.com/home/encrypt-data-in-linux-with-veracrypt-an-alternative-to-truecrypt](http://www.linuxandubuntu.com/home/encrypt-data-in-linux-with-veracrypt-an-alternative-to-truecrypt)
Not as hard as it first seems, I think the PGP, (pretty good privacy), stuff is similar to a MD5Sum, just makes sure everything is there. I did not install gpa or KGpg.

VeraCrypt puts on a good show while running, seems to work hard encrypting stuff, even recruits the user to provide extra randomness. Takes a bit of time to encrypt files and to open them. 

I tried the full partition encryption, rather than the sandbox and it worked fine. VeraCrypt needs to be installed on both Ubuntu and Windows to share the partition, (this only matters when plugging into a public computer though).

7Zip, (P7Zip), also needs to be installed on both drives to share the encrypted folder/file. It's much faster than VeraCrypt so it is not as impressive. It only encrypts as .7Z file type, not as .zip.

I figure installing dislocker on the flash drive might be a choice for encryption, as Windows computers already come with BitLocker. Looks pretty scary to install though and I understand it is read only.

---

### Post by AbleTassie on 2017-08-01
> **sudodus said:**
> The HDD is ***not*** bricked by writing a bootloader to it. The booting might be changed to something you don't want (or damaged) but it can be repaired, when booted from another drive. But things are easier to manage, when you have removed the internal drive.

Sudodus,

Thanks I realized later after asking the question that of course the HDD is not "bricked," because the boot loader is written onto the HDD during install. So the worst that could probably happen is the need for a new install. On the other hand, maybe the pen drive just would not boot, or the boot loader on the HDD would be damaged and need to be repaired, probably an arduous process involving booting off a rescue type device.

A.

---

### Post by AbleTassie on 2017-08-01
> **C.S.Cameron said:**
> These are the instructions I used to install VeraCrypt: [http://www.linuxandubuntu.com/home/encrypt-data-in-linux-with-veracrypt-an-alternative-to-truecrypt](http://www.linuxandubuntu.com/home/encrypt-data-in-linux-with-veracrypt-an-alternative-to-truecrypt)
Not as hard as it first seems, I think the PGP, (pretty good privacy), stuff is similar to a MD5Sum, 
                                                                                                                                          ...............

I figure installing dislocker on the flash drive might be a choice for encryption, as Windows computers already come with BitLocker. Looks pretty scary to install though and I understand it is read only.

Thanks Cameron,

The VeraCryt install now looks manageable. I'll have to think some about what I will do next. 

QUESTION: If I have one or more unencrypted folders or partitions, but use VeraCrypt or 7Zip to encrypt another partition or folder and a public Windows machine does not have the Veracrypt or 7Zip installed, the public Windows machine would still be able to access the uncrypted folders/partitions, but just not be able to access the encrypted partition/folder, correct?

BitLocker is apparently only on Windows Vista or later machines, see [https://en.wikipedia.org/wiki/BitLocker](https://en.wikipedia.org/wiki/BitLocker) . I am presently using Windows XP. Not sure if I could load Windows Vista or later on the PCs I presently have. 

Assuming I could load Windows Vista on my PCs, could I encrypt a partition using BitLocker on a virtualized Windows machine or a dual booted Windows machine (sharing the HDD with Lubuntu)? 

QUESTIONS: What does Dislocker being "read only" mean? A single install, with no updating? No possibility of uninstalling after the initial install?

A.

BTW: **7-Zip** ( [https://en.wikipedia.org/wiki/7-Zip](https://en.wikipedia.org/wiki/7-Zip) ) was  apparently created in 1999, so it apparently can be installed on a  Windows XP machine, see [http://www.7-zip.org/](http://www.7-zip.org/) :
[I]"**7-Zip** works in Windows 10 / 8 / 7 / Vista / XP / 2012 / 2008 / 2003 / 2000 / NT. There is a port of the command line version to Linux/Unix."
[/I]
There is an official Microsoft  "BitLocker To Go Reader" for Windows XP, that allows BitLocker encrypted  drives to be read, but not written to (or apparently created), see 
[https://www.microsoft.com/en-us/download/details.aspx?id=24303](https://www.microsoft.com/en-us/download/details.aspx?id=24303)

---

### Post by sudodus on 2017-08-01
> I am presently using Windows XP.

You seem very concerned about security, yet you are using Windows XP, which has passed end of life. That means that Windows XP receives no security updates, and you can expect it to be a target of malware. Please consider leaving Windows XP, at least stop using it when connected to the internet.

---

### Post by AbleTassie on 2017-08-01
Thanks for the caution Sudodus. I am aware that Windows XP is no longer supported and is vulnerable. In fact, I think the world wide the Wannacry virus occurred because of outdated Windows OSs if I am not mistaken. I only connect to the internet with Windows XP if I cannot do something equivalent with Lubuntu. 

Right now, the only thing I do this for is occasionally downloading stuff from a local public library. The Overdrive library download software [https://www.overdrive.com/](https://www.overdrive.com/) does not work in Linux.

 I've tried valiantly to get Overdrive to work in my Virtualized Windows XP to no avail. I've even corresponded with tech support at Overdrive about this and I still cannot get it to work. 

The Overdrive website suggests using WINE if you are using Linux, see [https://help.overdrive.com/customer/portal/articles/1481664-is-there-a-linux-version-of-the-overdrive-app-](https://help.overdrive.com/customer/portal/articles/1481664-is-there-a-linux-version-of-the-overdrive-app-) 

There is a thread on this forum about this that is not too encouraging: [URL="https://ubuntuforums.org/showthread.php?t=2171414&highlight=overdrive"]https://ubuntuforums.org/showthread.php?t=2171414&highlight=overdrive
[/URL]
There is also something here which has a later post in 2015 that is more optimistic [https://askubuntu.com/questions/539721/how-do-i-install-the-overdrive-lending-library-program-on-wine](https://askubuntu.com/questions/539721/how-do-i-install-the-overdrive-lending-library-program-on-wine)

 I also think WINE and PlayOnLInux are vulnerable as well. I have not tried the WINE & Overdrive combination. My understanding is that just having WINE installed in Ubuntu is a security vulnerability. I suppose I could install WINE temporarily when needed to use with the Overdrive app and then uninstall WINE when done. I suppose I could also sandbox WINE in Firejail.

Do you think using WINE installed in Lubuntu would be less vulnerable than downloading audio books by using the Overdrive app in Windows XP connected to the internet? 

A.

---

### Post by sudodus on 2017-08-01
> **AbleTassie said:**
> Do you think using WINE installed in Lubuntu would be less vulnerable than downloading audio books by using the Overdrive app in Windows XP connected to the internet? 

I don't know, but I think Wine is less vulnerable than Windows XP, and if you put it in a sandbox it will certainly be better.

---

### Post by C.S.Cameron on 2017-08-01
> **AbleTassie said:**
> 
QUESTION: If I have one or more unencrypted folders or partitions, but use VeraCrypt or 7Zip to encrypt another partition or folder and a public Windows machine does not have the Veracrypt or 7Zip installed, the public Windows machine would still be able to access the uncrypted folders/partitions, but just not be able to access the encrypted partition/folder, correct?

Correct, but remember Windows can only see the first partition on a flash drive, thus if you require Windows accessible encrypted data, a 7zip encrypted archive, or VeraCrypt container, that can reside in the unencrypted partition might be the way.

> BitLocker is apparently only on Windows Vista or later machines, see [https://en.wikipedia.org/wiki/BitLocker](https://en.wikipedia.org/wiki/BitLocker) . I am presently using Windows XP. Not sure if I could load Windows Vista or later on the PCs I presently have.

Assuming I could load Windows Vista on my PCs, could I encrypt a partition using BitLocker on a virtualized Windows machine or a dual booted Windows machine (sharing the HDD with Lubuntu)? 

I think it should work, does not seem BitLocker needs a lot of horsepower, But...

> QUESTIONS: What does DisLocker being "read only" mean? A single install, with no updating? No possibility of uninstalling after the initial install?


I was able to open the BitLocked partition with DisLocker OK, but could not write to it from Ubuntu, I might be missing something.

A .7Z archive has been working read/write for me in Ubuntu and Linux. I can not get a p7zip .zip archive to actually encrypt.

Edit: Discovered I was using -r when mounting the BitLocker partition, omitting -r makes the encrypted partition read/write with DisLocker. 
I am noticing that Terminal retains the command that contains the encryption key or password, how to clear previous commands in Terminal? history -c, will clear the history of the current session.

Edit2:
I now notice that Windows 10 can see multiple FAT32/NTFS partitions on a flash drive.

---

### Post by AbleTassie on 2017-08-02
Thanks sudodus and Cameron,

I am close to marking this thread as [SOLVED]. Just a couple more questions that relate to a full install with a first Windows accessible Data Partition (FAT32):

7zip is in essentially all Windows PCs, correct?

If I am using my laptop on public wireless and booting off the USB into a pendrive Ubuntu OS, the HDD will not be accessible from the internet unless the HDD is manually mounted, correct? (I have checked and it appears the HDD is unmounted by default during such a session)

Similarly, if I am using the Windows visible first data partition on a Library PC, the other partitions (Ubuntu OS partition, etc) will not be accessible (or mountable) for the Windows PC, will they?

Thanks,

A.

---

### Post by sudodus on 2017-08-03
> **AbleTassie said:**
> 7zip is in essentially all Windows PCs, correct?

I think you have to download and install 7zip, it is not delivered with Windows. There is some compression/decompression tool, that is integrated with Windows, it is similar to 7zip, but I don't think it *is* 7zip.
> 
If I am using my laptop on public wireless and booting off the USB into a pendrive Ubuntu OS, the HDD will not be accessible from the internet unless the HDD is manually mounted, correct? (I have checked and it appears the HDD is unmounted by default during such a session)

I think this is a correct description.
> 
Similarly, if I am using the Windows visible first data partition on a Library PC, the other partitions (Ubuntu OS partition, etc) will not be accessible (or mountable) for the Windows PC, will they?

I think this is a correct description.

(But Windows may change in the future, and also today things can look differently, if the USB drive is 32 GB or bigger, or if there are data indicating that the USB drive should be looked at as a SATA drive, not a USB pendrive.)

---

### Post by AbleTassie on 2017-08-03
Thanks to everybody, especially sudodus and Cameron,

I  will mark this thread as SOLVED.

A.

---

### Post by C.S.Cameron on 2017-08-03
Install 7Zip in Windows and P7Zip in Ubuntu. This will make a compressed and encrypted .7Z file right click accessible in Windows Explorer and Ubuntu Files. 

When I plug in a flash drive with Admin privileges I get access to the HDD, when I plug in a flash drive with Standard privileges I am asked for an Admin password to access the internal hard drive. Not sure what happens if SSH is set up? or the FBI gets involved?

I have never been able to see more than the first partition of a multi partition flash drive plugged into Windows. 
Using up to date Win 10, I only see the first partition of multi partition 64GB and 128GB USB3 flash drives. Perhaps this is due to my old BIOS or hardware.
I understand that there are drivers that will let Windows see ext partitions, but have never tried one, don't think your library computer will have them installed either.

Edit:
SSH'd from a Win10 computer using Putty to a persistent flash drive booted in a laptop . Had no problem accessing the laptop HDD when logged into SSH as the main administrative user, could not get access as the secondary administrative user, nor as a standard user.
Probably best to disable SSH on a stealth flash drive.\

Edit2: My apologies to Sudodus, after my last Win10 update I now see multiple FAT32/NTFS partitions on an 8GB flash drive.

---

