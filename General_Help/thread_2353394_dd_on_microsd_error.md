---
title: "dd on microsd error"
date: 2017-02-21
forum: General Help
---

### Post by ELMIT on 2017-02-21
lsb_release -a
LSB Version:	core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial


I got a Raspberry image to dd to a microSD card (16G, Class 10)

curl -L [https://downloads.raspberrypi.org/raspbian_latest](https://downloads.raspberrypi.org/raspbian_latest) > raspbian.zip
sha1sum raspbian.zip
unzip ./raspbian.zip 
IMAGE_NAME=$(ls | grep raspbian-jessie)
lsblk
DEVICE=/dev/sdd
test -b $DEVICE || echo "ERROR with ${DEVICE:-device}"
echo $IMAGE_NAME
echo $DEVICE
sudo umount /dev/sdd1
sudo umount /dev/sdd2

Till here everything looks fine!


DEV=${DEVICE/disk/rdisk} ; test -b $DEV && sudo dd if=$IMAGE_NAME of=$DEV || echo "ERROR writing $DEV"
dd: writing to '/dev/sdd': Input/output error
899705+0 records in
899704+0 records out
460648448 bytes (461 MB, 439 MiB) copied, 74.034 s, 6.2 MB/s
ERROR writing /dev/sdd



I tried to use gparted to delete every partition. Still the same!

---

### Post by sudodus on 2017-02-21
(461 MB, 439 MiB) copied - I think the image should be much bigger than that, maybe approximately 4 GB.

- Please check the size of the image (img-file)

- Please check that the download was good. You can probably check with md5sum or some other checksum.

If the image is bigger than what was written, something is seriously wrong. Are you sure that /dev/sdd is the correct target device (the 16 GB microSD card)?

I suggest that you try with ***mkusb***, that helps you identify the source file and target drive. Start from the unzipped img file. See the following links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

If mkusb fails too, maybe the card is damaged, so that writing fails, and you would get a corresponding error.

But something else could be failing. I suggest that you try

- in another USB port,
- with a different USB to card adapter,
- a different microSD to SD adapter,
- an SD card slot (if you have one),
-  You can also try with another system,
. for example a live drive with Lubuntu 16.04.1 LTS,
. and *in another computer.* In Windows you can use [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager) to clone from the img file to the card.

---

### Post by ELMIT on 2017-02-21
I used a different card reader, ... then it worked. Thanks!

---

### Post by sudodus on 2017-02-22
You are welcome, and thanks for sharing your solution :-)

---

