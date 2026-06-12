---
title: "External HDD trying to mount an formated partition"
date: 2015-10-03
forum: General Help
---

### Post by aru2 on 2015-10-03
Hello,

This is kind of a long story so ill try to be brief...

When i bought my machine I got it with windows 8.1 but then I changed the mechanical HDD that it came with for an SSD and I reused the mechanical drive as an external HDD.

Then i plugged in my now external HDD and i got an error saying that it was unable to mount windows... well I didn't really care about that because I only wanted to use the HDD as a backup drive. 

So I did a quick format and started copying my files in. 

Now every time I plug in my external HDD I get this error:

[http://http://i92.photobucket.com/albums/l7/arutsuro-kun/HDD.png](http://http://i92.photobucket.com/albums/l7/arutsuro-kun/HDD.png)

As you can see in the image I have a Bkp1 partition (which is where i copied all my files after the quick format) and LENOVO which is the one thats supposed to be gone at this point and its refusing to die... 

So i have no idea what to do... i can still use the HDD but its kind of annoying that its always trying to mount that old partition...

Any ideas?

---

### Post by TheFu on 2015-10-03
What are the partition labels?  Do any of them match/conflict?

BTW, large inline  images like that aren't nice to people who pay by the byte for internet.  Would nicer to make it an attachment.
[B]
Update:[/B]
yancek's reply below is probably the issue.  Boot Windows, disable fastboot. 
Explanation: [https://askubuntu.com/questions/452071/why-disable-fast-boot-on-windows-8-when-having-dual-booting](https://askubuntu.com/questions/452071/why-disable-fast-boot-on-windows-8-when-having-dual-booting)

---

### Post by yancek on 2015-10-03
The last sentence in your error message tells you what to do.  You were using the drive with windows and did not do a full shutdown.  Windows standard is to hibernate so it appears to be booting faster so you need to select one of the two options suggested in the message.

---

### Post by aru2 on 2015-10-03
@TheFu Im sorry about the image, I didnt think of that.

I dont think you guys understood me correctly... let me clarify...

The LENOVO partition was quick formated ... meaning that its supposed to have everything deleted from it.
The new label in its place is the Bkp1 label...

That error message is absurd because that partition label isnt even supposed to exist anymore.

---

### Post by TheFu on 2015-10-04
Please post the text output from these commands:
```
df -h
sudo parted -l
```
from just after the error.

---

### Post by aru2 on 2015-10-04
Ok, here is the result, thanks for the help 

> aru@Mari:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G   46M  1.6G   3% /run
/dev/sda2       424G   21G  382G   6% /
tmpfs           7.8G  1.4M  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sda1       511M  3.4M  508M   1% /boot/efi
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           1.6G   76K  1.6G   1% /run/user/1000
/dev/sdb3       996M  499M  498M  51% /media/aru/LRS_ESP
/dev/sdb5       893G  193G  700G  22% /media/aru/Bkp1
aru@Mari:~$ sudo parted -l
[sudo] password for aru: 
Model: ATA KINGSTON SHSS37A (scsi)
Disk /dev/sda: 480GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system     Name                  Flags
 1      1049kB  538MB  537MB   fat32           EFI System Partition  boot, esp
 2      538MB   463GB  462GB   ext4
 3      463GB   480GB  17.1GB  linux-swap(v1)


Model: WDC WD10 S21X-24R1BT0-SSH (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  1050MB  1049MB  ntfs         Basic data partition          hidden, diag
 2      1050MB  1322MB  273MB   fat32        EFI system partition          boot, hidden, esp
 3      1322MB  2371MB  1049MB  fat32        Basic data partition          hidden
 4      2371MB  2505MB  134MB                Microsoft reserved partition  msftres
 5      2505MB  960GB   958GB   ntfs         Basic data partition          msftdata
 6      960GB   987GB   26.8GB  ntfs         Basic data partition          msftdata
 7      987GB   1000GB  13.1GB  ntfs         Basic data partition          hidden, diag


aru@Mari:~$ 



---

### Post by aru2 on 2015-10-04
Hi, 

I found out what was going on... apparently the quick format didn&#8217;t eliminate the previous label it only created a new partition out of it ... which is strange... I used gparted to find the LENOVO partition, plus some other windows hidden recovery partitions and i reclaimed several GBs from my HDD and no more error! so im a happy camper now.

Thank you very much for your help I appreciate your time.

Regards.

---

### Post by yancek on 2015-10-04
Formatting a partition is not going to change the label if the partition has a label.  You can change labels for partitions in GParted.

---

