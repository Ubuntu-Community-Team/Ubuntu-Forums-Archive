---
title: "Installed ubuntu and now 2 partitions removed ( C windows and D My files)"
date: 2014-09-28
forum: General Help
---

### Post by thumper2 on 2014-09-28
Hello,

I just had problem with my laptop and re-installed ubuntu... Something went wrong and i see that BOTH Disc's C (where windows was installed)  and D (where all my files were stored) are removed.

Can some1 tell me if i cant get BACK disc D files? I have some IMPORTANT files in there and i would like to have my files back.

I dont care much for disc C ( windows 8 files ) i just need D files.

Thanks :(

---

### Post by AnotherKevin on 2014-09-28
Use your Windows install disk and it should repair it automatically.  Just put the disk in the drive and turn the computer on. 

Kevin

---

### Post by ajgreeny on 2014-09-28
You unfortunately fell foul of the bug that wipe the whole disk in spite of you telling the installer to reinstall using just the ubuntu partition, and I am not sure that the windows install disk will repair your system and get back the files as the partitions have now been formatted and are gone.
See [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

You may be able salvage something using testdisk [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) which I have never used so can not help with details of how to use.

Good luck!

---

### Post by thumper2 on 2014-09-28
> **AnotherKevin said:**
> Use your Windows install disk and it should  repair it automatically.  Just put the disk in the drive and turn the  computer on. 

Kevin




First thanks for your reply, I had two partitions Local disc C (where windows 8 was installed) and local disc D (where i had my stuff stored) after i installed ubunt i think Disc has been formated, so i just see one partition now :(  im not sure if windows repair will restore my Files (local D files)

---

### Post by thumper2 on 2014-09-28
> **ajgreeny said:**
> You unfortunately fell foul of the bug that wipe the whole disk in spite of you telling the installer to reinstall using just the ubuntu partition, and I am not sure that the windows install disk will repair your system and get back the files as the partitions have now been formatted and are gone.
See [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

You may be able salvage something using testdisk [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) which I have never used so can not help with details of how to use.

Good luck!

Thanks for your reply!

I may try this dadaRecovery link but the problem is that i never used ubuntu before and im not sure if i will be able to do it :(  If some1 can tell me step by step how to do it would be awesome :)

Screen of disc looks now: [http://i.imgur.com/ZpTcZj6.png](http://i.imgur.com/ZpTcZj6.png)

Thank you again!

---

### Post by oldfred on 2014-09-28
Besides testdisk many suggest Windows utilities for NTFS partitions.

But you may have to remove drive and plug into a working Windows system.

 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

### Post by thumper2 on 2014-09-28
> **oldfred said:**
> Besides testdisk many suggest Windows utilities for NTFS partitions.

But you may have to remove drive and plug into a working Windows system.

 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.


I will try, Thanks alot man!!!

---

### Post by nerdtron on 2014-09-28
Although I'm not here to offer any solution, Im here to say a few things to prevent this from happening again. Every now and then I see post like this and it makes me feel sad that people are risking/losing their data on the installation of Ubuntu. Sometimes it becomes a bad image on other people that Ubuntu caused them to lose their data.

1. Always make sure to have a backup of your data whenever you install a new OS (even Windows can wipe the hard drive during install)
2. Be familiar with the options on your installation. Ubuntu installer has different install option than the windows installer. You should have read carefully on what each options does and what option best fits your scenario.
3. Learn how to use "Something Else" option in the Ubuntu installer. Although this one is advance, this is very much the safest way on determining what exactly the installer will do to your hard drive partitions. This is where the you can customize what partition you are going to install Ubuntu much as the same way you choose which partition to install windows.

Good luck with recovering your data. I hope you would recover much of it. 

BTW, when recovering data from a wiped hard drive, be sure to save the recovered data on a separate hard drive so that the old data on the original hard drive won't be overwritten. Each time you write/save on your hard drive, the deleted data will be harder to recover.

---

### Post by thumper2 on 2014-09-29
> **nerdtron said:**
> Although I'm not here to offer any solution, Im here to say a few things to prevent this from happening again. Every now and then I see post like this and it makes me feel sad that people are risking/losing their data on the installation of Ubuntu. Sometimes it becomes a bad image on other people that Ubuntu caused them to lose their data.

1. Always make sure to have a backup of your data whenever you install a new OS (even Windows can wipe the hard drive during install)
2. Be familiar with the options on your installation. Ubuntu installer has different install option than the windows installer. You should have read carefully on what each options does and what option best fits your scenario.
3. Learn how to use "Something Else" option in the Ubuntu installer. Although this one is advance, this is very much the safest way on determining what exactly the installer will do to your hard drive partitions. This is where the you can customize what partition you are going to install Ubuntu much as the same way you choose which partition to install windows.

Good luck with recovering your data. I hope you would recover much of it. 

BTW, when recovering data from a wiped hard drive, be sure to save the recovered data on a separate hard drive so that the old data on the original hard drive won't be overwritten. Each time you write/save on your hard drive, the deleted data will be harder to recover.

Thank you sir!

---

