---
title: "How to resolve apparent uuid conflict?"
date: 2008-05-07
forum: General Help
---

### Post by MikeB23930 on 2008-05-07
I just got the following error message during boot Kubunut 8.04:

"Log of fsck -C3 -R -A -a 
Wed May  7 19:47:34 2008

fsck 1.40.8 (13-Mar-2008)
/dev/hdc2: clean, 851/642112 files, 75261/2558351 blocks
/dev/hdc6 has been mounted 24 times without being checked, check forced.
/dev/hdc6: 38/1281120 files (5.3% non-contiguous), 3823117/5120710 blocks
fsck.ext3: Unable to resolve 'UUID=945610e4-4b78-4b5e-b56b-804849e1466f'
fsck.ext3: Unable to resolve 'UUID=34677d84-e09d-4afb-939f-88bb98467598'
fsck died with exit status 8

Wed May  7 19:48:10 2008"

Can someone please tell me how to resolve apparent uuid conflict?  Please give detailed step by step instructions.

Further information:  I am trying to dual boot two installations of Kubuntu 8.04, one for general use and one to use to try to figure out how to compile and install the driver for my HVR 950 usb tuner stick.  My guess is the the conflict arises from making a common storage partition, /dev/hdc6, available to both installations, but I have no idea how how to correct this problem.

Thanks,

Mike

---

### Post by drs305 on 2008-05-07
First you might run:
```
sudo blkid
```
which will give you the UUIDs of your current partitions.

Next open /etc/fstab and compare the UUIDs to those from the previous command. The UUIDs from the blkid command are correct. If they are different in fstab, the ones in fstab are probably incorrect. Before editing fstab, back it up.
```
sudo cp /etc/fstab /etc/fstab.bak
```

---

### Post by MikeB23930 on 2008-05-07
> **drs305 said:**
> First you might run:
```
sudo blkid
```
which will give you the UUIDs of your current partitions.

Next open /etc/fstab and compare the UUIDs to those from the previous command. The UUIDs from the blkid command are correct. If they are different in fstab, the ones in fstab are probably incorrect. Before editing fstab, back it up.
```
sudo cp /etc/fstab /etc/fstab.bak
```

Oops, nevermind.  Apparently I only read part of your previous message.

Thanks for the quick reply.

The uuid's for hdc3 and hdc5 in fstab differ from those returned by blkid.  Do I correct things by simply copying the uuid's from blkid into fstab or do I need to do something more complicated?

Thanks,

Mike

---

### Post by drs305 on 2008-05-07
> **MikeB23930 said:**
> Oops, nevermind.  Apparently I only read part of your previous message.

Thanks for the quick reply.

The uuid's for hdc3 and hdc5 in fstab differ from those returned by blkid.  Do I correct things by simply copying the uuid's from blkid into fstab or do I need to do something more complicated?

Thanks,

Mike

If either of these are your root or home directory, I'd post the fstab and blkid commands here before proceeding to have an 'expert' check it out. Otherwise:

If you have made a copy of fstab, feel comfortable editing the file, and are fairly sure you've identified the correct uuid's for hdc3 and hdc5, you simply replace the fstab uuids with the corresponding uuid's for those two partitions from the blkid command.

---

### Post by MikeB23930 on 2008-05-08
> **drs305 said:**
> If either of these are your root or home directory, I'd post the fstab and blkid commands here before proceeding to have an 'expert' check it out. Otherwise:

If you have made a copy of fstab, feel comfortable editing the file, and are fairly sure you've identified the correct uuid's for hdc3 and hdc5, you simply replace the fstab uuids with the corresponding uuid's for those two partitions from the blkid command.

I replaced the uuid's in fstab with the ones returned by blkid.  That solved the problem--until I screw something up next time.

Thanks for your help.

Mike

---

