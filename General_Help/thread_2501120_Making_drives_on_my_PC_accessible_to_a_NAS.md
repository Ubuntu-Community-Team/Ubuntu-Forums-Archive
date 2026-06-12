---
title: "Making drives on my PC accessible to a NAS"
date: 2024-09-23
forum: General Help
---

### Post by makem2 on 2024-09-23
I have an Unraid based NAS using Nextcloud (Linux based), on my home network, along with one computer which is causing me headaches.

This is my main Ubuntu 24.04 machine and it has one nvme drive (nvme1n1p1) on which is a partition (Data) with a directory I specifically use as an Archive .

```
makem@makem-22:~$ lsblkNAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0         7:0    0     4K  1 loop /snap/bare/5
loop1         7:1    0  98.1M  1 loop /snap/bitwarden/120
loop2         7:2    0  96.5M  1 loop /snap/bitwarden/119
loop3         7:3    0   104M  1 loop /snap/core/16928
loop4         7:4    0 104.2M  1 loop /snap/core/17200
loop5         7:5    0  55.7M  1 loop /snap/core18/2823
loop6         7:6    0  55.7M  1 loop /snap/core18/2829
loop7         7:7    0  63.9M  1 loop /snap/core20/2318
loop8         7:8    0    64M  1 loop /snap/core20/2379
loop9         7:9    0  74.3M  1 loop /snap/core22/1586
loop10        7:10   0  74.3M  1 loop /snap/core22/1612
loop11        7:11   0  66.2M  1 loop /snap/core24/423
loop12        7:12   0  66.2M  1 loop /snap/core24/490
loop13        7:13   0 271.2M  1 loop /snap/firefox/4848
loop14        7:14   0 269.8M  1 loop /snap/firefox/4793
loop15        7:15   0 210.7M  1 loop /snap/gaming-graphics-core22/166
loop16        7:16   0 208.6M  1 loop /snap/gaming-graphics-core22/154
loop17        7:17   0 164.8M  1 loop /snap/gnome-3-28-1804/194
loop18        7:18   0 164.8M  1 loop /snap/gnome-3-28-1804/198
loop19        7:19   0 349.7M  1 loop /snap/gnome-3-38-2004/140
loop20        7:20   0 349.7M  1 loop /snap/gnome-3-38-2004/143
loop21        7:21   0 504.2M  1 loop /snap/gnome-42-2204/172
loop22        7:22   0 505.1M  1 loop /snap/gnome-42-2204/176
loop23        7:23   0  91.7M  1 loop /snap/gtk-common-themes/1535
loop24        7:24   0   3.1M  1 loop /snap/linux-steam-integration/12
loop25        7:25   0 212.1M  1 loop /snap/nextcloud-desktop-client/206
loop26        7:26   0 212.1M  1 loop /snap/nextcloud-desktop-client/208
loop27        7:27   0  12.9M  1 loop /snap/snap-store/1113
loop28        7:28   0  12.3M  1 loop /snap/snap-store/959
loop29        7:29   0  38.7M  1 loop /snap/snapd/21465
loop30        7:30   0  38.8M  1 loop /snap/snapd/21759
loop31        7:31   0   289M  1 loop /snap/solus-runtime-gaming/12
loop32        7:32   0 193.6M  1 loop /snap/steam/191
loop33        7:33   0 200.9M  1 loop /snap/steam/200
loop34        7:34   0 447.3M  1 loop /snap/telegram-desktop/6117
loop35        7:35   0 450.4M  1 loop /snap/telegram-desktop/6168
loop36        7:36   0 149.8M  1 loop /snap/thunderbird/509
loop37        7:37   0 149.8M  1 loop /snap/thunderbird/510
loop38        7:38   0    90M  1 loop /snap/ubpm/2
loop39        7:39   0  90.8M  1 loop /snap/ubpm/3
loop40        7:40   0  82.1M  1 loop /snap/whatsdesk/28
nvme1n1     259:0    0 476.9G  0 disk 
&#9500;&#9472;nvme1n1p1 259:1    0   260M  0 part /boot/efi
&#9500;&#9472;nvme1n1p2 259:2    0   128M  0 part 
&#9500;&#9472;nvme1n1p3 259:3    0   500M  0 part 
&#9500;&#9472;nvme1n1p4 259:4    0 181.9G  0 part /media/makem/Windows
&#9500;&#9472;nvme1n1p5 259:5    0  40.2G  0 part /var/snap/firefox/common/host-hunspell
&#9474;                                     /
&#9500;&#9472;nvme1n1p6 259:6    0  83.8G  0 part /home
&#9500;&#9472;nvme1n1p7 259:7    0 166.5G  0 part /media/makem/games-steam
&#9492;&#9472;nvme1n1p8 259:8    0   3.7G  0 part [SWAP]
nvme0n1     259:9    0   1.8T  0 disk 
&#9500;&#9472;nvme0n1p1 259:10   0    16M  0 part 
&#9492;&#9472;nvme0n1p2 259:11   0   1.8T  0 part /media/games
nvme2n1     259:12   0   1.8T  0 disk 
&#9492;&#9472;nvme2n1p1 259:13   0   1.8T  0 part /media/makem/Data
makem@makem-22:~$ 



```

