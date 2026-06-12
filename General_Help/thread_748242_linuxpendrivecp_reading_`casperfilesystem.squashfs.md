---
title: "linuxpendrivecp: reading `casper/filesystem.squashfs': Input/output error"
date: 2008-04-07
forum: General Help
---

### Post by dazulu on 2008-04-07
I've been trying to install 710 on my new 4gb pen drive. I've been following the tutorial over at [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") and all was going well up until the tutorial says to enter in the following command:

```
cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz /media/ubuntu710/
```

I execute the command and all goes well apart from this error message:

```
cp: reading `casper/filesystem.squashfs': Input/output error
```

Is it something to do with space because when I manually go to copy across the file from the live cd it says there is not enough space on the pen drive partition. How would i edit the tutorial to make enough space? It only copies across 428mb of the file when the full size is 600+. Yet there should be enough space because the partition is created with 750mb.

I continued with the tutorial through to the end despite this error and when I boot from the pen drive I get taken to the Busy Box. I've formatted the pen drive and tried the process a few times now with the same results.

Does anybody know what this error means and how I can go about fixing it? 

Thanks in advance! :)

---

### Post by _sluimers_ on 2008-04-18
I'm no expert, but I think it means you have a corrupt file on your live cd.

Get another CD or format your CD (I don't know if that's possible) and (re)install ubuntu 710.

---

