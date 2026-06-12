---
title: "How to move grub from sda to sdb?"
date: 2022-04-17
forum: General Help
---

### Post by cooperino on 2022-04-17
Hello,
I've asked in many places and also tried other solutions I found online, and none of them worked, and looks like no 1 has an answer for what is seemingly supposed to be a simple thing to do.
If you have the answer please guide me completely with specific commands because I will not be able to do it alone, I am not that high level in Linux/Ubuntu.

 I have 2 SSDs:
- First is a 250GB SSD with only Windows 10 installed on it.
- Second is a 500GB SSD originally installed with Windows 10. Then I shrank 200GB of it for Ubuntu (20.04).

I specified the boot drive during installation to be sdb, which is the 500GB, but it still installed GRUB inside sda1(/boot/efi) partition, alongside Windows Boot Manager of sda.

Using GPT

I tried the grub-install method ([FONT=var(--ff-mono)]grub-install  /dev/sdb) - it showed some output in terminal, but after the restart, the situation is the same: the boot partition remains in sda with GRUB in it.
[/FONT]
How can I move GRUB to the correct partition on sdb? Either alongside Windows Boot Manager of sdb (as it is now with sda), or maybe on a different partition on sdb.

I do not want to physically unplug the 250GB and then install Ubuntu, I want to solve it in a way that won't make me open the PC case every time I want to format my PC

Thanks!

---

### Post by oldfred on 2022-04-17
With UEFI, the grub-install uses the mount of the FAT32 partition in fstab which is the ESP to reinstall into.
You have to have an ESP on sdb & change UUID in fstab to the new UUID.

cat /etc/fstab
lsblk -f

---

### Post by cooperino on 2022-04-17
cat /etc/fstab shows:
/boot/efi was on /dev/sda2 during installation (the wrong one)

lsblk -f shows:
```
sda
|___sda1
|___sda2
       vfat       <some string>     65.5M     32% /boot/efi

sdb
|___sdb1
       vfat       <some string>
```


The rest of the partitions are either ntfs or ext4 (no esp)

How should I proceed from here?

Note that when checking /boot/efi from Windows, I see that it holds both grub (ubuntu) and Windows Boot Manager, should i somehow do the same and move both Windows Boot Manager and ubuntu to sdb1? (also I noticed on first SSD it's on sda2 but on second SSD it's on sdb2)

---

### Post by oldfred on 2022-04-17
I would keep Windows boot files in the Windows drive's ESP.

You need to change UUID in fstab for mount of ESP.
Then reinstall grub.
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
sudo nano /etc/fstab
sudo mount -a  # except I have found that this does not always remount the ESP. Only reboot seems to work.
sudo grub-install

Then check that UEFI has correct partUUID/GUID/ # compare to lsblk from above
sudo efibootmgr -v
And that efi on sdb1 has correct folders & grub.cfg has correct UUID.

---

### Post by cooperino on 2022-04-18
> **oldfred said:**
> I would keep Windows boot files in the Windows drive's ESP.

You need to change UUID in fstab for mount of ESP.
Then reinstall grub.
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
sudo nano /etc/fstab
sudo mount -a  # except I have found that this does not always remount the ESP. Only reboot seems to work.
sudo grub-install

Then check that UEFI has correct partUUID/GUID/ # compare to lsblk from above
sudo efibootmgr -v
And that efi on sdb1 has correct folders & grub.cfg has correct UUID.


Success! Thank you!

The only issue is that I changed to the UUID of the /boot/efi, and not /esp.. I did not know how to create /esp?

With GParted, esp is simply shrinking some 100MB fat32 and naming it /esp?

Or it's something that can be done only during installation?

So currently ubuntu and Windows Boot Manager are on the same /boot/efi partition

*I had to manually delete the ubuntu bootloader from the first drive's /boot/efi and then also remove the entry from the BIOS

---

### Post by oldfred on 2022-04-18
The ESP - efi system partition is mounted at /boot/efi and is at /EFI/ubuntu or /boot/efi/EFI/ubuntu.

Like this from parted:
```
[FONT=monospace][COLOR=#000000]Number  Start   End     Size    File system     Name                  Flags [/COLOR]
 1      1049kB  536MB   535MB   fat32           EFI System Partition  boot, esp


[/FONT]
```

