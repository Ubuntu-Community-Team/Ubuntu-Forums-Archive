---
title: "System to Larger Hard Drive"
date: 2007-09-02
forum: General Help
---

### Post by taekwondodogoof on 2007-09-02
Hi,
   I've looked around the forums and seen similar questions, but mine's a little different so I thought there might be a different (and easier) answer.
         I have 2 hard-drives, an 80-gig with Ubuntu, and a 150 gig with Windows and the MBR. I'm upgrading the Ubuntu 80-gig to around a 400gig because I've started using it much more than Windows lately. My question is, how can I easily transfer my current hard-drive over to the new one and be able to boot? I'm only changing the Ubuntu drive, not the Windows drive.
            THanks for the help!!! :KS

---

### Post by logos34 on 2007-09-02
Connect the new drive.  Use Gparted from a live utility cd ([Parted Magic]("http://partedmagic.com/"), for instance) to create the new root partition (plus any others) and copy the image to it using [Partimage]("http://www.partimage.org/Partimage-manual_Usage").

OR use the ['dd' command]("http://www.brunolinux.com/02-The_Terminal/The_dd_command.html").  For example:

**sudo dd if=/dev/sda1 of=/dev/sdb1 bs=4096 conv=notrunc,noerror**

(where sda1 is the linux root partition on the old drive, and sdb1 is the target partition on the new drive.)

or simply copy the whole drive:
[B]
sudo dd if=/dev/sda of=/dev/sdb[/B]

See dd man pages for further info.

[Reinstall grub to to the mbr of the new drive]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub").

---

### Post by rickyrockrat on 2007-09-05
Here's the steps:
First, put your new drive in the system and boot up in ubuntu
partition and format the new drive as you like:
sudo fdisk /dev/sda
sudo mke2fs -m 1 -j /dev/sda1
sudo mke2fs -m 1 -j /dev/sda2 
sudo mkswap /dev/sda3
Some say having the swap at the end of the drive is slower, but I suppose that would depend on what the end of the drive is to the drive :)

I use a 512M partition at the beginning of the disk because of some legacy BIOSes that couldn't boot past limited number of sectors. Modern BIOSes don't seem to care.
This 512 contains my linux kernels and grub:
/dev/sda1 boot
/dev/sda2 root
/dev/sda3 swap, type 82
if you have a boot partition, mount it somewhere and copy your current /boot directory there. I create directories in /mnt with the device name:
sudo mkdir /mnt/sda1
sudo mkdir /mnt/sda2
sudo mount /dev/sda1 /mnt/sda1
sudo cp -a /boot/* /mnt/sda1
Get your new UUIDs:
sudo vol_id /dev/sda1
sudo vol_id /dev/sda2
Edit your grub/menu.list and replace your UUID=xxxx numbers with what you got from sda2 (your linux root).  
sudo vi /mnt/sda1/grub/menu.lst
sudo umount /mnt/sda1
mount your new root partition
sudo mount /mount /dev/sda2 /mnt/sda2
Now copy files:
cd /
sudo cp -a bin boot cdrom dev etc home ini* li* opt root sbin tmp usr var /mnt/sda2
---- Wait a LONG time ---
cd /mnt/sda2
sudo mkdir proc srv sys
Now mark the partition (if you have multiple drives)
sudo echo "new sda2" >part
Edit your fstab (grab UUIDs)
sudo vol_id /dev/sda3
sudo vi /mnt/sda2/etc/fstab
replace your old UUIDs with new ones (from vol_id)
make sure to save (vi = :wq)
Now install grub -next lines are from grub command line:

sudo grub
find /part
when you find part, you know the which drive it is...my sda was hd1, so:
root (hd1,0)
setup (hd1)
quit

I hope I havent missed anything!  unmount your new drive
sudo umount /dev/sda2
format your swap
sudo mkwap /dev/sda3
restart PC, and select new drive from boot menu.  If you remove a drive from the system, don't panic!  Grub will re-order the drives, so when grub complains that the drive can't be found, drop into the grub command line (c) and run the find command again:
find /part
then edit the line that calls out your root (grub root, NOT linux root, very confusing) and replace the hdx,0 with whatever grub found, then boot.

Then make sure you edit the meun.lst file so you don't have to do it again!
sudo vi /boot/grub/menu.lst

Cheers!

---

### Post by rickyrockrat on 2007-09-05
If you use dd, you will get an EXACT copy of the old drive (including the old size). I don't think that is what you want.  You can theoretically resize it, but it is a long process that can be avoided.

---

