---
title: "Moving /home to another disk, which already contains some data, without erasing it"
date: 2022-02-07
forum: General Help
---

### Post by carlo8 on 2022-02-07
I have a remote server to which I have SSH access.
Currently, the /home folder is on the same disk as the root, and I was planning to move it to another SSD drive ("ssd1" in the picture), which is already connected and containing some data:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289982&stc=1[/IMG]
[IMG]https://ibb.co/Y8zRPQp[/IMG]

[IMG]https://ibb.co/Y8zRPQp[/IMG]


I checked the devices info with lsblk, and I got:
```

sda           8:0    0   1,8T  0 disk /media/sda1
nvme1n1     259:0    0   477G  0 disk 
&#9500;&#9472;nvme1n1p1 259:1    0   512M  0 part /boot/efi
&#9500;&#9472;nvme1n1p2 259:2    0     1K  0 part 
&#9492;&#9472;nvme1n1p5 259:3    0 476,4G  0 part /
nvme0n1     259:4    0   1,9T  0 disk 
&#9492;&#9472;nvme0n1p1 259:5    0   1,9T  0 part /media/ssd1

```


So, I was planning to do the following:

 
[LIST]
[*]Make a backup of the original home folder:
[/LIST]
```

sudo mv /home /home_orig    
sudo mkdir /home

```


[LIST]
[*]unmount the partition on the SSD disk from where it is now (/media) and mount it to the new /home folder:
[/LIST]
```

sudo umount /dev/nvme0n1p1
sudo mount /dev/nvme0n1p1 /home

```


[LIST]
[*]finally, make a backup of the original fstab file, and modify it this way:
[/LIST]
```


sudo cp /etc/fstab /etc/fstab_orig
sudo nano /etc/fstab
UUID=<>    /home    ext4    defaults   0  2

```

Is this the correct procedure? I checked [https://askubuntu.com/questions/21321/move-home-folder-to-second-drive](https://askubuntu.com/questions/21321/move-home-folder-to-second-drive) and [https://askubuntu.com/questions/5484/how-can-i-move-my-home-directory-to-another-partition-if-its-already-part-of-t](https://askubuntu.com/questions/5484/how-can-i-move-my-home-directory-to-another-partition-if-its-already-part-of-t), but the situation seems slightly different than mine...mostly, I'm worried about potentially deleting the data already present on ssd1.
Thanks!

---

### Post by grahammechanical on 2022-02-07
> mostly, I'm worried about potentially deleting the data already present on ssd1.

I suggest that you do two things first:

1) Backup your /home folder or at least the data that you do not want to lose.
2) Backup the data on ssd1 that you do not want to lose.

Store both backups in a safe area. Then experiment as much as you want. Even to the point of re-installing ubuntu using the something else option and setting /home as a partition on any drive you want.

Regards

---

### Post by oldfred on 2022-02-07
I may have posted similar in AskUbuntu.

To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) & 
[https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437](https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437)
[https://ubuntuforums.org/showthread.php?t=2343317](https://ubuntuforums.org/showthread.php?t=2343317)

An alternative is to use a data partition. You can move some or all data folders & just keep the mostly hidden user settings in /home inside / as they are small.
[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

