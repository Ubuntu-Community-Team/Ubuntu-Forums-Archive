---
title: "Cannot move file to Rubbish Bin on other partition"
date: 2013-08-16
forum: General Help
---

### Post by woodyg on 2013-08-16
Hi,
having got myself a bigger hdd for the data in my home partition, I decided to split it into two partitions. One is mounted as a regular home partition. The other one, media/secondary, mounts ok if my fstab file contain:

```
UUID=7dbc5269-fe2d-4528-b250-5e81ac075542   /home    ext4          defaults       0       2
UUID=a1e786f8-9f33-469c-a60f-e72161d8183d   /media/secondary    ext4          defaults       0       2
```

but then there is no rubbish bin in the partition  media/secondary and I get the message "[FONT=courier new]*Cannot move file to the Rubbish Bin, do you want to delete it immediately?*[/FONT]" when trying to delete a file. Googling a bit suggested that it was an ownership issue. I therefore modified fstab to:

```
UUID=7dbc5269-fe2d-4528-b250-5e81ac075542   /home    ext4          defaults       0       2
UUID=a1e786f8-9f33-469c-a60f-e72161d8183d   /media/secondary    ext4          defaults,uid=1000,gid=46       0       2
```

but then I get the error message

```
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

when trying to mount the partition (sudo mount -a). What am I doing wrong?

---

### Post by woodyg on 2013-08-17
I managed to solve my problem by manually creating a .Trash-1000 folder and chmod it 777. :p

---

