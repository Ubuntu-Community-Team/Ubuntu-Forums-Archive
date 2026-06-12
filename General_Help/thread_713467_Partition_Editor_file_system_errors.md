---
title: "Partition Editor file system errors"
date: 2008-03-02
forum: General Help
---

### Post by elicoten on 2008-03-02
I was trying to move & resize a partition on a USB drive when the USB connection failed and basically somehow got disconnected from the drive. The partition editor gave read errors and then said cannot stat /dev/sdb3, basically it got completely cut off. I connected the drive to a windows machine and it was dead as well. 

I unplugged the drive from the power and then plugged it in again and it connected again, but now when I try to resize the same partition (the resize operation didn't complete) I just get a whole load of error messages (see attachment).

What can I do to fix this partition so I can resize it. I can mount the partition and the files do seem to be there.

Thanks in advance

---

### Post by danielcc on 2008-03-02
could you move the data and make a new partition, then move it back?

---

### Post by elicoten on 2008-03-03
I don't know - is there any risk of corrupt the data by attempting to mount the partition and read the data?

Also how difficult is it to backup the linux system partition? Will simply copying the files be enough or does it need more than that? With Windows, if you simply copy the files to another partition and then back again the system is unbootable after that. You need special tools to backup a complete system?

---

