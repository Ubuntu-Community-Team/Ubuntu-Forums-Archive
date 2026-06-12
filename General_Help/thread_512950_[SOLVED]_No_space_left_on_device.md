---
title: "[SOLVED] No space left on device"
date: 2007-07-29
forum: General Help
---

### Post by init1 on 2007-07-29
I am trying to transfer files to a fat16 partition on my HD, but I get the "No space left on device" error. ```
df
``` says I have plenty of space left.

---

### Post by AlexThomson_NZ on 2007-07-29
Fat16 has a 2Gb limit, are you sure you're not just hitting that?

(Maybe df doesn't recognise those limits(?))

---

### Post by cilynx on 2007-07-29
I don't suppose you could give us a full terminal c&p of you trying the transfer along with the df output?

---

### Post by init1 on 2007-07-29
> **AlexThomson_NZ said:**
> Fat16 has a 2Gb limit, are you sure you're not just hitting that?

(Maybe df doesn't recognise those limits(?))
Nope. Checked that. The partition is only about 1GB, little more. 
Here is the df dump
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7             10799912   6721872   3529424  66% /
varrun                  253188       108    253080   1% /var/run
varlock                 253188         0    253188   0% /var/lock
procbususb              253188       100    253088   1% /proc/bus/usb
udev                    253188       100    253088   1% /dev
devshm                  253188         0    253188   0% /dev/shm
lrm                     253188     33788    219400  14% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1             10980932   4666052   5980168  44% /media/sda1
/dev/sda2             31537776  30753764    784012  98% /media/sda2
/dev/sda4              1172544     29856   1142688   3% /home/none/a
The device I am having issues with is /dev/sda4.

---

### Post by cilynx on 2007-07-30
What utility are you using to transfer?

---

### Post by init1 on 2007-07-30
> **cilynx said:**
> What utility are you using to transfer?
cp/mv.

---

### Post by dando80 on 2007-07-30
What does df -i say?

---

### Post by init1 on 2007-07-30
> **dando80 said:**
> What does df -i say?
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda7            1373568  142187 1231381   11% /
varrun                 63297      52   63245    1% /var/run
varlock                63297       1   63296    1% /var/lock
procbususb             63297    2886   60411    5% /proc/bus/usb
udev                   63297    2886   60411    5% /dev
devshm                 63297       1   63296    1% /dev/shm
lrm                    63297      17   63280    1% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1            1403520  116139 1287381    9% /media/sda1
/dev/sda2            4014080    6013 4008067    1% /media/sda2
/dev/sda4                  0       0       0    -  /home/none/a

---

### Post by dando80 on 2007-07-30
Doh!! Sorry for wasting your time. df -i is irrelevant for FAT16. Sorry...

Do you get the no space error regardless of what you try to copy there? Are you trying to create a file over 2GB in size by any chance? Can you try running scandisk / chkdsk, or whatever it is called,  against it from Windoze? Or fsck.msdos /dev/sda4 from linux while it is unmounted?

---

### Post by init1 on 2007-07-30
> **dando80 said:**
> Doh!! Sorry for wasting your time. df -i is irrelevant for FAT16. Sorry...

Do you get the no space error regardless of what you try to copy there? Are you trying to create a file over 2GB in size by any chance? Can you try running scandisk / chkdsk, or whatever it is called,  against it from Windoze? Or fsck.msdos /dev/sda4 from linux while it is unmounted?
Yes, even 
```

touch file.txt

```
fails.
I ran fsck.mdos and I didn't get any errors. Could it be because I have so many files? Is there a file limit for fat16?

---

### Post by AlexThomson_NZ on 2007-07-30
Fat16 supports 65,517 files

---

### Post by init1 on 2007-07-30
> **AlexThomson_NZ said:**
> Fat16 supports 65,517 files
I don't think I even got close.
If I delete some files, I can add more. Would fat32 be more reliable?

---

### Post by AlexThomson_NZ on 2007-07-30
Fat32 would be much better, or NTFS even better still (is ext3 an option?- you get get programs for windows that allow it to use ext partitions)

---

### Post by init1 on 2007-07-31
> **AlexThomson_NZ said:**
> Fat32 would be much better, or NTFS even better still (is ext3 an option?- you get get programs for windows that allow it to use ext partitions)
No windows for me. I have this partition for freedos. I was using fat16 because the freedos defrager only supported fat16. I guess I'll try mkfs.vfat now.

---

### Post by init1 on 2007-07-31
Yep, it worked :D.

---

