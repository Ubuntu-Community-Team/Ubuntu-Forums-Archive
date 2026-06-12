---
title: "[SOLVED] Automount partition"
date: 2008-07-08
forum: General Help
---

### Post by cyclobs on 2008-07-08
Hey guys, 

i have a windows partition that i store all of my music on, i've configured amarok to use the folder it's all stored in, i was wondering if anyone knew how to make Ubuntu auto mount that partition when i logged into session,

would help out a lot thanks guys :)

---

### Post by iaculallad on 2008-07-08
Post whatever displays when you issue the commands below:

```
cat /etc/fstab

sudo fdisk -l

sudo blkid
```

So, we could tailor your need for auto-mounting.

---

### Post by cyclobs on 2008-07-08
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=246699c0-1262-4d0d-94dd-6496b33467d4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=60f73491-2563-4300-aabd-b926215b83f8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26134   209921323+   7  HPFS/NTFS
/dev/sda2           26135       37607    92156872+   7  HPFS/NTFS
/dev/sda3           37608       38913    10490445    5  Extended
/dev/sda5           37608       38851     9992398+  83  Linux
/dev/sda6           38852       38913      497983+  82  Linux swap / Solaris



/dev/sda1: UUID="A644B11B44B0EF65" TYPE="ntfs" 
/dev/sda2: UUID="44542ECD542EC192" LABEL="Do Not touch" TYPE="ntfs" 
/dev/sda5: UUID="246699c0-1262-4d0d-94dd-6496b33467d4" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="60f73491-2563-4300-aabd-b926215b83f8"


Posted in order of commands.


don't worry about the "do not touch" partition, i'll be fixing that into the non labeled ntfs partition soon :)

---

### Post by iaculallad on 2008-07-08
Say, it's the /dev/sda2 that needs to be auto-mounted:

First thing to do is to install ntfs-3g driver.

```
sudo apt-get install ntfs-3g
```

Then, create the mount point for that device:

```
sudo mkdir /media/musicdrive
```

Open /etc/fstab file for editing:

```
gksudo gedit /etc/fstab
```

and add the line of code below to the last part of the file:

> /dev/sda2 /media/musicdrive ntfs-3g defaults 0 0

Save and Close the File: Drop to your terminal and issue the command:

```
sudo mount -a
```

---

### Post by cyclobs on 2008-07-08
awesome :D

thanks for your help :)

---

### Post by Kaizzer on 2009-10-06
> **iaculallad said:**
> Say, it's the /dev/sda2 that needs to be auto-mounted:

First thing to do is to install ntfs-3g driver.

```
sudo apt-get install ntfs-3g
```Then, create the mount point for that device:

```
sudo mkdir /media/musicdrive
```Open /etc/fstab file for editing:

```
gksudo gedit /etc/fstab
```and add the line of code below to the last part of the file:

/dev/sda2 /media/musicdrive ntfs-3g defaults 0 0                      

Save and Close the File: Drop to your terminal and issue the command:

```
sudo mount -a
```

I there.. new to this linux/Ubuntu world so i would like to ask you if there could be a problem if i make a mistake editing the fstab file .. ie something that you could not ..undone .. .

thanks in advance..-
regards.

---

### Post by erictherev on 2009-10-06
> **Kaizzer said:**
> I there.. new to this linux/Ubuntu world so i would like to ask you if there could be a problem if i make a mistake editing the fstab file .. ie something that you could not ..undone .. .

thanks in advance..-
regards.

Thanks for pointing me to this thread, Kaizzer.

In Linux, there is very little you can do that you cannot undo. The problem I've encountered is that sometimes it takes a while to get the help you need, and the waiting can be almost unbearable. If you are patient, though, there is almost always someone willing to answer your questions and help you out of whatever jam you've gotten yourself into.

Also, don't get your hopes up on this thread... It's been solved for over a year.

---

### Post by dcstar on 2009-10-06
> **Kaizzer said:**
> I there.. new to this linux/Ubuntu world so i would like to ask you if there could be a problem if i make a mistake editing the fstab file .. ie something that you could not ..undone .. .


There are GUI tools that can achieve exactly what you want in this area without having to take risks manually editing these files. Simply install the **pysdm** package: System-Administration-Storage Device Manager.

