---
title: "Resize Existing Partition with Unallocated Space"
date: 2019-11-14
forum: General Help
---

### Post by GirishSharma on 2019-11-14
Its a dual boot PC with Windows 10 and ubuntu 16.04. To upgrade, the Ubuntu, I started upgrade process, but I stucked due to low space on / mount point. So, I went to windows and shrunk the Windows partition (Disk Management) and a new partition of 20 GB created. Here is my fdisk output :
```

girish@girish-OptiPlex-3050:~$ sudo fdisk -l
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: E1D206C6-CD80-4796-8691-87310D959375

Device          Start        End    Sectors   Size Type
/dev/sda1        2048    1333247    1331200   650M EFI System
/dev/sda2     1333248    1595391     262144   128M Microsoft reserved
/dev/sda3     1595392 1888557055 1886961664 899.8G Microsoft basic data
/dev/sda4  1930500096 1936500735    6000640   2.9G Linux swap
/dev/sda5  1936500736 1951471615   14970880   7.1G Linux filesystem
/dev/sda6  1951471616 1953499135    2027520   990M Windows recovery environment

```

Gparted is showing me 20 GB as unallocated. Now, I want to merge this unallocated space to /dev/sda5. I followed this link : [https://askubuntu.com/questions/116351/increase-partition-size-on-which-ubuntu-is-installed](https://askubuntu.com/questions/116351/increase-partition-size-on-which-ubuntu-is-installed) because neither I have live CD nor Live USB. In that link I tried to follow the post of Sergey, but I am not understanding the meaning of this line :

use a to toggle the bootable flag on the new /dev/sda1 because there is no a option in the option list of /dev/sda command,

nor I am able to understand this text too :

"Make sure its start cylinder is exactly the same as the old /dev/sda1 used to have. For the end cylinder agree with the default choice, which is to make the partition to span the whole disk." How do I get the start cylinder number.

Kindly help me to merge the unallocated 20 GB space to / mount point.

Thank you.

---

### Post by Impavidus on 2019-11-14
That guide uses a dirty hack. I wouldn't do that on a production machine without knowing exactly what's going on. Just create a live usb. And I think that hack will only work when expanding a partition to the right, but you want to expand it to the left.

Furthermore, before you can expand the Ubuntu partition into the unallocated space, you have to deal with the swap partition, which is inbetween. So move that first, or delete it, or whatever you want. If you delete the swap partition (and create a new one, if you wish so), make sure you change your /etc/fstab to make sure the new swap partition is properly loaded and the system doesn't complain about not being able to find the old swap partition.

Or, given the very small size of your Ubuntu system, I assume you've got hardly any files there. Deleting both the swap partition and the root partition, followed by a fresh install, may be the best solution.

---

### Post by GirishSharma on 2019-11-14
> **Impavidus said:**
> That guide uses a dirty hack. I wouldn't do that on a production machine without knowing exactly what's going on. Just create a live usb. And I think that hack will only work when expanding a partition to the right, but you want to expand it to the left.

Furthermore, before you can expand the Ubuntu partition into the unallocated space, you have to deal with the swap partition, which is inbetween. So move that first, or delete it, or whatever you want. If you delete the swap partition (and create a new one, if you wish so), make sure you change your /etc/fstab to make sure the new swap partition is properly loaded and the system doesn't complain about not being able to find the old swap partition.

Or, given the very small size of your Ubuntu system, I assume you've got hardly any files there. Deleting both the swap partition and the root partition, followed by a fresh install, may be the best solution.

Thanks for your reply. Ok, as you suggested to go on live USB path, I will download ISO. For this I have [https://www.linuxliveusb.com/en/supported-linuxes](https://www.linuxliveusb.com/en/supported-linuxes) link, hovering mouse on U Tab and thinking to download ubuntu-10.04.1-desktop-i386.iso file because its seems me smallest in size 686 MB. Am I downloading the correct ISO for this purpose or you will suggest me some other Small ISO because I lives in a area which have very poor internet connectivity.

---

### Post by plucky on 2019-11-15
If you just need Gparted then you should search for "Gparted Live" and download and create a Live USB or CD. Much smaller than a Live ISO

Good Luck

---

### Post by Impavidus on 2019-11-15
If you only need gparted, you can use the gparted live disk. That should be smaller. A complete live disk that you can also use to install or fix Ubuntu is a good thing to have. I think the smallest one I could recommend is the Lubuntu 18.04 live disk, at 1GB.

Do you want a small one because your internet connection is expensive, slow or unreliable? There are ways to download the iso files such that it can resume the download after the connection failed, without restarting from the beginning.

---

### Post by GirishSharma on 2019-11-15
> **plucky said:**
> If you just need Gparted then you should search for "Gparted Live" and download and create a Live USB or CD. Much smaller than a Live ISO

Good Luck
Is it possible to merge/resize unallocated space to the Ubuntu partition without Gparted i.e. by commands on terminal please even I have downloaded Gparted Live USB, booted it from that USB but I am not able to use the Gparted i.e. which step I should take first and second. Examples on internet shows with extended entries but in mine case there is no extended partition. So, I am very much confused how do achieve the goal on terminal. I learned that it is not possible while partition is mounted, but if it is available with Gparted's terminal windows or any other way.

---

### Post by Impavidus on 2019-11-15
OK, so you've got the gparted live usb running. And you're correct that you don't have an extended partition. They are old-fashioned.

Gparted is easy to use, but you have the slight complication that your swap partition is inbetween the unallocated space and the partition that you want to expand.

First make sure the swap partition is off. That is sda4. If not, right-click on the swap partition, set swap off. Now you can move the swap partition to the left. Move it all the way until it sits against the Windows partition (sda3). Don't change its size. It's just right the way it is.

Now the unallocated space is inbetween sda4 and sda5. You can switch swap on, as that may speed things up a bit. Then make sure sda5, the Ubuntu root partition, is unmounted. If not, right click and unmount. Then you can change sda5. I don't know if you can directly expand it to the left, or maybe you have to move it to the left first, then expand to the right.

(Yes, there are command line tools to modify partitions, but that would be harder than gparted.)

---

### Post by TheFu on 2019-11-15
> **Impavidus said:**
>  (Yes, there are command line tools to modify partitions, but that would be harder than gparted.)

+1.

Much harder.  but if you want, feel free to try with **fdisk **or **parted**.  I don't know anyone who would attempt the type of thing you need using those if gparted was available.

BTW, I would just delete the swap partition, do the slide to the left, then re-add a swap of 4.1G at the end, then mount the partition that has /etc/ inside it and manually fix the swap UUID line inside the fstab.  

If we change anything (location or size) about any partition, expect to manually need to fix the fstab file.  It isn't hard, once you understand what each field in each line means, but to someone who has never seen it before, it can be next to impossible to do.  Regardless, make a backup of the fstab file.  
```
sudo cp fstab fstab-2019.11
```
This is so you can see what it needs to look like later.  Google "ubuntu fstab" for a how-to guide and keep that gparted boot flash drive handy.  You'll need it, most likely.

---

### Post by HermanAB on 2019-11-16
I hope you made a backup of everything, since playing with partitions is a good way to ruin your day...

---

### Post by GirishSharma on 2019-11-16
> **HermanAB said:**
> I hope you made a backup of everything, since playing with partitions is a good way to ruin your day...Yes, as everyone is strictly suggest to take backup before partition operation, now I am stuck how do take complete backup of hard disk (in mine case, I have only one HDD) with Ubuntu and Windows 10 data and metadata. Which tool I should use to take backup and in any case if anything wrong happens, how do I will get the current state of the system.

---

### Post by HermanAB on 2019-11-17
A full backup of course requires a second disk drive as big as the first one.  You can do that with the Ubuntu install CD/USBStick.  You just copy the whole device to another device with cat, dd or several other utilities, for example:
# cat /dev/sda > /dev/sdb

A better way is to only save your data, which should need orders of magnitude less space.

---

### Post by GirishSharma on 2019-11-17
> **HermanAB said:**
> A full backup of course requires a second disk drive as big as the first one.  You can do that with the Ubuntu install CD/USBStick.  You just copy the whole device to another device with cat, dd or several other utilities, for example:
# cat /dev/sda > /dev/sdb

A better way is to only save your data, which should need orders of magnitude less space.

Thanks once again for your reply. As original question was related to partition but now I am asking some questions for backup like :

1.Is there any command to know how much space I need to copy on target drive? 
2.Estimated time.
3.As I am using Gparted live USB, so  # cat /dev/sda > /dev/sdb is need to issue in Gparted session or I can run in normal Ubuntu terminal?
4.Can I say something link  # cat /dev/sda > Google Drive location because I don't have seperate HDD or storage location.

---

### Post by TheFu on 2019-11-18
> **GirishSharma said:**
> Thanks once again for your reply. As original question was related to partition but now I am asking some questions for backup like :

1.Is there any command to know how much space I need to copy on target drive? 
2.Estimated time.
3.As I am using Gparted live USB, so  # cat /dev/sda > /dev/sdb is need to issue in Gparted session or I can run in normal Ubuntu terminal?
4.Can I say something link  # cat /dev/sda > Google Drive location because I don't have seperate HDD or storage location.

1.  fdisk.   sdb must be at least as large as sda.  The entire disk.  This is a bit-for-bit clone of the entire disk. Whether the bits have critical data or random data or no data, doesn't matter.  All of it is going to be cloned.
2.  Longer than you like.
3.  Any Unix that supports 'cat' will work.  The command must be run as root or with sudo.  I've never seen any Unix that doesn't have cat or dd.  I would use dd or ddrescue to clone, but that's me. For backups, I use rdiff-backup with a 100 line script around it to get only the stuff, settings, data, and metadata needed. There isn't a 1 line command to use it for backups. Sorry.
4.  If it works, sure.  If it doesn't.  Nope.  No way would I put an unencrypted, bit-for-bit clone of an entire OS on cloudy storage.  NO FREAKIN' WAY!  Just post your credentials on the internet for the entire world instead.  That would be easier.

You really need a backup solution that has a different disk.  There are many more efficient backup methods. Lots of them are discussed in these forums.

---

### Post by GirishSharma on 2019-11-18
> **TheFu said:**
> 1.  fdisk.   sdb must be at least as large as sda.  The entire disk.  This is a bit-for-bit clone of the entire disk. Whether the bits have critical data or random data or no data, doesn't matter.  All of it is going to be cloned.
2.  Longer than you like.
3.  Any Unix that supports 'cat' will work.  The command must be run as root or with sudo.  I've never seen any Unix that doesn't have cat or dd.  I would use dd or ddrescue to clone, but that's me. For backups, I use rdiff-backup with a 100 line script around it to get only the stuff, settings, data, and metadata needed. There isn't a 1 line command to use it for backups. Sorry.
4.  If it works, sure.  If it doesn't.  Nope.  No way would I put an unencrypted, bit-for-bit clone of an entire OS on cloudy storage.  NO FREAKIN' WAY!  Just post your credentials on the internet for the entire world instead.  That would be easier.

You really need a backup solution that has a different disk.  There are many more efficient backup methods. Lots of them are discussed in these forums.


My current Gparted Screen is showing like this : (Currently running Ubuntu Session)

```


[FONT=courier new]Partition    Name                            File System    Mount Point    Label        Size          Used       Unused       Flags    
/dev/sda1    EFI System Partition            fat32          /boot/efi      ESP          650.00 MiB    50.07 MiB  599.93 MiB   boot,esp 
/dev/sda2    Microsoft reserved partition    unknown                                    128.00 MiB    --         --           msftres    
/dev/sda3    Basic Data partition            ntfs                          OS           899.77 GiB    24.37 GiB  875.40 GiB   msftdata
unallocated                                  unallocated                                 20.00 GiB    --         --
/dev/sda4                                    linux-swap                                   2.86 GiB     0.00 B      2.86 GiB
/dev/sda5                                    ext4           /                             7.14 GiB     5.11 GiB    2.03 GiB
/dev/sda6                                    ntfs                          WINRETOOLS   990.00 MiB   382.29 MiB  607.71 MiB   hidden,diags
unallocated                                  unallocated                                 12.71 MiB    --
[/FONT]

```

I am trying to merge/resize /dev/sda5 with first unallocated entry of 20 GB which I made by Shrink C: in Windows 10.
Will you please mention steps to achieve this as I am not able to take backup neither on our local intranet nor any storage location/device.

---

### Post by GirishSharma on 2019-11-18
Finally, I resized the partition by taking the risk of data loss because I was not having other options. So, I :

1.Booted the system by Gparted Live USB (Made some changes in BIOS by Enabling Legacy Option)
2.First dragged the SWAP to the left. This showed me unallocated entry after Swap entry.
3.Dragged /dev/sda5 (My linux partition) to the left. This showed me unallocated entry after /dev/sda5
4.Expanded /dev/sda5 as much as I could. Now it showed me unallocated 1 MiB and /dev/sda5 expanded.
5.Clicked on Apply Button.
6.Done.

```

girish@girish-OptiPlex-3050:~$ sudo fdisk -l
[sudo] password for girish: 
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: E1D206C6-CD80-4796-8691-87310D959375

Device          Start        End    Sectors   Size Type
/dev/sda1        2048    1333247    1331200   650M EFI System
/dev/sda2     1333248    1595391     262144   128M Microsoft reserved
/dev/sda3     1595392 1888557055 1886961664 899.8G Microsoft basic data
/dev/sda4  1888557056 1894557695    6000640   2.9G Linux swap
/dev/sda5  1894557696 1951469567   56911872  27.1G Linux filesystem
/dev/sda6  1951471616 1953499135    2027520   990M Windows recovery environment

```

Thanks to all of you who participated in my problem and replied.

---