I am able to sync my /home directory with the NAS and even our mobile phones but I cannot sync my Archive in this nvme1n1p1.

It has been suggested that the easiest way to access the Archive would be to put the nvme actually in the NAS as an Unassigned Device. Howerver, if I do that then I will be wasting > 1.0TB of the nvme which I currently use in my Ubuntu.

When I try to pick the /media/makem/Data directory using Nextcloud Add Folder Sync Connection I get a Permission denied error. It appears I must do something at the Ubuntu end to allow the connection.

```
makem@makem-22:/media/makem$ ls -latotal 32
drwxr-xr-x 6 root  root   4096 Sep 14 15:15 .
drwxr-xr-x 4 root  root   4096 Aug  9  2023 ..
drwxrwxrwx 1 root  root   4096 Sep 16 15:16 Data
drwxr-xr-x 6 makem makem  4096 Sep 15 20:43 games-steam
drwxr-xr-x 2 root  root   4096 Jan 29  2024 temp
drwxrwxrwx 1 root  root  12288 Sep 15 18:08 Windows
makem@makem-22:/media/makem$


```

Can I ask for help achieving my aim of syncing the Archive with the NAS please?

---

### Post by oldfred on 2024-09-23
Please redo your lsblk.
All the snaps(loop) are not drives and provide no info.
And format & details would help. Did you label your archive as archive, so we know which partition that is?
lsblk -e 7 -o name,fstype,size,fsused,label,UUID,mountpoint

The -e 7 excludes the loops in the lsblk output.

I like to label all partitions, especially those I do not regularly mount with fstab.

---

### Post by makem2 on 2024-09-23
> **oldfred said:**
> Please redo your lsblk.
All the snaps(loop) are not drives and provide no info.
And format & details would help. Did you label your archive as archive, so we know which partition that is?
lsblk -e 7 -o name,fstype,size,fsused,label,UUID,mountpoint

The -e 7 excludes the loops in the lsblk output.

I like to label all partitions, especially those I do not regularly mount with fstab.

Thank you for your response.

```
makem@makem-22:~$ lsblk -e 7 -o name,fstype,size,fsused,label,UUID,mountpointNAME        FSTYPE   SIZE FSUSED LABEL       UUID                                 MOUNTPOINT
nvme1n1            476.9G                                                         
&#9500;&#9472;nvme1n1p1 vfat     260M  33.4M SYSTEM      40DB-4F92                            /boot/efi
&#9500;&#9472;nvme1n1p2          128M                                                         
&#9500;&#9472;nvme1n1p3 ntfs     500M        Recovery    F026DBCE26DB9446                     
&#9500;&#9472;nvme1n1p4 ntfs   181.9G   115G Windows     CE6CDDE46CDDC77D                     /media/makem/Windows
&#9500;&#9472;nvme1n1p5 ext4    40.2G  22.8G             3388ecd3-9ab1-44d8-90cf-88b70af20f14 /
&#9500;&#9472;nvme1n1p6 ext4    83.8G  53.8G             6e3e25f1-7705-4a68-934a-e5b1676c58b2 /home
&#9500;&#9472;nvme1n1p7 ext4   166.5G  41.1G games-steam 8d58ff3d-fa93-4b35-a343-34883602c151 /media/makem/games-steam
&#9492;&#9472;nvme1n1p8 swap     3.7G                    4ede3f10-e290-4fe4-970a-27537f3a0499 [SWAP]
nvme0n1              1.8T                                                         
&#9500;&#9472;nvme0n1p1           16M                                                         
&#9492;&#9472;nvme0n1p2 ntfs     1.8T 795.2G games       E07CD0EB7CD0BD8A                     /media/games
nvme2n1              1.8T                                                         
&#9492;&#9472;nvme2n1p1 ntfs     1.8T 456.2G Data        02599539052AB338                     /media/makem/Data
makem@makem-22:~$ 



```

