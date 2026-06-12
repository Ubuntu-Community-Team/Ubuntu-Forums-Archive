---
title: "GUID Partition Table (GPT) drive imaging software for linux variants?"
date: 2013-05-10
forum: General Help
---

### Post by pursuvant on 2013-05-10
Why is it difficult to find backup software that can image hard disks with GPT for linux variants ? I have a System 76 gazp8 with Intel 520 series 240G SSD (GUID Partition Table). Looking for backup software for one of the layers in my backup strategy, checked many references on this forum - but when looking into details i found they (i.e. Clonezilla) use fdisk and that is not going to work out if you want to image GPT disks.

Does anyone make software for linux that can image & restore a GPT hard disk correctly? I'm talking imaging here please (not cloning), all sectors on the disk, with compression, to an image file on a usb external hard drive dedicated for holding backup images. Imaging software would boot from CD/DVD to perform the image & restore operations. Thanks in advance, for allowing me to ask a question that gets asked million + one times.

---

### Post by albandy on 2013-05-10
So you want to make a compressed image of an entire disk?

run as sudo:

 dd if=/dev/sdb conv=sync,noerror bs=64K | gzip -c  > /media/my_usb_disk/sdb.img.gz

this will make an image of the disk sdb, compress it and save in your usb disk  as sdb.img.gz

to restore it:
gunzip -c /media/my_usb_disk/sdb.img.gz | dd of=/dev/sdb conv=sync,noerror bs=64K


Of course you've to use a filesystem in the usb disk that support large files, don't use FAT32 as it's limited to 4GB per file.

You can do this stuff using the ubuntu live cd.

---

### Post by pursuvant on 2013-05-13
Thx albandy, my first linux box will get here this week, so i can't test  the scripts below yet, but given dd is the way to go this should be  pretty close. Any critiques would be appreciated

-----------------------
#!/usr/gmill/bin/bash/bakups 


# 
# GPT SSD DRIVE IMAGE
#
# Notes:
# boot from unbuntu live cd
# run as sudo (root access)
# no partitions should be mounted on the drive that will be imaged
# Don't zero empty blocks on an SSD when during imaging
# To make any script executable: chmod 777 <scriptfilename.sh>
# 

# Setup static variables for this script run...
LAPTOP        ="gazp8"

# Stamp all the operations with the same local timestamp...
NOW=$(date +"%Y%m%d.%H%M%S")

# Destination file for this image...
GZIMGFILE="$NOW.$LAPTOP.sda.img.tar.gz"

# Destination file for backup of the GPT Partition table only...
GZGPTFILE="$NOW.$LAPTOP.sda.sgdisk.backup.gpt"

# Blocksize for run...
BLOCKSIZE="1024K"

# Echo run variables...
echo "LAPTOP: ${LAPTOP}"
echo "NOW: ${NOW}"
echo "GZIMGFILE: ${GZIMGFILE}"
echo "GZGPTFILE: ${GZGPTFILE}"
echo "BLOCSIZE: ${BLOCKSIZE}"

# CREATE DRIVE IMAGE...
# Mount the NTFS external usb drive that is destination for the backup image file...
mount -t ntfs-3g /dev/sdb1 /mnt/sdb1

# Image drive to file located on the external usb drive...
sudo dd if=/dev/sda conv=sync,noerror bs=$BLOCKSIZE | gzip -c > /mnt/sdb1/$GZIMGFILE

# snap a separate backup, of protective MBR, the main header, the backup header, and one copy of the partition table...
sgdisk -b /mnt/sdb1/GZGPTFILE /dev/sda

# Store drive geometry info as text for quick ref...
gdisk -l /dev/sda > /mnt/sdb1/$GZIMGFILE.gdisk.info

 
------------------------------------

#!/usr/gmill/bin/bash/bakups  

# 
# GPT SSD DRIVE RESTORE
#
# Notes:
# boot from unbuntu live cd
# run as sudo (root access)
# Don't zero empty blocks on an SSD when during imaging
# To make any script executable: chmod 777 <scriptfilename.sh>
# 

# Setup static variables for this script run...
LAPTOP        ="gazp8"

# Stamp all the operations with the same local timestamp...
NOW=$(date +"%Y%m%d.%H%M%S")

# Source image file to be restored (example below was created on 2013-05-10 at 10:22:36am)...
GZIMGFILE="20130510.102236.$LAPTOP.sda.img.tar.gz"

# Destination file for backup of the GPT Partition table only...
GZGPTFILE="$NOW.$LAPTOP.sda.sgdisk.backup.gpt"

# Blocksize for run...
BLOCKSIZE="1024K"

# Echo run variables...
echo "LAPTOP: ${LAPTOP}"
echo "NOW: ${NOW}"
echo "GZIMGFILE: ${GZIMGFILE}"
echo "GZGPTFILE: ${GZGPTFILE}"
echo "BLOCSIZE: ${BLOCKSIZE}"


# CREATE DRIVE IMAGE...
# Mount the external usb drive that is source of the restore file...
mount -t ntfs-3g /dev/sdb1 /mnt/sdb1

# Restore drive from the image file on external USB drive...
sudo gunzip -c /mnt/sdb1/$GZIMGFILE | dd of=/dev/sda conv=sync,noerror bs=$BLOCKSIZE 

# snap a separate backup, of protective MBR, the main header, the backup header, and one copy of the partition table...
sgdisk -b /mnt/sdb1/GZGPTFILE /dev/sda

# Store drive geometry info as text for quick ref of the restored disk...
gdisk -l /dev/sda > /mnt/sdb1/$NOW.restored.$GZIMGFILE.gdisk.info

# swap is located on the primary drive, it will be activated automatically...
# no change to partitions, so no changes needed to mountpoint instructions...

---

