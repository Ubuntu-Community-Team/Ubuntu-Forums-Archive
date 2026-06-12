---
title: "Mounting new hard drive in Ubuntu 12.10"
date: 2013-03-19
forum: General Help
---

### Post by mathu12 on 2013-03-19
Hello all. I am quite new to Ubuntu and am requesting a bit of help with my new hard drive install. I have built a home theater and I am using this computer as the home theater computer. I installed Ubuntu 12.10 and have liked it so far. I will use the computer to stream media and play it directly to my projector via HDMI. To store all of my media, I just purchased a new Western Digital 1TB Blue Sata hard drive. I installed it but am not able to see if in the file system. 

So, my question is, can someone walk me through the process of formatting to the correct Linux file system/ mounting the hard drive properly/ naming it and placing correctly to easily place and access media files? Sorry for such a simple question but after spending hours searching, I have not been able to get it right. Any help would be greatly appreciated.

Thanks.

---

### Post by Bashing-om on 2013-03-19
mathu12; Hi ! Welcome back !

See if this link answers your questions. The instructions are clear and concise, works for me !
[http://help.ubuntu.com/community/InstallingANewHardDrive](http://help.ubuntu.com/community/InstallingANewHardDrive)[INDENT=2]
where there is a will there is a way

[/INDENT]

---

### Post by mathu12 on 2013-03-20
Thanks so much for the reply Basing-on. I followed the link you provided and I am now able to see and use the new hard drive. There is one new concern however. When I reboot now, it get an error: "The disk drive for /my drive/... is not ready yet or not present". Not sure what is causing this. I would like to get rid of this error if anyone has any ideas.

Thanks.

---

### Post by oldfred on 2013-03-20
I post the same instructions as Bashin-on, but have not looked at them for a while. They still suggest using device for mounting in fstab, but we all use UUID as UUID has less chance of changing. External drives and even my internal drives sometimes change device numbers. I skipped a port on motherboard and sometimes my flash drive is sdb and sometime sde. And then all my drives get different device numbers.

Post UUID & fstab.

       sudo blkid -c /dev/null -o list
      
 cat /etc/fstab

We can give specific instructions or follow these directions.
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

      
 More info on Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by mathu12 on 2013-03-21
> **oldfred said:**
> I post the same instructions as Bashin-on, but have not looked at them for a while. They still suggest using device for mounting in fstab, but we all use UUID as UUID has less chance of changing. External drives and even my internal drives sometimes change device numbers. I skipped a port on motherboard and sometimes my flash drive is sdb and sometime sde. And then all my drives get different device numbers.

Post UUID & fstab.

       sudo blkid -c /dev/null -o list
      
 cat /etc/fstab

We can give specific instructions or follow these directions.
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

      
 More info on Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

This is the result of the sudo blkid -c /dev/null -o list:

/dev/sda1  ext2             /boot          993976d9-5c75-480e-acd5-71af29edf7f2
/dev/sda5  LVM2_member      (in use)       Ir4t2D-9M00-mUKm-06U9-G3Yb-PNTm-yBDdRK
/dev/sdb2  ntfs             /media/mathu12/52561BBB6BC88055 52561BBB6BC88055
/dev/mapper/ubuntu-root
           ext4             /              42d9eb40-bc70-4111-b9c9-c4e7fb289f6c
/dev/mapper/ubuntu-swap_1
           swap             <swap>         f6cffaff-a7bc-49f1-888a-5bbf778b3c25

And this for the cat /etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=993976d9-5c75-480e-acd5-71af29edf7f2 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu-swap_1 none            swap    sw              0       0
/dev/sdb1    /mnt/HDD1   ntfs    defaults     0        2

Thanks.

---

### Post by oldfred on 2013-03-21
I do not know LVM and what difference that many make.

But you show no sdb1, but do have a sdb2 as NTFS.

And in fstab you are trying to mount sdb1 which does not seem to exist?

Either change to the sdb2 or better to the UUID of sdb2.

Preferred format of NTFS type entry.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
> UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

      
 ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a

---

### Post by mathu12 on 2013-03-23
> **oldfred said:**
> I do not know LVM and what difference that many make.

But you show no sdb1, but do have a sdb2 as NTFS.

And in fstab you are trying to mount sdb1 which does not seem to exist?

Either change to the sdb2 or better to the UUID of sdb2.

Preferred format of NTFS type entry.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:

Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

      
 ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a

Thanks so much for the info. I updated my fstab with the UUID for my hard drive with the template by Morbius1 and it worked great. No more issues with my new hard drive. Thanks to everyone. I am marking this one "Solved".

---