The Archive is a directory within the drive labelled Data.

I have just been to windows and with the help of my son made an SMB share of the directory Archive. I returned to linux and now find the the Archive is no longer accessible as it has an error 'broken link'. It appears I may have lost all of the data.

Windows is uploading the Archive to the NAS so I assume the directory is locked hence the broken link error. There is some 159gb of data so it will take a while.

I still need the Ubuntu connection because I rarely use Windows so please bear with me. The Archive include information such as '[COLOR=#000000]*The -e 7 excludes the loops in the lsblk output'  *[/COLOR]as and when I come across it.

---

### Post by oldfred on 2024-09-23
You cannot backup Linux data to NTFS as it does not support Linux permissions & ownership. If just data, not system files, you can restore default permissions & ownership when you restore data.

Also Microsoft turns on its fast startup setting with updates which sets hibernation flag. Then the Linux NTFS driver cannot fully or default mount all NTFS partitions.

---

### Post by makem2 on 2024-09-24
> **oldfred said:**
> You cannot backup Linux data to NTFS as it does not support Linux permissions & ownership. If just data, not system files, you can restore default permissions & ownership when you restore data.

Also Microsoft turns on its fast startup setting with updates which sets hibernation flag. Then the Linux NTFS driver cannot fully or default mount all NTFS partitions.

Would please explain what that means in my situation.

99% of the time I use Linux only, however when I do need to use Windows it is handy to be able to on very rare occasions, to be able to access the Archive. These times are rare in the 1% of the time I am using Windows.

The Archive was generated in Linux, mainly used in Linux and just needs very occasional Windows access.

Do you have any suggestions on how I should proceed?

---

### Post by ActionParsnip on 2024-09-24
NTFS cannot store Linux file permissions. It has it's own structure and so on. When you restore data, the access it once had may not be restored and the files will be put in place using default access. If this is casual user data (Pictures, audio etc) then this is less problematic but you may find that you need to chown/chmod when you use the data once copied to a Linux file system

---

### Post by makem2 on 2024-09-24
> **ActionParsnip said:**
> NTFS cannot store Linux file permissions. It has it's own structure and so on. When you restore data, the access it once had may not be restored and the files will be put in place using default access. If this is casual user data (Pictures, audio etc) then this is less problematic but you may find that you need to chown/chmod when you use the data once copied to a Linux file system

Are you saying that 'copying' the data to a Linux based NAS means I may have to chown/chmod when I use the data? That cannot be true surely as more Windows users use Nextcloud on Unraid than do Linux users from my short experience.

The data was and still is, initiated solely in Linux OS on an NTFS file system to enable Windows to access the data. The data is not casual pictures or audio etc. nor is it system files. Some data may have been added from Windows over the years but as said it has been used mainly from Linux and as far as I have been aware as a user there not been any problem in access in either direction.

For me, having to have Windows is a necessary pain.

---

### Post by ActionParsnip on 2024-09-24
> **makem2 said:**
> Are you saying that 'copying' the data to a Linux based NAS means I may have to chown/chmod when I use the data? That cannot be true surely as more Windows users use Nextcloud on Unraid than do Linux users from my short experience.

The data was and still is, initiated solely in Linux OS on an NTFS file system to enable Windows to access the data. The data is not casual pictures or audio etc. Some data may have been added from Windows over the years but as said it has been used mainly from Linux and as far as I have been aware as a user there not been any problem in access in either direction.

For me, having to have Windows is a necessary pain.

You will get the access given by the NAS when you mount the NAS. You'll set the access at mount time using mount options.

