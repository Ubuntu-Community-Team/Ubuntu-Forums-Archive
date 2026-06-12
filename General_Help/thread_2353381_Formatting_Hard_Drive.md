---
title: "Formatting Hard Drive"
date: 2017-02-21
forum: General Help
---

### Post by daniell59 on 2017-02-21
I just added another hard drive to my computer. It will be used for storage. What file system would be best to format it to? Any other suggestions about formatting will be appreciated.

Thanks

---

### Post by daporkchop on 2017-02-21
ext4 if you're using it only on Ubuntu/Linux, if not then NTFS for windows compatibilty. You COULD do FAT32, but then you'd lose the ability to store big files-

---

### Post by daniell59 on 2017-02-21
> **daporkchop said:**
> ext4 if you're using it only on Ubuntu/Linux, if not then NTFS for windows compatibilty. You COULD do FAT32, but then you'd lose the ability to store big files-

Thanks, it will only be used on Linux.

---

### Post by ajgreeny on 2017-02-21
Yes, format the partition on the disk to ext4.

Find it's UUID after formatting using command ```
sudo blkid -c /dev/null
``` then add a line for it to /etc/fstab so it is mounted at boot,
```
UUID=66E53AEC54455DB2 /mnt/data ext4 defaults 0 1
``` using your own UUID of course.
Now create the folder /mnt/data with command ```
sudo mkdir /mnt/data
``` and to check all is well, run command ```
sudo mount -a
``` No output from that command means the disk is mounted and available, and that there was no problem with your fstab file.

To use the partition on that disk as user you will need to change ownership of the mountpoint with command ```
sudo chown -R $USER:$USER /mnt/data
``` and possinly also ```
chmod -R 755 /mnt/data
``` This command does not need sudo as you already own the mountpoint but it will give you, as user, full read/write permissions and all others read only.

---

### Post by daniell59 on 2017-02-21
> **ajgreeny said:**
> Yes, format the partition on the disk to ext4.

Find it's UUID after formatting using command ```
sudo blkid -c /dev/null
``` then add a line for it to /etc/fstab so it is mounted at boot,
```
UUID=66E53AEC54455DB2 /mnt/data ext4 defaults 0 1
``` using your own UUID of course.
Now create the folder /mnt/data with command ```
sudo mkdir /mnt/data
``` and to check all is well, run command ```
sudo mount -a
``` No output from that command means the disk is mounted and available, and that there was no problem with your fstab file.

To use the partition on that disk as user you will need to change ownership of the mountpoint with command ```
sudo chown -R $USER:$USER /mnt/data
``` and possinly also ```
chmod -R 755 /mnt/data
``` This command does not need sudo as you already own the mountpoint but it will give you, as user, full read/write permissions and all others read only.

Please excuse my ignorance. I am ashamed to say, I don't know what UUID is.

Thanks for your informative reply.

---

### Post by howefield on 2017-02-21
> **daniell59 said:**
> Please excuse my ignorance. I am ashamed to say, I don't know what UUID is.

It is the **U**niversally **u**nique **id**entifier which each disk/partition on your system can be identified by.

To get it, open a terminal and use the command..

```
ls -al /dev/disk/by-uuid
```

output will be something like..

```
drwxr-xr-x 2 root root 100 Feb 21 11:58 .
drwxr-xr-x 6 root root 120 Feb 21 11:58 ..
lrwxrwxrwx 1 root root  10 Feb 21 11:58 **33f4f7ae-ac99-4251-8f46-d43e7412b9df** -> ../../sda2
lrwxrwxrwx 1 root root  10 Feb 21 11:58 **93c9af6e-36b9-44e9-a36b-f912a7434dce** -> ../../sda1
lrwxrwxrwx 1 root root  10 Feb 21 11:58 **b96aebfe-2824-4bc4-83a9-84e8ffec97d5** -> ../../sda4
```

UUIDs in bold.

Alternatively use..

```
sudo blkid
```

Which would also detail the labels of the disk if you have labelled them.

---

### Post by daniell59 on 2017-02-21
Correct me if I am wrong, but wont Gparted show the UUID?

---

### Post by howefield on 2017-02-21
> **daniell59 said:**
> Correct me if I am wrong, but wont Gparted show the UUID?

Indeed, gparted will offer you the UUID from the disk/partition properties which you'll be able to highlight and copy to the clipboard.

---

