---
title: "Ubuntu 16.04 Login Loop after mounting new HDD to /home"
date: 2018-01-08
forum: General Help
---

### Post by sstern3 on 2018-01-08
I just completed a new PC build, which due to some indecision on my part has a 128 SSD and two 1TB HDDs. I partitioned the SSD to dual boot windows and linux, and decided to just give each OS its own HDD. The windows side was simple enough, but when I tried to make the linux partition use the other hard drive for the /home directory, I started running into issues. 

I followed the steps for changing /home following this guide: [https://www.tecmint.com/move-home-directory-to-new-partition-disk-in-linux/](https://www.tecmint.com/move-home-directory-to-new-partition-disk-in-linux/)

As far as I can tell, the computer *does* recognize the drive as /home; it would seem that this operation was successful, but that I must have accidentally nicked something else in the system, because when I tried to log in (either as myself or as a guest session) the computer froze for 1-5 seconds before going to a blackscreen and resetting me to the login screen.

I tried all the tips suggested on this page: [http://www.linuxslaves.com/2016/05/3-ways-fix-ubuntu-gets-stuck-login-loop.html](http://www.linuxslaves.com/2016/05/3-ways-fix-ubuntu-gets-stuck-login-loop.html) 
But to no avail; they didn't do anything for me.

Then, I followed the top reply in this thread: [https://askubuntu.com/questions/762831/ubuntu-16-stuck-in-login-loop-after-installing-nvidia-364-drivers](https://askubuntu.com/questions/762831/ubuntu-16-stuck-in-login-loop-after-installing-nvidia-364-drivers)
Interestingly, after following that advice I now *can* log in and reach the desktop as a guest, but *not* on my personal account, which is still caught in the loop. As well, the time it takes to cycle back to the login screen is now much longer.

I'm not sure what's left to do really. I tried "sudo cat ~/.xsession-errors" and got the following message:
openConnection: connect: No such file or directory
cannot connect to brltty at :0

I'm relatively new to ubuntu, so I'm not sure what my next steps are for troubleshooting. Any ideas?

---

### Post by oldfred on 2018-01-09
I recent times I have seen more issues with fstab. It has become more particular or any error stops booting. Before it used to have to time out on most errors and then ask or proceed to boot.

Post these:
cat /etc/fstab
 sudo blkid -c /dev/null -o list 
sudo parted -l

---

### Post by leunam12 on 2018-01-09
Did you use cp to copy your home to the new drive? If you did you are probably facing permission problems. 
The right command is ```
sudo rsync -avXS /home/ /path/to/new/home/
```

---

### Post by sstern3 on 2018-01-09
Here's the fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=3d4679b6-4b51-4184-860b-a716c83f9d5b /             ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb2 during installation
UUID=0028-4A17  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sdb6 during installation
UUID=6e96ed40-5aa1-4b55-b93f-90524b5c63a5 none            swap    sw              0       0
# Set home to sdc1, per Aaron Kili's guide
UUID=3c450312-048b-40cc-b74a-065d21409081 /home         ext4    defaults          0       2

```

The blkid:

```

device                         fs_type     label        mount point                        UUID
-------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                               (not mounted)                      
/dev/sda2                      ntfs        Hard Drive A (not mounted)                      8E5281F85281E575
/dev/sdb1                      ntfs        Recovery     (not mounted)                      B28427328426F90D
/dev/sdb2                      vfat                     /boot/efi                          0028-4A17
/dev/sdb3                                               (not mounted)                      
/dev/sdb4                      ntfs        WindowsPart  (not mounted)                      8AF22AB2F22AA285
/dev/sdb5                      ext4                     /                                  3d4679b6-4b51-4184-860b-a716c83f9d5b
/dev/sdb6                      swap                     [SWAP]                             6e96ed40-5aa1-4b55-b93f-90524b5c63a5
/dev/sdc1                      ext4        LinuxHDD     /home                   3c450312-048b-40cc-b74a-065d21409081

```

And the parted:

```

Model: ATA WDC WD10EADX-22T (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
 2      135MB   1000GB  1000GB  ntfs         Basic data partition          msftdata


Model: ATA ADATA SU800 (scsi)
Disk /dev/sdb: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  524MB   523MB   ntfs            Basic data partition          hidden, diag
 2      524MB   628MB   104MB   fat32           EFI system partition          boot, esp
 3      628MB   645MB   16.8MB                  Microsoft reserved partition  msftres
 4      645MB   65.1GB  64.5GB  ntfs            Basic data partition          msftdata
 5      65.1GB  124GB   58.8GB  ext4            Basic data partition          msftdata
 6      124GB   128GB   4096MB  linux-swap(v1)


Model: ATA ST1000DM010-2EP1 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  1000GB  1000GB  ext4         primary

```

---

### Post by oldfred on 2018-01-09
Your sdc1 is not showing an UUID??
Is it reformatted or something else wrong with it?

Also with UEFI grub really wants to install to the ESP on drive seen as sda. You have the ESP on sdb. 
You can convert Microsoft reserved to ESP, FAT32 with boot flag. The Microsoft reserved is required before the first NTFS partition that you boot from. So Microsoft partitioning tools always add that first, but only required on drive you boot from.
Or you could rearrange drives. You can plug SSD into SATA0 or first port on motherboard. And plug other drives in order, do not skip ports. I have in past and that can lead to issues. My flash drive as sdf has become sdb and my other hard drives move up a letter. I guess I skipped SATA1 port. But not sure if Windows would have any issues with drive order.

---

### Post by sstern3 on 2018-01-09
My bad, I think I missed sdc1's UUID when copying over from pastebin. sdc1 does have a UUID, and as far as I can tell it does match the one in fstab. I have edited the post to reflect that.

As for your second paragraph, I'm afraid I don't understand these concepts very well. So far, the Windows partition has been functioning pretty much perfectly (just some issues remembering time-of-day), so I'm hesitant to make any changes. After all, last time I tried to fix something that wasn't necessarily broken, I dug myself into this mess. What would change if I followed your tips, and more importantly, what actually would I be changing?

---

### Post by sstern3 on 2018-01-09
> **leunam12 said:**
> Did you use cp to copy your home to the new  drive? If you did you are probably facing permission problems. 
The right command is ```
sudo rsync -avXS /home/ /path/to/new/home/
```

As far as I can tell, what I did was essentially copy /home onto a new drive, but then told the OS that the drive itself *is* /home. It would make sense if permissions were causing issues, but because of the way I did this I'm pretty sure /path/to/new/home/ would be identical to /home/, no? Or am I confused about how mounting works?

---

### Post by oldfred on 2018-01-09
This has details on moving /home from inside / to a separate partition.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) 

Also shows commands to set ownership  & permissions of specific files in /home and all of /home.
[https://ubuntuforums.org/showthread.php?p=6161267](https://ubuntuforums.org/showthread.php?p=6161267)

Only for /home, not any other system folder.

 sudo chown -R $USER:$USER /home/$USER
sudo chmod -R a+rwX,o-w /home/$USER 
Note -R is recursion or all sub-folder & files are also changed.

---

### Post by sstern3 on 2018-01-09
Thank you! Your suggestion provided exactly what I needed; it seems that while I had reset ownership of /home after remounting, I had not changed the permissions for any of its contents. Recursively changing ownership within /home/$user solved the problem.

Notably, upon logging in I still lacked my taskbar/launcher thing, but that was solved by following the answer by dr_smit in this thread:
[https://askubuntu.com/questions/761035/ubuntu-16-04-no-menu-bar-or-launcher-help](https://askubuntu.com/questions/761035/ubuntu-16-04-no-menu-bar-or-launcher-help)

I'll look into your UEFI advice, too. Thanks again!

---

