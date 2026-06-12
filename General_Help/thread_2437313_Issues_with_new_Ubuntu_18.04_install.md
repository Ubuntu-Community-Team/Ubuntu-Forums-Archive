---
title: "Issues with new Ubuntu 18.04 install"
date: 2020-02-21
forum: General Help
---

### Post by davy jones on 2020-02-21
I just installed Ubuntu 18.04. I previously had 14.04 and I replaced it using the 'something else' option in the installer. I retained my previous /home partition without formatting it. I'd previously done an install which had not used my preexisting /home partition, but I did not like that, so I reinstalled it. Now I'm facing a few problems:

1. Files (Nautilus) does not have a side bar that enables me to access folders other than Home. There doesn't seem to be any straightforward way to access any other folders. Only way is using the address bar. I need a fix for this.
2. To access hidden files and folders in my Home folder and any other folders other than Home, I have to enter my password. This wasn't the case in my 14.04 install. I need to ensure that I can open all of this without having to enter my password every time.
3. I have an NTFS partition in my HDD which contains all my data like music, videos, pictures etc. I don't see this in /media in the new install. It's not even visible in Disks. How do I access this?

My hunch is that the saved settings in my /home partition have caused these issues, since none of them happened when I hadn't used this /home partition. I just don't know how to fix these. Please help.

---

### Post by oldfred on 2020-02-21
Post these (use code tags # in forum advanced editor):

cat /etc/fstab
lsblk -f
sudo parted -l

---

### Post by davy jones on 2020-02-21
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=38aa1627-3f51-469c-b46e-efac50913ae5 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=2C2A-F617  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda8 during installation
UUID=ac6616d9-90d8-48cf-ba7a-29b466e556bf /home           ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=96ff2bf7-5776-4d15-b5d8-c48d97652995 none            swap    sw              0       0
```

```
NAME    FSTYPE  LABEL      UUID                                 MOUNTPOINT
loop0   squashf                                                 /snap/gnome-calc
loop1   squashf                                                 /snap/gnome-syst
loop2   squashf                                                 /snap/core18/166
loop3   squashf                                                 /snap/gnome-logs
loop4   squashf                                                 /snap/gnome-char
loop5   squashf                                                 /snap/core/8268
loop6   squashf                                                 /snap/gnome-3-28
loop7   squashf                                                 /snap/gtk-common
sda                                                             
&#9500;&#9472;sda1  vfat    ESP        2C2A-F617                            /boot/efi
&#9500;&#9472;sda2  vfat    DIAGS      DA9A-507B                            
&#9500;&#9472;sda3                                                          
&#9500;&#9472;sda4  ntfs    WINRETOOLS 92C49BA0C49B855F                     
&#9500;&#9472;sda5  ntfs    OS         88329F64329F5652                     
&#9500;&#9472;sda6  ntfs               1E6E1FC96E1F991B                     
&#9500;&#9472;sda7  ext4               38aa1627-3f51-469c-b46e-efac50913ae5 /
&#9500;&#9472;sda8  ext4               ac6616d9-90d8-48cf-ba7a-29b466e556bf /home
&#9500;&#9472;sda9  swap               96ff2bf7-5776-4d15-b5d8-c48d97652995 [SWAP]
&#9500;&#9472;sda10                                                         
&#9500;&#9472;sda11 ntfs    Data       365315F110F42CE7                     
&#9492;&#9472;sda12 ntfs    PBR Image  EA32E81032E7E015                     
sr0                                   

```

```
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  525MB   524MB   fat32           EFI system partition          boot, esp
 2      525MB   567MB   41.9MB  fat32           Basic data partition          hidden
 3      567MB   701MB   134MB                   Microsoft reserved partition  msftres
 4      701MB   1226MB  524MB   ntfs            Basic data partition          hidden, diag
 5      1226MB  109GB   107GB   ntfs            Basic data partition          msftdata
 6      109GB   109GB   473MB   ntfs                                          hidden, diag
 7      109GB   131GB   21.5GB  ext4
 8      131GB   152GB   21.0GB  ext4                                          msftdata
 9      152GB   157GB   5000MB  linux-swap(v1)
10      157GB   157GB   1049kB
11      157GB   990GB   833GB   ntfs                                          msftdata
12      990GB   1000GB  10.3GB  ntfs            Microsoft recovery partition  hidden, diag

```

---

### Post by dragonfly41 on 2020-02-21
Try Thunar File Manager.  This will allow you to view hidden folders/files and to unmount/mount partitions.
There are others .. I like Krusader but it has a lot, a lot, of kde baggage. Nevertheless I use it.

---

### Post by oldfred on 2020-02-21
In Nautilus the side bar show or not is a setting in preferences.

Settings look normal, did you change user name(s) and then user 1000 is not the default in /home?

In Nautilus I like to turn on show user & permissions. Preferences, list  columns. I think find I did something to make a file as root when I should not have used sudo or downloaded something that defaulted to root. So then I can reset those.

---

### Post by davy jones on 2020-02-22
So most of this stuff sorted itself out because my new system took some time to read all the settings saved in my Home folder. I downloaded Nemo since I'd been using that for years over Nautilus. It's my default file manager but I'm only facing two issues with it.

1. It doesn't seem to have any options in Preferences to enable remembering recently used files.
2. Even though I've set it as my default file manager, neither one of my Web browsers (Firefox and Chrome) still treat Nautilus as my default FM while downloading any files. If I click on the "show in folder" option on either browser, it opens Nemo, but the actual download is always done using Nautilus on both browsers.

1 is not a deal-breaker but 2 is quite irritating. Is there a fix?

---

### Post by kurt18947 on 2020-02-23
You might try searching "use nemo as the default file manager + Ubuntu" or similar. I have Nemo as default and it took a couple terminal commands, nothing dramatic.

---

### Post by davy jones on 2020-02-25
It's already my default browser. But for a few things, other apps seem to use Nautilus. Web browsers use it when I'm choosing a destination for a download. VLC does it when I use the app to play a video.

---

