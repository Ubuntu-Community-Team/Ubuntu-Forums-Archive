---
title: "can't get encrypted external drive to mount on system start-up"
date: 2024-07-20
forum: General Help
---

### Post by Old Jimma on 2024-07-20
Hello Forum People:

I did a fresh reinstall of 22.04 and enabled full disc encryption during the reinstall: [HTML]https://linuxconfig.org/ubuntu-22-04-enable-full-disk-encryption[/HTML]

After that, I used the disk utility:
[LIST]
[*]first, to mount an external drive, 
[*]and then to encrypt it.
[*]
[/LIST]

Here is what the "mount" entry in my /etc/fstab looks like:

> 
UUID=a4833c03-860e-4a45-915d-d4802a7ba9ca /mnt/NVME2 auto nosuid,nodev,nofail,x-gvfs-name=NVME2 0 0


Then, I rebooted.

Fter the reboot, I used the following code to backup files to the mounted drive:

> 
rdiff-backup /home/HOMEDRIVENAME/ /mnt/NVME2/


The opperation seemed to complete nicely.

Then, I used the Disk Usage Analyzer and saw that the amount of hard disk I was using had **doubled**!

[IMG]/home/camillesmith/Documents/Computer/02_All_GAZELLE_STUFF/Encrypting Attached Drives/2024-07-20_06-43.png[/IMG]


This suggested that my effort to mount the external drive had failed, and that rdiff-backup had written the backup to the mount point (/mnt/NVME2) of the home drive rather than to the external drive.

I tried several ways of fixing /etc/fstab, including re-writting it 
[LIST]
[*]using the disk utility ([https://ubuntuhandbook.org/index.php/2023/05/auto-mount-external-disk-partitions/](https://ubuntuhandbook.org/index.php/2023/05/auto-mount-external-disk-partitions/)),
[*]and [HTML]https://askubuntu.com/questions/1378363/how-do-i-mount-external-drive-to-the-same-mountpoint-every-time[HTML]
[*]
[/LIST]

Nothing I tried worked.

Could somebody please steer me into some knowledge so that I can get that external drive mounted on start up on a consistent basis, please?

Thanks,
Old

---

### Post by Old Jimma on 2024-07-20
Hello People:

Perhaps my problem has something to do with my not knowing much about /etc/crypttab [HTML]https://linuxconfig.org/introduction-to-crypttab-with-examples[/HTML]

I'm going to learn ... right now!!!

---

