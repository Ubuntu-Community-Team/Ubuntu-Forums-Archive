---
title: "Problem with partition when installing version 8 ubuntu"
date: 2008-07-06
forum: General Help
---

### Post by shaheel16 on 2008-07-06
Hi there. well at the partition window im having problem to get ubuntu 8.04 KTs desktop ed to install on the desired drive.

I have the following config:

1st hard drive:

C:\(containing Windows OS)
D:\( logical drive used for data storage)



2nd hard drive:

E:\( primary drive left for ubuntu to install)

F:\(data storage logical drive)

so i need to set up ubuntu in the primary partition of disk 2 ( drive "E" here)... so any help plz.zzz.. ?? :confused:

---

### Post by PmDematagoda on 2008-07-06
Well, in your case you will need to use the Manual Partition method, you may have to delete partition sdb1, but please make sure that it is the partition you are looking for by doing:-
```
sudo mkdir /media/test && sudo mount /dev/sdb1 /media/test
```
and then going into /media/test.

After you delete sdb1 you will want to first create a swap partition of about 512mb-1Gb in size, and the remaining space for Ubuntu with the ext3 file system and with / as the mount point.

---

### Post by hal8000 on 2008-07-06
From the live CD environment post the output of
fdisk -l


you will be installing into your second hard drive which ubuntu will see as
/dev/sdb

If you are certain that its the first partition then this will be sdb1, however windows drive naming is pretty useless as a drive letters can be assigned in any order.

---

### Post by shaheel16 on 2008-07-06
OK I'll delete the partition.. 

 are u sure that i'll be able to use both the windows on the first drive and ubuntu on the second one...??

---

### Post by shaheel16 on 2008-07-06
> **hal8000 said:**
> From the live CD environment post the output of
fdisk -l


you will be installing into your second hard drive which ubuntu will see as
/dev/sdb

If you are certain that its the first partition then this will be sdb1, however windows drive naming is pretty useless as a drive letters can be assigned in any order.




Ok I'll try this on ubuntu.. and i'll post it here...

:)

---

### Post by PmDematagoda on 2008-07-06
> **shaheel16 said:**
> OK I'll delete the partition.. 

 are u sure that i'll be able to use both the windows on the first drive and ubuntu on the second one...??

Yes you can, GRUB makes this possible, and GRUB is automatically installed and configured during the Ubuntu install.

---

### Post by shaheel16 on 2008-07-06
Well from GPARTED on ubuntu live cd ive got the following:

/dev/sdf1   the partition im keeping for ubuntu


/dev/sdf2   another partition containing data ..


so i delete sdf1 during install and create a swap then remaining t mount ubuntu? ?

---

### Post by PmDematagoda on 2008-07-06
If your information is correct, then yes, that is what you should do.

---

### Post by shaheel16 on 2008-07-06
OK.. I cross my fingers.... Hope this work out perfectly....

Thanks a lot for your suggestions... :KS

---

### Post by shaheel16 on 2008-07-06
Well All went much fine than I expected...


The very first option(Otomatic resize) worked well.. Ubuntu just took that particular partition and installed itself and my windows is still there ...

All systems fine.. Thanks once againe for those who were there yesterday guding me..... :popcorn:

---