---

### Post by makem2 on 2024-09-24
> **ActionParsnip said:**
> You will get the access given by the NAS when you mount the NAS. You'll set the access at mount time using mount options.

I think that what you say is what I asked when I started this thread. Would you please explain how to 'mount the NAS'?

Will this fix the broken links to data in Linux?

---

### Post by makem2 on 2024-09-24
Decided Nextcloud is not for me after finding that it had not fixed the uploading problem in 4 years! 

I will look at an alternative which may be Folder Sync Desktop.

I will keep Unraid because even if this alternative to Nextcloud turns out not suitable there will be a way!

I thank you both for your input and bow out.

Edit: Looks like Syncthing available from github or ubuntu repos. is the one for me.

---

### Post by oldfred on 2024-09-24
I do not use NAS nor nextcloud.
I do backup with rsync to multiple drives, flash drives, external SSDs & some data to DVD, so I have data in multiple places.

---

### Post by makem2 on 2024-09-24
I have since been able to reinstate the Archive link by removing the Nextcloud sync.

I now have the correct output:

```

makem@makem-22:/media/makem/Data$ ls -lhtotal 24K
drwxrwxrwx 1 root root    0 Jul 14  2023 '$RECYCLE.BIN'
drwxrwxrwx 1 root root 4.0K Sep 24 18:23  Archive
drwxrwxrwx 1 root root    0 Feb  5  2024 'backup of hdd2'
drwxrwxrwx 1 root root 4.0K Sep 23 00:07  downloads
-rwxrwxrwx 2 root root 8.0K Sep 24 11:41  DumpStack.log.tmp
drwxrwxrwx 1 root root 4.0K Sep 24 17:55  nextcloud
drwxrwxrwx 1 root root    0 Aug  4  2023  SteamLibrary
drwxrwxrwx 1 root root 4.0K Sep 24 18:23 'System Volume Information'
makem@makem-22:/media/makem/Data$ 



```

I have stripped out the unnecessary two lines using ls -lh 


For ease of anyone who might deign to assist I put the drive layout below again:

```

makem@makem-22:~$ lsblk -e 7 -o name,fstype,size,fsused,label,UUID,mountpointNAME        FSTYPE   SIZE FSUSED LABEL       UUID                                 MOUNTPOINT
nvme2n1            476.9G                                                         
&#9500;&#9472;nvme2n1p1 vfat     260M  33.4M SYSTEM      40DB-4F92                            /boot/efi
&#9500;&#9472;nvme2n1p2          128M                                                         
&#9500;&#9472;nvme2n1p3 ntfs     500M        Recovery    F026DBCE26DB9446                     
&#9500;&#9472;nvme2n1p4 ntfs   181.9G 125.9G Windows     CE6CDDE46CDDC77D                     /media/makem/Windows
&#9500;&#9472;nvme2n1p5 ext4    40.2G  22.8G             3388ecd3-9ab1-44d8-90cf-88b70af20f14 /
&#9500;&#9472;nvme2n1p6 ext4    83.8G    54G             6e3e25f1-7705-4a68-934a-e5b1676c58b2 /home
&#9500;&#9472;nvme2n1p7 ext4   166.5G  41.1G games-steam 8d58ff3d-fa93-4b35-a343-34883602c151 /media/makem/games-steam
&#9492;&#9472;nvme2n1p8 swap     3.7G                    4ede3f10-e290-4fe4-970a-27537f3a0499 [SWAP]
nvme0n1              1.8T                                                         
&#9500;&#9472;nvme0n1p1           16M                                                         
&#9492;&#9472;nvme0n1p2 ntfs     1.8T 795.2G games       E07CD0EB7CD0BD8A                     /media/games
nvme1n1              1.8T                                                         
&#9492;&#9472;nvme1n1p1 ntfs     1.8T 439.2G Data        02599539052AB338                     /media/makem/Data
makem@makem-22:~$ 



```

'Archive' is a directory in Data: /media/makem/Data/Archive/

---

### Post by makem2 on 2024-09-26
> **ActionParsnip said:**
> You will get the access given by the NAS when you mount the NAS. You'll set the access at mount time using mount options.

Would you be able to tell me the syntax to mount the NAS please?

---