---

### Post by cooperino on 2022-04-18
Oh so in my case it's /boot/efi, I see it slightly different on GParted:
```
Name                      File System       Mount Point        Size           Used          Unused         Flags
EFI system partition    fat32               /boot/efi              100.00MiB    35MiB        65MiB            boot, esp
```

So if Windows already created the esp partition and you told me to make a new esp for ubuntu, should I just shrink some 100MiB for a second esp partition after this one and mount it before installing grub, change to its UUID in fstab and install grub? (And then end up with 2 esp partitions if that's possible?)

---

### Post by oldfred on 2022-04-18
Only one ESP per drive.
You only must have one ESP per system.
I do prefer to have one per drive, but that is not required.
Ubuntu expects ESP to be on first drive that UEFI/BIOS sees, otherwise grub install fails.

---

### Post by Dennis N on 2022-04-18
> And then end up with 2 esp partitions if that's possible?
You can have more than one EFI system partition (ESP) per drive. The UEFI specification does not restrict the number. For example, one drive in my computer uses 3 ESPs (below). In some situations, you need more than one. 

```
Disk /dev/sdc: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: Samsung SSD 850 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: B6E97BD6-2B6E-4A3F-B555-78D1815E9522

Device         Start       End   Sectors   Size Type
/dev/sdc1       2048    165887    163840    80M [COLOR="#FF0000"]EFI System[/COLOR]
/dev/sdc2     165888  53413887  53248000  25.4G Linux LVM
/dev/sdc3   53413888 106661887  53248000  25.4G Linux filesystem
/dev/sdc4  106661888 106825727    163840    80M [COLOR="#FF0000"]EFI System[/COLOR]
/dev/sdc5  106825728 297289727 190464000  90.8G Linux LVM
/dev/sdc6  297289728 297453567    163840    80M [COLOR="#FF0000"]EFI System[/COLOR]
/dev/sdc7  297453568 543213567 245760000 117.2G Linux LVM
/dev/sdc8  543213568 551405567   8192000   3.9G Linux swap
/dev/sdc9  551405568 858605567 307200000 146.5G Linux LVM

  
```

---

### Post by cooperino on 2022-04-19
I created a new fat32 partition. but it has no mount point like the original /boot/efi, so what do I write in fstab?

Right now it's:
```
UUID=ABCD-1234 /boot/efi       vfat    umask=0077      0       1

```
but since I don't have /boot/efi what do I write there instead? What should I replace this line assuming I only have the UUID without mount point?

---

### Post by oldfred on 2022-04-19
I have seen systems that only work with one ESP. UEFI spec does say multiple allowed.
But if one drive, most do not need multiple ESPs.

For users who want multiple ESP, actually only have one FAT32 partition flagged as the ESP, but have boot files in those FAT32 partitions and grub will boot them. UEFI only needs to see one ESP to find grub.

If you have /EFI/ubuntu in another ESP, copy that & /EFI/Boot into you new FAT32 partition.

---

### Post by cooperino on 2022-04-19
thank you.
I have a few problems now, one of them is on this new post: [https://ubuntuforums.org/showthread.php?t=2473963](https://ubuntuforums.org/showthread.php?t=2473963)

Please understand that since I'm really novice with this, I might be confusing with things and it might make no sense to you.

I did make a new fat32 partition, sdb5 using GParted, and it's empty.

But, it has no flags and I did not have an option to set flags when creating this partition. So I couldn't set it to esp, so it's just an empty partition, but no /EFI/ubuntu there.
What are the steps to make this partition esp, create a EFI/Ubuntu folder and copy the files there?

Also, I tried another method to install GRUB on this partition, which is the solution you provided earlier: to change the UUID in fstab to the new partition and use mount -a, then grub-install. But in this case that didn't work because the new partition doesn't have a mount point.. what exactly is this mount point and how can I set a mount point to the new partition?

---

### Post by oldfred on 2022-04-19
The mount has to be as shown.
But if /boot/efi does not exist then it will not work.
Does mount show mount of the old efi partition?

If you use gparted and right click, it gives you all the partition parameters. If you add esp, it will also add boot.
In Boot-Repair you can use advanced mode, choose total grub reinstall & choose drive sdb (not the ESP) and it should correctly install.

---

