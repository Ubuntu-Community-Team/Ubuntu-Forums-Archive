---
title: "How to create several partitions and tell ubuntu installer which one to install in?"
date: 2021-11-27
forum: General Help
---

### Post by dora5 on 2021-11-27
I want to create several partitions using Disks and then tell the installer which partition to install Ubuntu into.

I keep ending up wtih very strange partitions.  Even two 1000 Gb partitions on a 1000 GB hard drive!

I can not find where it allows me to choose which existing partition to install in.

Do I have to manually set up all my partitions including home and whatever, to be left with free space for the rest of my partitions, or, can I do what MAKES SENSE and create several partitions, tell the installer which one to install in and then let it do its thing within that partition.

I do not believe that people with existing partitions and files on other partitions can't use what partition they want to. 

Someone else asked the same question on one of these forums and got told how to install alongside windows when he specifically said files were on the other partition, everything except how to install on the partition that he wanted to install on.

When I google how to install on a specific partition in Ubuntu all I can find is how to install Ubuntu alongside Windows.

Selecting a partition to install on SHOULD be the same difference as selecting a drive to install on.

Note that ubuntu uses remaining free space to install alongside another operating system, it's another procedure entirely.

I specifically need to create partitions and tell it where to install Ubuntu. What I do or did with the other partitions is for me to worry about.  How specifically do I do that?

Highlighted /dev/sdb2 ext 4 
Device for boot loader installation picked /dev/sdb2


Clicked on Install now


It says "no root file system is defined.   Please correct this from the partitioning menu."


If I try to create my partitions inside the partition sdb2 manually by highlighting sdb2 and trying to create a swap partition on it, it won't let me add a partition to sdb2.   



Thanks!

---

### Post by dragonfly41 on 2021-11-27
Ubuntu LiveUSB *does* give you the option to choose which partition to install in .. using (from memory) "Something else" (read links from OldfFred and you will be on the right path).

Regarding ..

