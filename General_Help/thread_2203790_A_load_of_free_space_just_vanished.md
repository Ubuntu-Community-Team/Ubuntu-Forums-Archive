---
title: "A load of free space just vanished"
date: 2014-02-05
forum: General Help
---

### Post by Przemysaw_aba on 2014-02-05
Well, it's kind of unusual and serious problem. For two or  three weeks circa 20 GB from my home folder just vanished. It's not a  matter of any big files, even hidden, because I checked it out many  times and I used disc analyzer. 
  How does it look from my perspective? Maybe (but it is only guess,  not proof) it's a fault of VirtualBox. At least, the problem began after  installing this program. I choose an option of create virtual disc or  something like that, but then I claimed there is no need to do this, and  soon turn on the program. However, the trouble occur. The computer  started to work hard and there was shown info, that there is only 900 MB  free space (more or less, I do not remember, but it should be 20 GB). 
  What I remember is then I wanted to uninstall VitrualBox and X86  virtualization solution, but it was just impossible. I tried to switch  on root, but after log out there was shown a column of communiques and  the only way to turn off the computer was power cut. When I log in root,  some problems still existed, I didn't see any possible large files or  something, and what is more there was a communique-info about any error  of programmer. 
  But nevermind. Finally I uninstalled both VirtualBox and X86  virtualization solution. However the trouble still existed. I also  deleted some large programs, like PlayOnLinux, so it allowed me to get a  few GB free space. Still too less, but...
  It is quite bizarre. The free space in my home folder changes  regardless if I download or delete files. Well, there was a period, when  I didn't download or delete, just shut down or turn on my computer, and  free space rised. After delete Playonlinux, there was 3,5 GB free  space, and after next day it was circa 8 GB, then even over 10. But it  is still too little. 
  Two days ago, I had to copy some files form my pendrive. They were  only powerpoint presentations, so the size of them was about few MB.  After plug in pendrive and copy files, the computer slow down again, and  the communique about no free space on disc occur again. It was  necessary to me to work on it, so I deleted two large files (about 6,5  GB) to work calm, but after next turning on computer, this free space  also vanished! 
  I do not know if I make myself clear. It does not look like there is  any large file on my disc, but if something still shortened the disc  size. I do not know if it is any tip, but when I want to edit a file  made in LibreOffice, I cannot do this, because there is communique about  use to read only or open copy. Before this accident it had never occur.

result of df -h

```
System plików  rozm. u&#380;yte dost. %u&#380;. zamont. na
/dev/sda8        82G   77G  963M  99% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            996M  4,0K  996M   1% /dev
tmpfs           202M  1,1M  201M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none           1008M   12K 1008M   1% /run/shm
none            100M   60K  100M   1% /run/user
/dev/sda1       118G   52G   66G  45% /media/root/7018FEB618FE7A84
/dev/sda6       166G  2,0G  156G   2% /media/root/fb1f683e-18b2-4643-b08b-6e98ceae3abe
```

result of sudo parted --list:

```
Model: ATA WDC WD5000AAKS-0 (scsi)
Dysk /dev/sda: 500GB
Rozmiar sektora (logiczny/fizyczny): 512B/512B
Tablica partycji: msdos

Numer  Pocz&#261;tek  Koniec  Rozmiar  Typ       System plików   Flaga
 1     32,3kB    126GB   126GB    primary   ntfs            &#322;adowalna
 2     126GB     500GB   374GB    extended                  lba
 5     126GB     220GB   94,0GB   logical   ntfs
 8     220GB     309GB   89,6GB   logical   ext4
 9     309GB     313GB   3846MB   logical   linux-swap(v1)
 6     313GB     494GB   181GB    logical   ext4
 7     494GB     500GB   6179MB   logical   linux-swap(v1)
```

```
ubuntu@ubuntu:~$ sudo parted --list
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32,3kB  126GB  126GB   primary   ntfs            boot
 2      126GB   500GB  374GB   extended                  lba
 5      126GB   220GB  94,0GB  logical   ntfs
 8      220GB   309GB  89,6GB  logical   ext4
 9      309GB   313GB  3846MB  logical   linux-swap(v1)
 6      313GB   494GB  181GB   logical   ext4
 7      494GB   500GB  6179MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label      
```

