---
title: "2nd Drive Location in File Explorer."
date: 2021-12-18
forum: General Help
---

### Post by tedeye on 2021-12-18
Hello Guys and Gals - 

I run 21.04 on my laptop, which has two drives - a NVMe and a standard 2.5" SATA.  I use the NVMe for the OS and keep my media files on the 2.5" drive.  When I open the file explorer, the 2.5" drive is listed under other, so I have to click on it to gain access to it.  Is there some way I can get it to show up along with the standard folders like Downloads, Pictures, Documents, etc.?  Thanks for any help.

---

### Post by oldfred on 2021-12-18
I like to label partitions that I only use occassionally.

But if an internal drive you should add an entry to fstab.
You have to create a mount point, give yourself ownership & permissions and then add entry into fstab.
Generally better to copy & paste an example and adjust for your UUID & mount point.

To see your UUIDs.
lsblk -e 7 -o name,fstype,size,fsused,label,UUID,mountpoint
Some examples:
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
[https://wiki.archlinux.org/index.php/fstab](https://wiki.archlinux.org/index.php/fstab)

I now use labels fro some mounts & use noatime for SSD partitions & relatime for HDD partitions. 
See these for more details:
man mount
man fstab

---

### Post by Qbert on 2021-12-24
Thanks Fred.  I realized when I opened the drive it creates its own icon on the side panel, so I just added that to the favorites and it works for me.  Thanks again.

---

### Post by ActionParsnip on 2021-12-24
If you run:
```

sudo blkid

```
You can see its ID. You can then make a folder to mount the file system to each bootup by adding a file to /etc/fstab
If you make a folder using the below:
```

sudo mkdir /data

```
You can then run:
```

sudo cp /etc/fstab /etc/fstab-2021-12-24
sudo vi /etc/fstab

```
(Use any editor you prefer. I just like vi).

Then add the below:
```

UUID=5caaee32-c3d3-429e-bad7-2898cf923805  /data  ext4  defaults 0 0

```

Your UUID will be different so don't just copy and paste the above and expect it to work. Change it for your UUID of the partition you are working with. Your system will now mount the extra storage to /data each boot. To make access quicker, you can run:
```

ln -s /data /home/$USER/Data

```
(This one you can run as is)

Then you will see a new folder in your user's home to get access to the files. You can even use the symlink (Which is what the command created) in the terminal as if it was a normal directory.

---

