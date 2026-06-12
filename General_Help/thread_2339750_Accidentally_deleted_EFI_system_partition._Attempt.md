---
title: "Accidentally deleted EFI system partition. Attempting to recover. Help!"
date: 2016-10-12
forum: General Help
---

### Post by dickvicious on 2016-10-12
Hi,

First time posting to the forums, but long time ubuntu user. Yesterday I accidentally deleted my EFI system partition (sda1) while trying to format an SD card. Anyways, I immediately ran testdisk and tried to recover the deleted partition. It seemed to have worked correctly, but after a reboot I was not able to get back into the system. I either got a "Invalid Partition Table!" message or was launched into grub (Im not certain which, but I think it was grub).

I then ran testdisk again to see if that would do anything and then I ran GParted and noticed the recovered EFI partition did not have the ESP flag so I set it and rebooted. I think this actually made things worse since I don&#8217;t remember being able to get into grub any more after this point. 

I then tried to run the Ubuntu Boot Repair tool (a few times with different options) without luck. Now I am getting the "Invalid Partition Table!" message and wanted to ask for help before going any further and possibly screwing things up worse.

The following are the logs from the different tools used in order.
Testdisk - [http://paste.ubuntu.com/23313358/](http://paste.ubuntu.com/23313358/)
Testdisk - [http://paste.ubuntu.com/23313361/](http://paste.ubuntu.com/23313361/)
BootRepair (ran as regular user) - [http://paste.ubuntu.com/23313364/](http://paste.ubuntu.com/23313364/)
BootRepair - [http://paste.ubuntu.com/23313367/](http://paste.ubuntu.com/23313367/)
BootRepair - [http://paste.ubuntu.com/23311001/](http://paste.ubuntu.com/23311001/)
BootRepair - [http://paste.ubuntu.com/23311094/](http://paste.ubuntu.com/23311094/)

Any help would be appreciated. Thanks!

---

### Post by oldfred on 2016-10-12
The ESP - efi system partition looks normal. Typical boot files are shown.

I do not know LVM nor full drive encryption.
But errors now look like something related to the LVM.
You may need to run fsck on the partitions inside the LVM, which requires mounting the LVM.

This is on resize, but first part is on mounting LVM, and then mentions you at that point can do repairs.
       How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
sudo apt-get update && sudo apt-get install lvm2 cryptsetup 

I just copied these commands, not sure exactly correct.

 df -h
sudo blkid
sudo fdisk -l
sudo pvdisplay
sudo lvdisplay
mount
sudo vgscan --mknodes
sudo vgchange -ay
sudo e2fsck -f /dev/ubuntu-vg/root

---

### Post by dickvicious on 2016-10-12
Thanks for the reply!

I'm able to get into the filesystem while using an Ubuntu Live CD. Im currently using it to backup my files in case I need to just reinstall after all. So since I can mount the filesystem and use it normally, it wouldnt be a corruption issue right? What error did you see that lead you to that?

---

### Post by oldfred on 2016-10-12
A lot of errors on trying to update or install grub.

It could just be a fsck on /boot partition sda2, which is not inside the LVM.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda2 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda2
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda2

Or a dosfsck on ESP.
      
 sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sda1
man dosfsck

---

### Post by dickvicious on 2016-10-12
Ok, ran those. I cant reboot yet as im still backing up, but seems like no errors were found?

```
sudo e2fsck -C0 -p -f -v /dev/sda2
                                                                               
         572 inodes used (0.46%, out of 124928)
         118 non-contiguous files (20.6%)
           2 non-contiguous directories (0.3%)
             # of inodes with ind/dind/tind blocks: 118/15/0
      180490 blocks used (36.12%, out of 499712)
           0 bad blocks
           0 large files

         552 regular files
          11 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
         563 files
```

```
sudo fsck.vfat -V /dev/sda1
fsck.fat 3.0.28 (2015-05-16)
Starting check/repair pass.
Starting verification pass.
/dev/sda1: 32 files, 2934/130811 clusters
```

```
sudo fsck.vfat -t -a /dev/sda1
fsck.fat 3.0.28 (2015-05-16)
/dev/sda1: 32 files, 2934/130811 clusters
```

---

### Post by oldfred on 2016-10-12
Not sure then if Boot-Repair did not correctly mount /boot & your root inside the LVM which is required to update/install grub.

---

