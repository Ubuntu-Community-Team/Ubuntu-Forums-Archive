---
title: "Nautilus stop showing copy file progress after some time"
date: 2019-02-27
forum: General Help
---

### Post by ramesh-chandr on 2019-02-27
Hi, 

I am trying to copy a 12 GB file to my new hard drive connected with SATA to USB adapter. Transfer starts with 250 Mb/s transfer rate later start slowing to upto 176Mb/s and then Nautilus stop showing any progress in copy. But my hard disk shows the sign of busy. if I cancel the copy operation. Nautilus show operation cancelled. But hard disk still show sign of busy. I cannot un-mount the hard disk even after waiting for half an hour. 

I am using Ubuntu 18.10. 

Is there any issue with my hard disk? any suggestion to fix this issue. 

Thanks
Ramesh Chandra

---

### Post by Dennis N on 2019-02-27
Depends on your flash drive's specifications. Kingston Data Traveler USB 2.0 with avg. Random Read Speed 4.75MB/s = approx. 42 minutes to read and transfer 12 gB.

---

### Post by ramesh-chandr on 2019-02-27
I am using a brand new Seagate BarraCuda 4TB Hard Drive 2.5" 15mm SATA III Internal HDD - ST4000LM02. Below are the read/write test result.

```

/$ dd if=/dev/zero of=/media/ramesh/NAS/tempfile oflag=direct bs=8M count=64
64+0 records in
64+0 records out
536870912 bytes (537 MB, 512 MiB) copied, 4.51221 s, 119 MB/s
/$ dd if=/media/ramesh/NAS/tempfile of=/dev/null iflag=direct bs=8M
64+0 records in
64+0 records out
536870912 bytes (537 MB, 512 MiB) copied, 4.43433 s, 121 MB/s


```

---

### Post by Dennis N on 2019-02-27
> I am trying to copy a 12 GB file to my new hard drive connected with SATA to USB adapter.
This suggests that you are coping through USB port. So you are restricted at best to USB transfer speeds by that. What version of USB? You are also copying this file to the new drive from some other device. What would that be? A flash drive? Another hard disk? You didn't say. Whatever it is, it has a certain read speed, so no data can move faster than that. 

For example, If you file was on a Kingston 16gB USB 2.0 Data traveler, this device can only read and send data out at the stated speed (4.75 mB per sec) on average, so you would be further limited to this slow speed, even though USB 2.0 can theoretically transfer data much faster.

---

### Post by ramesh-chandr on 2019-03-02
Don't know the reason for this issue. But when I am using another USB port for my external HDD, it's working fine. Look like there is an issue with the USB port. 

Thanks for your support.

---

