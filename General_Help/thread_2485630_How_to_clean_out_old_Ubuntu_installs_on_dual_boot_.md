---
title: "How to clean out old Ubuntu installs on dual boot machine"
date: 2023-04-04
forum: General Help
---

### Post by michael351 on 2023-04-04
I have an 'old' dual boot Windows/Ubuntu home theater PC. Over the years and many updates and upgrades the system disk is a mess.
I would like to clear out the old leaving only windows and a partition for ubuntu 22.04. The image linked below (using Gparted) shows my disk.
I see sda4 is the partition I would like to wipe and use, but I can't seem to do it using Ubuntu install (live-USB) without wiping the entire drive.
Any suggestions


[LIST]
[*][https://www.dropbox.com/s/xlltonpux59e4tx/Aspire_disk_layout.JPG?dl=0](https://www.dropbox.com/s/xlltonpux59e4tx/Aspire_disk_layout.JPG?dl=0)
[/LIST]

---

### Post by tea for one on 2023-04-04
Which version of Windows do you have?
Both Windows 10 and 11 need an EFI System Partition, which is not visible in your screen shot.

---

### Post by Frogs Hair on 2023-04-04
An image from the Windows disk management would be helpful as well. From my dual booting experience, when installing or reinstalling a dual boot on the same drive with Windows it's best to make changes to the disk from Windows. What I did in this case was to backup any files from Ubuntu a removable drive or cloud storage, change the old partitions to un-allocated space and install Ubuntu on that space. As stated the Windows version is important to know first.

 My experience _was_ with Win 10 and Ubuntu using[ EasyBCD]("https://neosmart.net/EasyBCD/") in legacy mode, this allowed me to remove and install new versions of Ubuntu with no boot issues at all. I now run Win 11 and Linux on different drives which is a much different procedure.

---

### Post by oldfred on 2023-04-04
Often with live installer, you have to unmount the swap partition in the extended partition when using the old MBR (msdos) partitioning. 
Having swap mounted in effect mounts entire extended partition, so you cannot modify anything in the extended partition.

From your install run this to see the partitions you are using. 
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

Be sure to have good backups, just in case wrong partition is deleted or partition still has some data you want.
Also make sure your main working install is default boot, otherwise deleting partition used for booting will break boot.

---

### Post by michael351 on 2023-04-05
It's windows 10.
Looking at the gparted screen shot I linked above, the linux-swap is on sda7. boot is on sda9

My fear is screwing up the boot loader so when its time to install Ubuntu. I have to find the EFI system partition as per 'tea for one'.
Everything is backed up, so this is becoming more of an education exercise.

---

### Post by tea for one on 2023-04-05
> **michael351 said:**
> Everything is backed up, so this is becoming more of an education exercise.
Good news to read that you have back-ups.

Now, it looks like Windows 10 is installed in old-fashioned legacy mode because there is no ESP.
Also, you have extended partitions, which indicate msdos partition table rather than gpt.
I imagine that this PC was originally Windows 7?

A more fruitful "education exercise" would be:-
Download Windows 11 iso (assuming the PC is compatible)
Install with Windows 11 defaults (this will use UEFI mode with GPT and remove all existing partitions)
Restore data backup
Create space for Ubuntu using Windows tools
Install your preferred flavour of Ubuntu

If your oldish PC is not compatible with Windows 11, there are published workarounds.
Alternatively, just install a flavour of Ubuntu.

---

### Post by michael351 on 2023-04-05
I don't see "EFI" ?

 ```
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

  NAME    FSTYPE   SIZE FSUSED LABEL           PARTLABEL MOUNTPOINT UUID                                             PARTUUID
  sda            232.9G
  [FONT=&amp]&#9500;[/FONT][FONT=Calibri]&#9472;[/FONT]sda1  ntfs      17G        PQSERVICE                                       6CDA8279DA823F78                            72d8e29b-01
  [FONT=&amp]&#9500;[/FONT][FONT=Calibri]&#9472;[/FONT]sda2  ntfs     100M        SYSTEM RESERVED                      F4848360848323E8                                  72d8e29b-02
  [FONT=&amp]&#9500;[/FONT][FONT=Calibri]&#9472;[/FONT]sda3  ntfs    79.4G        Acer                                                   DE0284BF02849E61                          72d8e29b-03
  [FONT=&amp]&#9500;[/FONT][FONT=Calibri]&#9472;[/FONT]sda4             1K                                                                                                                             72d8e29b-04
  [FONT=&amp]&#9500;[/FONT][FONT=Calibri]&#9472;[/FONT]sda5  ntfs    27.3G        z_theater                                         01CCBF5767863390                              72d8e29b-05
  [FONT=&amp]&#9500;[/FONT][FONT=Calibri]&#9472;[/FONT]sda6  ext4    49.4G                                                             d40b84a2-7c54-4a20-8e33-ed2c2d516ec6 72d8e29b-06
  [FONT=&amp]&#9500;[/FONT][FONT=Calibri]&#9472;[/FONT]sda7  swap     2.2G                                  [SWAP]                 b93d264a-92c0-4646-90c9-052cc0f12021 72d8e29b-07
  [FONT=&amp]&#9500;[/FONT][FONT=Calibri]&#9472;[/FONT]sda8  ext4    35.5G  29.6G                           /                        24af3e43-a0b1-4376-87b7-7c0cfad2d050 72d8e29b-08
  [FONT=&amp]&#9500;[/FONT][FONT=Calibri]&#9472;[/FONT]sda9  vfat     512M                                                                  C978-C86A                                    72d8e29b-09
  &#9492;&#9472;sda10 ext4    21.5G                                                                 cff95a97-bd30-49b7-9f8d-ffdc315ed151 72d8e29b-0a

```

---

### Post by yancek on 2023-04-05
In the output in your last post, sda9 appears to be an EFI partition.  The GParted image in your first post shows it as an EFI partition (boot, esp).
sda4 is the Extended partition and contains all the logcial partitions with higher numbers.  sda8 is your Linux/Ubuntu system partition as seen by the mount point /.  You can't delete that without first unmounting and deleting all the logcial partitions (sda5-sda10) and I don't believe that is what you want.

If you boot Ubuntu, can you try to mount sda9 to see what is in it?  Is there an ubuntu directory?  Since you have an Extended partition, you have installed in Legacy mode and probably do not have a GPT drive.  Do you boot Ubuntu and windows from Grub?  If so, you would have Ubuntu also installed Legacy as an EFI Grub won't boot a Legacy windows.

Since you have backups, you can do as suggested above by tea for one or boot and install Ubuntu to sda8, booting with Legacy mode turned on in the BIOS and selecting the Legacy USB boot option in the BIOS.  Asked above but not answered, is this windows install an upgrade from windows 7??

---

### Post by oldfred on 2023-04-05
If computer is so old as to be Windows 7, it may be better to use a light weight flavor of Ubuntu.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

One disadvantage of BIOS/MBR is you only have one MBR for boot loader.
Windows 8 or later uses fast start up or if it needs any fixes and then grub often will not boot Windows. And you then have to temporarily install a Windows boot loader to MBR, repair Windows and restore grub.
Or you need Windows repair/recovery flash drive & Ubuntu live installer available all the time to make repairs.

Note Windows 7 is EoL and not supported anymore. Should not be used to connect to Internet if you are using it.

If system is UEFI based, and supports UEFI installs, then Acer requires some extra settings particularly "trust" setting in UEFI for Ubuntu entry.

---

### Post by michael351 on 2023-04-05
Yes! You are correct, this PC started out as Windows 7! I added Ubuntu to it and then upgraded windows to windows 10.
But each time, the old OS's remained. One of the partitions is still windows 7.
PC is not compatible with windows 11. If I install Ubuntu, it just adds it instead of replace the older one. That's why I am running out of room.

---

### Post by michael351 on 2023-04-05
It's a windows 10 machine. It just has windows 7 in one of the partitions I would like to eliminate and reclaim

---

### Post by michael351 on 2023-04-05
> **yancek said:**
> In the output in your last post, sda9 appears to be an EFI partition.  The GParted image in your first post shows it as an EFI partition (boot, esp).
sda4 is the Extended partition and contains all the logcial partitions with higher numbers.  sda8 is your Linux/Ubuntu system partition as seen by the mount point /.  You can't delete that without first unmounting and deleting all the logcial partitions (sda5-sda10) and I don't believe that is what you want.

If you boot Ubuntu, can you try to mount sda9 to see what is in it?  Is there an ubuntu directory?  Since you have an Extended partition, you have installed in Legacy mode and probably do not have a GPT drive.  Do you boot Ubuntu and windows from Grub?  If so, you would have Ubuntu also installed Legacy as an EFI Grub won't boot a Legacy windows.

Since you have backups, you can do as suggested above by tea for one or boot and install Ubuntu to sda8, booting with Legacy mode turned on in the BIOS and selecting the Legacy USB boot option in the BIOS.  Asked above but not answered, is this windows install an upgrade from windows 7??

The windows install was upgraded from windows 7 to windows 10.

---

### Post by michael351 on 2023-04-05
Can I just boot into windows and using its disk tools remove sda4? Then boot using Ubuntu live-USB and install Ubuntu along side Windows?

---

### Post by tea for one on 2023-04-05
Before we suggest an adventurous "education exercise", can you confirm that this is not your main PC?

---

### Post by Tadaen_Sylvermane on 2023-04-05
While probably not a popular viewpoint I'd highly suggest you start from scratch. Back everything up and reinstall Windows. Then create a single partition with lvm for your linux stuff. Then you can delete / add partitions at will without messing about with partitioning directly. That is a partition mess you have there.

---

### Post by michael351 on 2023-04-05
> **tea for one said:**
> Before we suggest an adventurous "education exercise", can you confirm that this is not your main PC?

No, not at all. this is used as a home theater PC with Kodi. I also use Plex, Emby, and a few others. Essentially I use it as a Roku device except I can use other tools on a big screen from time to time.
The only issue, is I do not have Windows install disks/license code. The PC came to me with windows installed. If I wipe the drive and start over, I don't have a way to restore windows except to use my backups to put it back the way it was.

---

### Post by michael351 on 2023-04-05
I don't have windows license to start from scratch. The PC came with windows 7 on it and then I just upgraded to 10 some time ago.

---

### Post by Tadaen_Sylvermane on 2023-04-05
Theoretically it should auto activate when you sign into your MS account. Again in theory. Feature of Windows 10+.

---

### Post by tea for one on 2023-04-06
The Legacy Windows 10 to be retained is installed on sda3 (together with ntfs partitions on sda1 and sda2).
If that is correct, can you boot into Windows 10 via the Windows bootloader (i.e. not Grub)?

---

### Post by yancek on 2023-04-06
>   					Can I just boot into windows and using its disk tools remove sda4? 

No, you can't.  That is explained in post 8, the first paragraph.

You indicate that you still have windows 7 along with windows 10.  If you updated 7 to 10 I would have expected it to use the same partitions.  If you have 7 on one partition, which one is it?

The GParted output in your first post shows that you are booted to the system on partition sda8.  What is on sda6 and sda10, the other Linux partitions?  Are those data partitions or are those the previous installs of Ubuntu?

---

### Post by michael351 on 2023-04-06
> **yancek said:**
> No, you can't.  That is explained in post 8, the first paragraph.

You indicate that you still have windows 7 along with windows 10.  If you updated 7 to 10 I would have expected it to use the same partitions.  If you have 7 on one partition, which one is it?

The GParted output in your first post shows that you are booted to the system on partition sda8.  What is on sda6 and sda10, the other Linux partitions?  Are those data partitions or are those the previous installs of Ubuntu?

One is a data partition (sda6; empty) and the other is a previous Ubuntu install (Ubuntu 14). 
Again - how this happens, I don't know, just that when I install from a live-USB, it doesn't write over the old install and puts it in a new partition, hence my original question.\

---

### Post by oldfred on 2023-04-06
Then you can use gparted to delete those partitions.
Do not use Windows. It is known in BIOS/MBR mode to not include ext4 logical partitions when updating partition table. Data is still there, just partition table is not correct.

If using same partition, you should use Something Else install option and choose/change that partition as / . Same if /home if separate.
Other options either shrink an existing partition, use unallocated space, or even totally erase drive.

---

### Post by michael351 on 2023-04-06
> **oldfred said:**
> Then you can use gparted to delete those partitions.
Do not use Windows. It is known in BIOS/MBR mode to not include ext4 logical partitions when updating partition table. Data is still there, just partition table is not correct.

If using same partition, you should use Something Else install option and choose/change that partition as / . Same if /home if separate.
Other options either shrink an existing partition, use unallocated space, or even totally erase drive.

Making progress - some of the partitions are reported "mounted" and I can't delete them even though they are "not mounted" .....
I now have Ubuntu 22.04 working properly alongside windows 10, but ubuntu 14 and windows 7 are still there. Museum relics.

---

### Post by oldfred on 2023-04-06
Gparted typically mounts swap which mounts all of the extended partition.
So to edit any partition inside the extended, you have to unmount swap.

One advantage of gpt partitions is you can modify unmounted partitions on same drive you boot from, just not any mounted partitions if using gparted from your install.

---

### Post by michael351 on 2023-04-06
> **oldfred said:**
> Gparted typically mounts swap which mounts all of the extended partition.
So to edit any partition inside the extended, you have to unmount swap.

One advantage of gpt partitions is you can modify unmounted partitions on same drive you boot from, just not any mounted partitions if using gparted from your install.

Thank you!

---

### Post by yancek on 2023-04-07
>  Again - how this happens, I don't know, just that when I install from a  live-USB, it doesn't write over the old install and puts it in a new  partition, 

Some information on that problem is in post 22.  When installing Ubuntu on a computer which already has an install of Ubuntu or Linux, you should see a message that it has been detected and ask if you want to install over it or to a separate partition.  When you want to install over another instance, it is best to use the manual install method which is called Something Else in Ubuntu.

Usually it is easier to delete and/or modify partitions by using a 'live' USB.  With Ubuntu, you will have GParted as part of the system on the USB.  If the partitions are mounted on boot, you should unmount them before trying to modify them.  You should be able to delete or format sda6, the empty partition and the partition which has Ubuntu 14, whichever that is.  Also, where is windows 7.  I would have expected windows 10 to update/upgrade it on the same partition(s).

It may be possible to combine partitions without deleting them if they are contiguous but if there is nothing on the Extended partition you want to keep.  If you run the command:  sudo fdisk -l it will list the partitions with the sectors which is needed to see if partitions can be combined.

---

### Post by michael351 on 2023-04-07
> **yancek said:**
> Some information on that problem is in post 22.  When installing Ubuntu on a computer which already has an install of Ubuntu or Linux, you should see a message that it has been detected and ask if you want to install over it or to a separate partition.  When you want to install over another instance, it is best to use the manual install method which is called Something Else in Ubuntu.

Usually it is easier to delete and/or modify partitions by using a 'live' USB.  With Ubuntu, you will have GParted as part of the system on the USB.  If the partitions are mounted on boot, you should unmount them before trying to modify them.  You should be able to delete or format sda6, the empty partition and the partition which has Ubuntu 14, whichever that is.  Also, where is windows 7.  I would have expected windows 10 to update/upgrade it on the same partition(s).

It may be possible to combine partitions without deleting them if they are contiguous but if there is nothing on the Extended partition you want to keep.  If you run the command:  sudo fdisk -l it will list the partitions with the sectors which is needed to see if partitions can be combined.

Yes - this worked. Once I unmounted Swap (used live-USB), the rest were easy. Just simple cleanup in the end. My mistake was not using manual install to write over the previous version.

---

### Post by HermanAB on 2023-04-09
Hmm, my solution to multiboot is to install Linux and a vitualizer such as Virtualbox.  Then I can make as many other systems as desired without screwing up the host.

---

