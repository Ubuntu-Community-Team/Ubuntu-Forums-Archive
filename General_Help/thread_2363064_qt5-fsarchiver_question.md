---
title: "qt5-fsarchiver question"
date: 2017-06-05
forum: General Help
---

### Post by ra7411 on 2017-06-05
I installed qt5-fsarchiver today and gave it a test run. It seemed to work ok, but the gui menu shows and allows backup of partitions on all 3 HDs I have on this machine, but only allows the backup to be saved to sda6 .

1) have I overlooked something that allows saving backups to any partition?
2) can an existing backup be moved to another partition without messing a restore operation?

---

### Post by monkeybrain20122 on 2017-06-05
1) It seems that you cannot save to the partitions where your current OS is. So in my screenshot Ubuntu 17.04 is in sda1(/)  and sda5(/home), it is  the OS where qt5-fsarchiver is installed and run from. So it can't save to those (sda6 is swap), but it can save to sda7 and sda8 on the same drive, and to sdb1, sdb5 and sdb6 (the three long names under media/myusername/) in an attached external drive.

2) yes.

BTW, fsarchiver is very easy to use, the command line version has more options than the qt gui (you can exclude directories with fsarchiver but apparently not with qt5-fsarchiver)

---