[COLOR=#000000]> Someone else asked the same question on one of these forums and got told how to install alongside windows when he specifically said files were on the other partition, everything except how to install on the partition that he wanted to install on.

Perhaps the OP was not following the best route. I usually write to suggest avoid sharing Windows drive.
Windows can be an awkward tenant in a drive shared with Ubuntu.[/COLOR]

---

### Post by deadflowr on 2021-11-27
> It says "no root file system is defined. Please correct this from the partitioning menu."
You need to set the mount point for / (root).
This thread probably explains it better as it has Pictures: [https://ubuntu-mate.community/t/install-ubuntu-mate-using-the-something-else-method/651]("https://ubuntu-mate.community/t/install-ubuntu-mate-using-the-something-else-method/651")

In general, in Something Else, you highlight the wanted partition, click on change (or edit if that's the option) then set the file system type (usually ext4) and then set the mount point,
for full file system just use /.

---

### Post by grahammechanical on 2021-11-27
> f I try to create my partitions inside the partition sdb2 manually by  highlighting sdb2 and trying to create a swap partition on it, it won't  let me add a partition to sdb2.   

As you have found out it is not possible to create a partition inside a partition. Years ago hard drives had a Master Boot Record (MBR) partitioning scheme. That MBR scheme only allowed four primary partitions. To have more than four partitions we had to use one of the four allocated Primary partitions as a special kind of partition called an Extended partition. Then inside that Extended partition we could create many Logical partitions.

On modern computer systems hard drives have GUID Partitioning Table (GPT) as the partitioning scheme. We are not limited to four primary partitions but can have many primary partitions. We do not need to have an Extended partition with Logical partitions inside the Extended partition. So unless you are using MBR partitioning it is no surprise that you could not create a swap partition inside the sdb2 partition.

Ubuntu stopped using a swap partition with the release of Ubuntu 18.04. So, as this was a new install of perhaps 20.04 then you did not need a swap partition. The installer would have created a swap file.

Regards

---

### Post by oldfred on 2021-11-27
Deadflowr's link which has screen shots should be what you need.
But you must know if system is UEFI or BIOS. Hardware since about 2012 is normally UEFI. 

If newer user having just large / (root) as ext4 is all you really need. 
With UEFI it will auto find ESP - efi system partition on first drive and create a swap file. But you must have an ESP on first drive. Grub install selection with Ubuntu's Ubiquity installer does not work, it only uses ESP on first drive.

If BIOS, you typically want grub installed to same drive as Ubuntu. You always select a drive, never a partition for grub install.

If more advanced & understand partitioning, you can have separate partition for /home. You select or create another ext4 partition during install.
That is also somewhat easier as installer creates entry into fstab and gives you ownership & permissions.

Even more advanced would be separate data partition(s). You create those before or after install, but usually cannot add them during install. You then have to manually add to fstab and give yourself ownership & permissions.

What brand/model system? many require settings in UEFI.
If using UEFI, better to use gpt partitioning. Note that changing from MBR to gpt will erase drive.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

My screen shots are really old. I should update them.
But the screens are still the same, just somewhat updated graphics/colors.

---

### Post by ActionParsnip on 2021-11-28
If you use the "something else" option then you can partition as you like. You will neeyat least a 50Gb partition for the root file system. You can then make the rest of the space be used as you wish. You can even specify non standard mount points in the installer. Most users like a separate partition for /home
Alternatively you can just let the Ubuntu installer setup the disk layout for you and be fine

---

### Post by yancek on 2021-11-28
>  I keep ending up wtih very strange partitions.  Even two 1000 Gb partitions on a 1000 GB hard drive! 

That sounds very much like you have the older Legacy/MBR  system as that would show the Extended partition as 1GB and you could also have a 1GB Logical partition.

>  Do I have to manually set up all my partitions including home and whatever 

What you want is a 'manual' install and the Ubuntu installer calls that  option  'Something Else".  There are any number of ways to install based on people's preferences and it would not realistically be possible to list them all on the installer so you get the 'manual' OR 'Something Else' option.

>   Device for boot loader installation picked /dev/sdb2

The above quote is a very basic error.  Since you indicate that you are installing only Ubuntu, the install of the bootloader to a partition (/dev/sdb2) will never work.  If you had another operating system install with its own bootloader it would be possible but in your case installing only Ubuntu, you would need to select the device, /dev/sdb and then set sdb to first boot priority in the BIOS firmware.

THe links posted above should be more than enough to correctly install Ubuntu.

---

### Post by TheFu on 2021-11-28
Just to add another option ... not suggesting this to anyone else.

After the installer starts and networking is up, I switch to a different tty then install ssh and copy over a partition + LVM script that sets up a disk the way I prefer.  This script uses no GUI.
Someone else had the same idea: [Https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144](Https://ubuntuforums.org/showthread.php?t=2465735&p=14053144#post14053144)

The tools used, in order, are 
 sgdisk pvcreate vgcreate lvcreate lvscan mkfs mkswap 

Then I switch back to the installer tty and use the "Do something else" option to connect the partitions and LVs to file systems and mount locations.  In the end, I have a system that has 1 disk, 3 partitions, and some number of LVs sized the way I prefer for root, home, var, swap just to get started.  I size them to be just what is needed for a few months of use. This is because LVM allows extending an LV in 5 seconds while the system keeps running. 
If I need RAID1, during the install, setting up the LVs without RAID is the method, but I can use lvconvert to create a mirror as needed on anther physical disk.  Flexibility.  That's what this effort provides. I've never been able to guess the correct size of storage for any need in 20+ yrs. With LVM, I don't have to be clairvoyant. For plain partitions that need to be RAID'd, that's a manual thing to basically /boot and /boot/EFI are involved.

Instead of using ssh, perhaps wget or curl could be used to get the script from another system .. or sneaker*net via USB?

Just another option for consideration.

---

