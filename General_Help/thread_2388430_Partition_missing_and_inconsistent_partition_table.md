---
title: "Partition missing and inconsistent partition table"
date: 2018-04-02
forum: General Help
---

### Post by fra87 on 2018-04-02
[COLOR=#111111][FONT=Ubuntu]Hi Everyone,

I recently installed Ubuntu 16.04 LTS on my wife's laptop. Originally there was Win 7 on it and I simply wiped out everything and used the whole disk for Ubuntu. I followed the following guide to create partitions: [How to use manual partitioning during installation?]("https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa")[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After I filled the /home/*user*/... directory with some personal files I received the warning that /root was running out of space.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I checked the space available on the partitions and /home disappeared while /boot dramatically increased (During the installation, I assigned 500 MB to /boot and 230 GB to /home)
[/FONT][/COLOR]
Filesystem      Size  Used Avail Use% Mounted on
udev            1,9G     0  1,9G   0% /dev
tmpfs           385M  6,2M  379M   2% /run
/dev/sda5        19G  7,6G   11G  43% /
tmpfs           1,9G   13M  1,9G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           1,9G     0  1,9G   0% /sys/fs/cgroup
/dev/sda8       9,1G   22M  8,6G   1% /tmp
/dev/sda7       9,1G  983M  7,7G  12% /var
/dev/sda6       230G  250M  218G   1% /boot
/dev/sda9       185G  9,9G  166G   6% /opt
tmpfs           385M   60K  385M   1% /run/user/1000


[COLOR=#111111][FONT=Ubuntu]What happened here? Or maybe.. what did I do wrong here? Thank you for your time.[/FONT][/COLOR]

---

### Post by yancek on 2018-04-02
I'm not sure why you created all those partitions as they certainly are not needed.  Since you are not using LVM, there is really no need for a separate boot partition.  Simplify things for yourself and just create a / (root filesystem) partition and /home partition.  Having a /var partition is only usually practical if you are running a server as that is the default location for those files.

I don't know why you are getting that message as your / partition is only 43% used.  Is it the / (root) filesystem or the /root user directory?  You should not need to be putting anything in the /root user directory.

Is this an EFI machine or the older Legacy?  I notice you have no primary partitions which is a bit odd.  Can you boot the Ubuntu install medium and run the following from a terminal, post the output here:

```
sudo parted -l
```

Lower case Letter L in the command.

---

### Post by Dennis N on 2018-04-02
The only way I can see that adding files to /home/user would decrease available space in root partition (/) would be when your home directory is on the root partition - meaning that you did not create a separate home partition. 

Your boot partition is going to increase over time as you get updated kernels, and if you don't remove the old ones, that partition will soon run out of space even though you disk has available space elsewhere. You say you assigned 230 GB to home partition, but it looks like you assigned that 230GB to /boot instead. If you need separate boot (you might be using encryption?) 2GB should be enough, each set of kernel packages is about 300 MB. Most people retain only 2 or 3 kernels.

As yancek said, putting var, opt and tmp on their own partitions is not needed. Your guide says separate partition for these are optional.  It seems like an inefficient use of space.

---

### Post by fra87 on 2018-04-03
Thank you for your reply.
I have now 43% because as soon as I received the warning I moved the files from /home and I checked the partitions.
I do not have proof buy I am pretty sure I have created the /home partition. I followed step by step the guide I linked in my original question.
This is the output of sudo parted -l :

Model: ATA ST9500325AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  8193MB  8191MB  primary   linux-swap(v1)  boot
 2      8194MB  500GB   492GB   extended
 5      8194MB  28.7GB  20.5GB  logical   ext4
 6      28.7GB  279GB   250GB   logical   ext4
 7      279GB   289GB   9999MB  logical   ext4
 8      289GB   299GB   9999MB  logical   ext4
 9      299GB   500GB   201GB   logical   ext4

---

### Post by fra87 on 2018-04-03
> **Dennis N said:**
> The only way I can see that adding files to /home/user would decrease available space in root partition (/) would be when your home directory is on the root partition - meaning that you did not create a separate home partition. 

Your boot partition is going to increase over time as you get updated kernels, and if you don't remove the old ones, that partition will soon run out of space even though you disk has available space elsewhere. You say you assigned 230 GB to home partition, but it looks like you assigned that 230GB to /boot instead. If you need separate boot (you might be using encryption?) 2GB should be enough, each set of kernel packages is about 300 MB. Most people retain only 2 or 3 kernels.

As yancek said, putting var, opt and tmp on their own partitions is not needed. Your guide says separate partition for these are optional.  It seems like an inefficient use of space.

Thank you for your reply.
Trust me, I did it. I am noob but I really followed step by step the guide. After the an update the partitions were all messed up.
Anyway I think I am going to reinstall it and I let ubuntu do the partitions.

---

