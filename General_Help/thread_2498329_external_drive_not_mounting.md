---
title: "external drive not mounting"
date: 2024-06-09
forum: General Help
---

### Post by angel mike on 2024-06-09
I have a Seagate external storage device which usually mounts with no trouble . I decided to install Ubuntu 24.04 and tried to use it but it could not mount.
I found the the 24.04 so full of bugs that I reinstalled Ubuntu 22.04
I think the 24.04 must have done something to the Seagate.
I now get an error message saying 'unknown' error.

PS: Title should read 'External storage device not mounting'

---

### Post by oldfred on 2024-06-09
Is external drive gpt partitioned?
post this in code tags.
sudo parted -l
lsblk -f

---

### Post by yancek on 2024-06-09
It isn't clear what you are doing but I'm guessing you installed 24.04 on a different drive and attempted to mount some filesystem on a partition on the external drive you refer to, is that correct?  It would be useful to indicate what filesystem type is on the partition(s) on the external drive you failed to mount.  Did you attempt to mount from a terminal and if so, what command specifically did you use?  Posting the output of the commands suggested in post 2 would be a first step in getting help.

---

### Post by angel mike on 2024-06-09
Thanks for the quick response. 
First to Oldfred 
```
[                         sudo parted -l
 [sudo] password for mgstevens:  
 Model: Micron 2300 NVMe 512GB (nvme)
 Disk /dev/nvme0n1: 512GB
 Sector size (logical/physical): 512B/512B
 Partition Table: gpt
 Disk Flags:  
 
 
 Number  Start   End     Size    File system  Name  Flags
  1      1049kB  1128MB  1127MB  fat32              boot, esp
  2      1128MB  512GB   511GB   ext4
 
```
 
 ```
lsblk -f  
 NAME FSTYPE FSVER LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINTS

 nvme0n1
 &#9474;                                                                            
 &#9500;&#9472;nvme0n1p1
 &#9474;    vfat   FAT32       E97D-4A24                                 1G     1% /boot/efi
 &#9492;&#9472;nvme0n1p2
      ext4   1.0         209592ba-0b6b-4935-925d-65cecb8b8ae6  432.3G     2% /
 mgstevens@mgstevens-XPS-13-9310:~$ ]
```

---

### Post by angel mike on 2024-06-09
Thanks Yancek - All I did was to download the iso of 24.04 from the official site and make a bootable usb using the disk creator. I then changed the boot order to load the usb and the program  installed with no problems.
It worked ok  until I decided to try and mount the seagate storage - it would not mount. I then read a few reviews some said they had the same problem. At that point I decided to reinstall version 22.04 from a usb that I have used before. It was then I found that I could not mount the seagate.

---

### Post by angel mike on 2024-06-09
I am now finding on my laptop that Firefox is not loading  after using it a few times so I have to restart the laptop. It also occasionally flickers -never done that before ! Have I picked up a bug/virus ?

---