I cannot fathom why people continually tell new Linux users to stuff around with these files when a better option has existed for a very long time.

---

### Post by erictherev on 2009-10-07
> **dcstar said:**
> There are GUI tools that can achieve exactly what you want in this area without having to take risks manually editing these files. Simply install the **pysdm** package: System-Administration-Storage Device Manager.

I cannot fathom why people continually tell new Linux users to stuff around with these files when a better option has existed for a very long time.

I had never heard of these, and had no clue what ntfs-config did. (I assumed that ntfs-3g would take care of the config for my NTFS partitions.)

Thanks! That's working great now.

Kaizzer... Don't forget to take care of the naming scheme for your NTFS partition in your conkyrc.

---

### Post by Kaizzer on 2009-10-08
> **erictherev said:**
> 
Kaizzer... Don't forget to take care of the naming scheme for your NTFS partition in your conkyrc.

thanks .. i wont .. when im done with the conky upgrade that is driving me nuts since im on 8.04 .. 
:) 

read you in "the other" thread :)

---

### Post by bogdan.s on 2010-01-07
Many thanks to iaculallad; very good article and easy to follow..._[U]_[/U]

---

### Post by babygenius55 on 2010-01-28
> **dcstar said:**
> There are GUI tools that can achieve exactly what you want in this area without having to take risks manually editing these files. Simply install the **pysdm** package: System-Administration-Storage Device Manager.

I cannot fathom why people continually tell new Linux users to stuff around with these files when a better option has existed for a very long time.


Where do you people find all of these nifty commands?

---

### Post by remo_mein05 on 2010-12-14
thanx bro...i like the way linux does it's job...stil gt lot to learn..:-0

---

### Post by MatthewtSmith on 2011-01-12
:KS:Pthanks guys helped lots:P:KS

---

### Post by checoimg on 2011-01-12
How do I have to configure it for a NTFS partition automount? I did it my way and got problems on startup. I it just stops owrking at all I had to enter live session and roll back to old fstab file.

---

### Post by axiom613 on 2011-05-19
Thanks Iaculallad! I know this is an old post but I had the exact same problem, so thanks to all of you.

---

### Post by meka4996 on 2011-06-20
> **dcstar said:**
> There are GUI tools that can achieve exactly what you want in this area without having to take risks manually editing these files. Simply install the **pysdm** package: System-Administration-Storage Device Manager.

I cannot fathom why people continually tell new Linux users to stuff around with these files when a better option has existed for a very long time.

See below the new partition entry added to /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sdc7       /mnt/data160e3p7  ext3  errors=remount-ro         0  0  

That was added by pysdm (System-> Administration-> Storage Device Manager) and it does not use UUID( what if GRUB decides to call the other hard disk sda instead of sdb ??), does not use relatime(causing hard disks to record access time every time, thus slowing down the system! ), does not enable fsck ckecking on the partition(not checking until something weird happens!)

See references:
quoting from /etc/fstab: "UUID= as a more robust way to name devices that works even if disks are added and removed."

relatime: [http://linux.koolsolutions.com/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/](http://linux.koolsolutions.com/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/)

fsck ckecking: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by spoilt-the-programmer on 2011-09-04
Well I found this very straight forward guide. Do give it a try. Its much simple.

Auto Mount Windows Partition in Ubuntu:
[http://bit.ly/rbpSyV](http://bit.ly/rbpSyV)

[Ubuntu Tips and Tricks.]("http://thetechnofreaks.com/category/howtos/ubuntu/")

---

### Post by Mr Atlas on 2013-01-21
> **iaculallad said:**
> Post whatever displays when you issue the commands below:

```
cat /etc/fstab

sudo fdisk -l

sudo blkid
```So, we could tailor your need for auto-mounting.

> **iaculallad said:**
> Say, it's the /dev/sda2 that needs to be auto-mounted:

First thing to do is to install ntfs-3g driver.

```
sudo apt-get install ntfs-3g
```Then, create the mount point for that device:

```
sudo mkdir /media/musicdrive
```Open /etc/fstab file for editing:

```
gksudo gedit /etc/fstab
```and add the line of code below to the last part of the file:



Save and Close the File: Drop to your terminal and issue the command:

```
sudo mount -a
```


Thanks for the helpful tip. Glad this thread turn this into a painless process.

---

