---
title: "Using &quot;dd&quot; to clone boot drive"
date: 2013-04-10
forum: General Help
---

### Post by streat on 2013-04-10
Hello all, I would like to clone my boot partition to another drive to be stored offsite. I have read that using the command "dd if=/dev/sda of=/dev/sdb bs=32" is a solid way to clone a drive but I have also read this can cause corruption if the drive is mounted as my boot drive would be. Does anyone have a suggestion for a work around or a better solution to cloning my boot drive for redundancy purposes?
Thank you!

---

### Post by oldfred on 2013-04-10
The command dd is very powerful and will work like you want if you do not have second drive still plugged in afterwards. It creates exact image so you have duplicate UUIDs and settings and system will not boot correctly with both drives plugged in. dd also copies empty space, so is slower,  and must be from same size to same size.

 Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

 Many just use clonezilla.
Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

      Tar backup script:
[https://help.ubuntu.com/12.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/12.04/serverguide/C/backup-shellscripts.html)
But do not use dd for copies from MBR to gpt partitioned drives, use cp -a
[https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)

     I do not do full image backups as I see no advantage to backing up system. My plan is just a reinstall and restore data. But I have a home system, and if a business, you should have regular backups & off site backups.

---

### Post by streat on 2013-04-10
Worked perfectly, thank you!!

---

