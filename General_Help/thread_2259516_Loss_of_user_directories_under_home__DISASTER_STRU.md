---
title: "Loss of user directories under /home  DISASTER STRUCK"
date: 2015-01-04
forum: General Help
---

### Post by cigtoxdoc on 2015-01-04
The user directories under /home/ suddenly disappeared this afternoon.  OS is Ubuntu 14.04 64-bit.  I discoverd this when I rebooted my laptop and found that the login would recyle each time I entered my password.  I got some semblance of order by creating a new user.  Basically users with user ids of 1000, 1001, and 1002 got wiped up and their directory names under /home/ removed.  However, TESTDISK 6.14 finds them.  Most of the files were not removed from the SSD and are showing in white-colored font.  My main data files were in separate partitions under /media .

Question 1:  What is the correct way to make the user name show up and their directories and filea reappear?

Question 2:  How does one go about putting together my Evolution e-mail database?  All folder or subfolders seem to be there although apparently TESTDISK will have to recover about thirty oof these.

SpiderOak backup service appears to have lost many of the files they were backing up.

John

---

### Post by cigtoxdoc on 2015-01-05
TESTDISK has recovered over 114,000 files from from my /home/myname folder and copied these to a 2 TB USB drive.  So do I make a new home/myname and copy the contents of the home/myname folder on the USB drive back to the PC?

John

---

### Post by Impavidus on 2015-01-05
Did you have a separate /home partition? Failure to mount the /home partition would give exactly your symptoms without any file really being gone. Fixing /etc/fstab and remounting it would fix the problem.

---

