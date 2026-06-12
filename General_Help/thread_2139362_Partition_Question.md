---
title: "Partition Question"
date: 2013-04-26
forum: General Help
---

### Post by Nick8 on 2013-04-26
Hello, I hope you can help me with this quick problem I've been having.

I've been trying to create a separate partition on /dev/sda, to store various files. I don't need it to auto-mount; I'm happy to mount it manually when I need it.

I can do all this fine, but for some reason, if I format it as ext2 or ext3, I can read it, but I cannot write to it unless I'm root. Also a 'lost+found' folder appears in it. However, if I format it as NTFS, I can write to it normally (without needing to be root), and there's no lost+found folder created in it.

Please can someone explain why this is, and how to make it so that I can write to the ext2 or ext3 partition without being root?

I've tried creating the partition using cfdisk + mkntfs, and KDE Partition Manager, and the result is the same for both.

I have a simple partition structure, on a 160GB HDD:

/dev/sda1   /  (Linux Mint) (40GB)
/dev/sda2   swap (1GB)
/dev/sda3   / (Kubuntu) (20GB)
/dev/sda4   partition in question (~100GB)

Thanks for your help.

---

### Post by CatKiller on 2013-04-26
Lost+Found contains the recovered files from running fsck. You can't run fsck on an NTFS filesystem, so no Lost+Found.

You need to use root because of the Unix permissions system. NTFS can't handle Unix permissions, so you don't need to be root.

Permissions for who can use a particular ext filesystem are set at mount time, along with permissions on the mount point and the permissions on the files themselves. There is no inherent reason why you can't mount an ext filesystem and have write permissions for whomever you choose.

---

### Post by Nick8 on 2013-04-26
Thank you for your quick reply.

How can I set it so that every time I manually mount it, I will be able to write to it without being root? I don't really want to add it to fstab, causing it to mount every time I log in.

---

### Post by CatKiller on 2013-04-26
I'm not near my computer at the moment, so I can't check for you, but ** man mount** has all the mount options listed. Also you can add a partition to fstab without it necessarily automatically mounting; I believe it's the ** noauto** option, but check ** man fstab**. That way you don't have to enter options every time.

Otherwise, there's probably a handy guide somewhere.

It's possible you just need to change ownership of the mount point.

EDIT: here's [one]("http://www.psychocats.net/ubuntu/mountlinux"), and [another]("https://help.ubuntu.com/community/AutomaticallyMountPartitions"), from a quick search. It's a long time since I've done it, so I'm rusty on the details.

---

### Post by oldfred on 2013-04-26
Be sure not to run any of the ownership & permission commands on anything other than your data partition.

 #if not known to list partitions, change sda4 to your data partition or create multiples with different mount points
# is comment, do not type
sudo fdisk -l
sudo mkdir /mnt/data
sudo mount /dev/sda4 /mnt/data
#where sda4 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown $USER:$USER /mnt/data

---