### Post by oldfred on 2024-06-09
Please use Code Tags when posting terminal output. And loops devices are snap apps, so not real devices.
Code Tags
[https://ubuntuforums.org/showthread.php?t=2497846](https://ubuntuforums.org/showthread.php?t=2497846)

You show install on NVMe drive, but then no sda or external drive? 
Was it plugged in when you ran commands?

Should have had you run this as it excludes snaps/loop, which I removed when I added code tags to your post.
lsblk -e 7 -o name,fstype,size,fsused,label,UUID,mountpoint

---

### Post by angel mike on 2024-06-10
Sorry about that Oldfred - yes forgot to plug in the seegstate. Here is the correct version I hope thanks.

```


$ lsblk -f 
NAME FSTYPE FSVER LABEL UUID                                 FSAVAIL FSUSE% MOUNTPOINTS
loop0
     squash 4.0                                                    0   100% /snap/bare/5
loop1
     squash 4.0                                                    0   100% /snap/core20/1405
loop2
     squash 4.0                                                    0   100% /snap/core20/2318
loop3
     squash 4.0                                                    0   100% /snap/firefox/1232
loop4
     squash 4.0                                                    0   100% /snap/gnome-3-38-2004/143
loop5
     squash 4.0                                                    0   100% /snap/gnome-3-38-2004/99
loop6
     squash 4.0                                                    0   100% /snap/gtk-common-themes/1535
loop7
     squash 4.0                                                    0   100% /snap/gtk-common-themes/1534
loop8
     squash 4.0                                                    0   100% /snap/snap-store/575
loop9
     squash 4.0                                                    0   100% /snap/snapd-desktop-integration/10
loop10
     squash 4.0                                                    0   100% /snap/snapd/21759
sda                                                                         
&#9492;&#9472;sda1
     ntfs         Seagate Backup Plus Drive
                        EAF65B44F65B1065                                    
nvme0n1
&#9474;                                                                           
&#9500;&#9472;nvme0n1p1
&#9474;    vfat   FAT32       E97D-4A24                                 1G     1% /boot/efi
&#9492;&#9472;nvme0n1p2
     ext4   1.0         209592ba-0b6b-4935-925d-65cecb8b8ae6  432.2G     2% /
mgstevens@mgstevens-XPS-13-9310:~$ 

  	 	 	 	   $ sudo parted -l
 [sudo] password for mgstevens:  
 Model: Seagate BUP Slim BK (scsi)
 Disk /dev/sda: 1000GB
 Sector size (logical/physical): 512B/4096B
 Partition Table: msdos
 Disk Flags:  
 
 
 Number  Start   End     Size    Type     File system  Flags
  1      1049kB  1000GB  1000GB  primary  ntfs         boot
 
 
 
 
 Model: Micron 2300 NVMe 512GB (nvme)
 Disk /dev/nvme0n1: 512GB
 Sector size (logical/physical): 512B/512B
 Partition Table: gpt
 Disk Flags:  
 
 
 Number  Start   End     Size    File system  Name  Flags
  1      1049kB  1128MB  1127MB  fat32              boot, esp
  2      1128MB  512GB   511GB   ext4
 

```

---

### Post by ActionParsnip on 2024-06-10
Appears to be NTFS formatted. I suggest you plug the device into a Windows system (NTFS is proprietary and only Microsoft truly knows how it works) and run a full chkdsk to make sure it is complete and consistent. You can then use the safe remove feature in the OS to flush the disk cache (wait for Windows to tell you to ununplug it) then unplug. You can then reconnect it to the Ubuntu system and test

---

### Post by yancek on 2024-06-10
With a problem such as you were having, posting the filesystem type  is basic information you should post initially.  You were asked this in post 3!  Since your other drive has only  EFI and Linux partitions, why do you have a drive with a partition with a windows filesystem?  Are you sharing this drive with other computers using windows?  If that is the case, it may be a hibernation problem but could be any number of problems with the ntfs filesystem.   If you are going to continue to use a windows filesystem on a drive, you need to be aware of this. 

As pointed out above, you will need to use windows to run chkdsk or other software to fix the problems on the proprietary filesystem.

---

### Post by angel mike on 2024-06-10
Thanks for the replies - I do nor use Microsoft Windows but I have a usb with Windows 10 which I could use on my desktop PC but going away for a week so there will be a delay in response. I have never changed any flags. I described the procedure I used to load Ubuntu 24.04.
More to the point my Firefox
has been effected and the seagate will not mount on my desktop PC which has Ubuntu 22.04 and never given a problem mounting the seagate

---

### Post by angel mike on 2024-06-11
If you read the comments on this link you will see that using Ubuntu 24.04 is cause for concern [https://linuxiac.com/do-not-try-to-upgrade-to-ubuntu-24-04-at-this-time/](https://linuxiac.com/do-not-try-to-upgrade-to-ubuntu-24-04-at-this-time/)

---

### Post by coffeecat on 2024-06-11
> **angel mike said:**
> If you read the comments on this link you will see that using Ubuntu 24.04 is cause for concern [https://linuxiac.com/do-not-try-to-upgrade-to-ubuntu-24-04-at-this-time/](https://linuxiac.com/do-not-try-to-upgrade-to-ubuntu-24-04-at-this-time/)

Not relevant to your problem. That link is about an issue that affected upgrades 23.10 -> 24.04 or 22.04 -> 24.04 very shortly after the release of 24.04 and which I believe has been fixed now. You fresh-installed 24.04 and should not have encountered the issues described. The article is actually titled "Do not try to **Upgrade** to Ubuntu 24.04 at This Time." It does not say "Do not install 24.04."

I have to say that upgrading, rather than fresh installing, to a new release so soon after its release is - er - adventurous, or perhaps unwise, so I have no sympathy for the abusive and illiterate moaners and groaners in the comments section of that article. There are a couple of thoughtful comments there, but many are just unhelpful background noise.

Fwiw I installed 24.04 fresh and have had zero problems so far.

---

### Post by yancek on 2024-06-11
>  Thanks for the replies - I do nor use Microsoft Windows

What exactly then is the point in having an external drive which is entirely in a windows filesystem format?  There is no logical reason to do that and you have come across one of the primary reasons NOT to do it.  When there is a problem with the proprietary filesystem, you need proprietary software to repair it.

---

### Post by angel mike on 2024-07-17
Thank everyone for your responses - an amazing number!
I eventually solved the problem by using Disks and used the repair option - which was successful almost immediately ! It must have been something simple. I will close this thread but not before issuing a warning. 

Do not updated to Ubuntu 24.04 in its present state ! My problem arose when I tried to mount my external hard drive ( Seagate 1 TB) - it messed up the file file system.

---

