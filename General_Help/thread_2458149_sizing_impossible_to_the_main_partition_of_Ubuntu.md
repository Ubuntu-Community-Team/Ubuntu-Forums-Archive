---
title: "sizing impossible to the main partition of Ubuntu"
date: 2021-02-17
forum: General Help
---

### Post by dunivixs on 2021-02-17
Hello all, 
I tried to install a game from Lutris but this one is too voluminous for my partition Ubuntu, its size is 107 Go (There is 30 Go left but I need 38 Go to download the game)
To find some place, I removed some files/folders from my windows 7 's partition.
But I cannot modify the size of my Ubuntu's partition because this one is running by my operating system. 
So I started my PC on a Gparted liveUSB, but I could not  stretch my partition (I could only stretch Windows 7's partition)

Here is an image which will allow you to more understand my probleme :
[https://cdn.discordapp.com/attachments/434408303817261056/811637575328202816/Capture_decran_de_2021-02-17_17-36-40.png](https://cdn.discordapp.com/attachments/434408303817261056/811637575328202816/Capture_decran_de_2021-02-17_17-36-40.png)
(The partition that I wand to spread is the orange (/dev/sda6) and I took some space from the /dev/sda2)

Thank you very much for your help !!

Sorry it is in french, because i'm french

---

### Post by TheFu on 2021-02-17
logical partitions must be completely contained inside any extended-primary partition. Only 1 extended partition i allowed. It cannot be resized if there are any logical partitions.

This is one more reason that GPT partitioning is better than msdos/mbr partitioning.
wikipedia has articles on each of these things.

BTW, ```
sudo fdisk -l /dev/sda
``` would show the partition data clearly.

---

### Post by CelticWarrior on 2021-02-17
I wouldn't touch any of this.

In order to use the now unallocated space at the left everything inside the extend partition would need to be moved and resized, starting by the extended partition itself, a very risky set of operations.

Do yourself and us a favor and do NOT use an obsolete and unsupported OS like Windows 7, at least not online. Better reinstall Ubuntu using the whole disk and say goodbye forever to Windows 7.

---

### Post by Impavidus on 2021-02-17
It can be done, but it's a bit risky.

First of all, you cannot modify a partition when it's in use, so you have to boot a live disk (like the one you used to install Ubuntu). On the live disk you'll find a tool named gparted (I think Kubuntu comes with a different but similar tool), which you can use to edit partitions. First you have to move partition 4 to the left, then extend partition 3 to the left, then expand partition 6. These are all slow operations with a relatively high risk of data loss.

I don't know what's inside partition 4, but it's a bit strange. It's a small fat32 partition. These get rarely nowadays, except as efi partitions, but you use a legacy system, so you don't need an efi partition. Maybe it was automatically created but not used?

---

### Post by dunivixs on 2021-02-18
In fact I did not create this partition an it is empty. I do not why it exists !!

I will try to move the partition 4 on the left next to the 2.
Could I move it from Ubuntu with Gparted ? 
And then I will spread partition 3 then partition 6 with Gparted LIVE USB. 
On Friday I will say you if that has worked.
Thanks

---

### Post by Hagar Delest on 2021-02-18
For the record, "cross posting" with this topic: [https://ubuntuforums.org/showthread.php?t=2458147](https://ubuntuforums.org/showthread.php?t=2458147)

---

### Post by Dennis N on 2021-02-18
> In fact I did not create this partition an it is empty. I do not why it exists !!
The fat32 partition is automatically created by the 20.04 installer when you install in BIOS mode using some of the possible options. One option which does this is the "Erase disk and install..." option, which produced these partitions in a vm:

```
Disk /dev/vda: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  538MB   537MB   primary   fat32        boot
 2      539MB   21.5GB  20.9GB  extended
 5      539MB   21.5GB  20.9GB  logical   ext4
```

(The fat32 partition is empty - it's needed for EFI system partitiion in UEFI systems.)

You may have used an "alongside" option that becomes active when another OS is present.

---

### Post by grahammechanical on 2021-02-18
I have two hard drives. One is MBR partitioned format with an Extended partition and Logical partitions inside it. One of these partitions contains a version of Ubuntu (20.10). And the drive also has my data partition. The other hard drive is GPT partitioned format and has several operating systems on it. Including Ubuntu 20.04 & 21.04 as well as some other OS.

Over the years I have deleted; created; moved and expanded partitions depending upon my need to try out different operating systems. It is scary but nothing has ever broken. I set GParted to apply one operation at a time. We can list several operations in GParted but waiting for them all to finish before finding out if something has gone wrong is a bit too much for my nerves.

Regards

---

### Post by dunivixs on 2021-02-19
According to this picture : [https://cdn.discordapp.com/attachments/434408303817261056/812236750285045780/Capture_decran_de_2021-02-19_09-18-45.png](https://cdn.discordapp.com/attachments/434408303817261056/812236750285045780/Capture_decran_de_2021-02-19_09-18-45.png)
I have to unmount the partition /dev/sda4; so I did and when I want to move like that : [https://cdn.discordapp.com/attachments/434408303817261056/812237569734737920/Capture_decran_de_2021-02-19_09-21-19.png](https://cdn.discordapp.com/attachments/434408303817261056/812237569734737920/Capture_decran_de_2021-02-19_09-21-19.png)
 there is that message : [https://cdn.discordapp.com/attachments/434408303817261056/812237586508677130/Capture_decran_de_2021-02-19_09-21-24.png](https://cdn.discordapp.com/attachments/434408303817261056/812237586508677130/Capture_decran_de_2021-02-19_09-21-24.png)

That scares me because in the warning it talks about the "/boot" and the partition that I want to move is the "/boot/efi".
If I move the partition /dev/sda4, will I have problems to start my computer on Ubuntu ?

What do you suggest for me ?

Thanks

---

### Post by Hagar Delest on 2021-02-19
Since you've installed Ubuntu after Windows, I think that Grub has been installed in the MBR. Since it has not been changed (should be in the first partition I think), then it should not be a problem.
However, if there is an issue, there are ways to fix GRUB afterward, see: [https://askubuntu.com/questions/299886/partitions-is-it-safe-to-move-partition-containing-boot](https://askubuntu.com/questions/299886/partitions-is-it-safe-to-move-partition-containing-boot).
I did wreck my system few months ago and I managed to fix the boot loader with the commands found on the net (I think that was the same as in the askubuntu thread). So, in case of issue, no panic, be sure that you can boot from your usb key and that's all.
Make sure you've a backup of all your user data, just in case.
Wait for other replies if you need several opinions.

---

### Post by dunivixs on 2021-02-19
Thanks
I will move the partition on the left and then reboot my computer to see if Ubuntu starts again. 
In case I have my Windows 7 operating system for the moment, waiting that I install Ubuntu, and yes I will save all my data.
I will do that on the afternoon

Dunivixs

---

### Post by Hagar Delest on 2021-02-19
Great.
As advised by grahammechanical, do the GParted operations one by one. First move sda4 and apply the change with the green button. Then extend sda3 and apply the change and then resize sda6 if needed.
It may take some time to move the 66Gio.

Note: I stand corrected, you've not a MBR boot but an EFI (I mixed the information with another post of the topic). But then, it seems to be more robust. Higher chances that there is nothing to do afterward.

---

### Post by dunivixs on 2021-02-19
After having moved my two partitions, every thing looks to like to work good.
To expand my /dev/sda6 it takes 30 minutes.
I have also created a live USB of Ubuntu just in case.

Thank you very much all !

---

### Post by Hagar Delest on 2021-02-19
Well done!

---