```

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                 1007M   41M  966M   5% /
none                 1002M  296K 1002M   1% /dev
/dev/sr0              686M  686M     0 100% /cdrom
/dev/loop0            658M  658M     0 100% /rofs
none                 1007M  104K 1006M   1% /dev/shm
tmpfs                1007M   12K 1007M   1% /tmp
none                 1007M   88K 1007M   1% /var/run
none                 1007M  4,0K 1007M   1% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda5              88G   57G   31G  65% /media/Nowy
/dev/sda1             118G   52G   66G  45% /media/7018FEB618FE7A84
/dev/sda6             166G  2,2G  156G   2% /media/fb1f683e-18b2-4643-b08b-6e98ceae3abe
/dev/sda8              83G   78G  970M  99% /media/c8fe3d9b-0bf7-4337-a9d5-81cd543b4664


```

```

Model: ATA WDC WD5000AAKS-0 (scsi)
Dysk /dev/sda: 500GB
Rozmiar sektora (logiczny/fizyczny): 512B/512B
Tablica partycji: msdos

Numer  Pocz&#261;tek  Koniec  Rozmiar  Typ       System plików   Flaga
 1     32,3kB    126GB   126GB    primary   ntfs            &#322;adowalna
 2     126GB     500GB   374GB    extended                  lba
 5     126GB     220GB   94,0GB   logical   ntfs
 8     220GB     309GB   89,6GB   logical   ext4
 9     309GB     313GB   3846MB   logical   linux-swap(v1)
 6     313GB     494GB   181GB    logical   ext4
 7     494GB     500GB   6179MB   logical   linux-swap(v1)



```

That's how looked disc usage in 28.01.




[IMG]http://oi57.tinypic.com/jb5xxv.jpg[/IMG]

And how it looks now. 

[IMG]http://oi61.tinypic.com/wlsmwx.jpg[/IMG]

Any ideas?

---

### Post by jeanjd63 on 2014-02-05
Hello

You can do a :
[B]sudo  du  -sh  /*  | sort -rh
[/B]You 'll find where is the biggest directory and then inside you will find by :
[B]sudo  du  -sh  /directory/*  | sort -rh
[/B]etc...

---

### Post by Przemysaw_aba on 2014-02-05
Hello

Thank You for Your advice. I think it can be valuable, but I must ask one more question. 
It seems, that the cause of trouble are those files: 

```
9,8G    /var/log/syslog.1
9,8G    /var/log/kern.log
7,8G    /var/log/kern.log.1
394M    /var/log/mysql
305M    /var/log/kern.log.2.gz
197M    /var/log/syslog.2.gz
```

Is there any possibility to delete them or something? I do not want to make any damage in my system.

---

### Post by Przemysaw_aba on 2014-02-06
All right, the case is solved. I delete log files by BleachBit.

---

### Post by Bashing-om on 2014-02-06
Przemysaw_aba; Hi !

That is good, but not well. - deleting the log files -
There is a reason the log files have grown to such a large size and requires investigation for what is running amuck.
(old config files from the VM environment ? )

[INDENT][INDENT]The system is talking to you
[/INDENT][/INDENT]

---

### Post by JKyleOKC on 2014-02-06
> **Przemysaw_aba said:**
> How does it look from my perspective? Maybe (but it is only guess,  not proof) it's a fault of VirtualBox. At least, the problem began after  installing this program. I choose an option of create virtual disc or  something like that, but then I claimed there is no need to do this, and  soon turn on the program. However, the trouble occur. The computer  started to work hard and there was shown info, that there is only 900 MB  free space (more or less, I do not remember, but it should be 20 GB).When you chose the "create virtual disk" option, the VBox wizard program created the virtual disk as a large file within your home directory. Depending on which version of VBox you used, that large file could be stored inside a hidden directory named ".VirtualBox" within your home directory, and inside of the "HardDisks" subdirectory within ".VirtualBox" or alternatively inside a directory named the same as your virtual machine's name, within the "VirtualBox VMs" directory in your home directory.

In either case, that large file with the ".vdi" extension type may be the root cause of your problem. As for uninstalling VirtualBox, the method of doing so depends on how you installed it. If you installed from the Software Center, you should be able to uninstall it from the Software Center. If you used "apt-get" from a command line, then "apt-get" should do the job for you.

Edit--If you aborted creation of the virtual disk, and then attempted to start the virtual machine anyway, you may have simply created an infinite loop as the virtual machine attempted to access the non-existent virtual disk. This could have caused the logs to grow huge, and finally run out of space on the disk. Since you deleted the logs it's no longer possible to tell whether this is what happened, but if the logs don't grow back to multi-GB sizes, it's quite likely to be the case. I would keep an eye on syslog and kern.log for the next few reboots just to be sure there's nothing else going on...

---

