---
title: "Problem installing Ubuntu."
date: 2015-09-28
forum: General Help
---

### Post by Tallorder64 on 2015-09-28
My old computer went up and I purchased a HP Pavillion with Windows10.  For the last 8 years I have had nothing Windows (shudder, shudder) on my computer.  To date, I have spent about 200 hours trying to install Ubuntu on my computer as my only OS.  I created another partisan (F) as some websites advised.  Ubuntu is installed in F but the computer refuses to recognize it.  I am about to give up.  I was and am quite happy with Ubuntu and I don't want anything Windows in my house. Does anyone have a solution to this?  I have owned a computer since 1984 (a 31 pound portable asbig as a suitcase with 256k and a six" screen so I am not new to computers or new to Ubuntu.  If I am having so much of a problem to install Ubuntu I wonder what a newby will run into.

---

### Post by yancek on 2015-09-28
> Ubuntu is installed in F but the computer refuses to recognize it

Linux does not use the drive/partition nomenclature from the 1970's that windows still does.  The link below explains this in some detail and has a tutorial on installing Ubuntu also.  You do need to create a separate partition with a Linux filesystem format.  You can't do that from windows, you can create the partition but not format as windows is not able to do that.  You can create a partition if there is unallocated space and format during the install of Ubuntu.  Not having any information on your drives/partitions limits suggestions.  I expect your windows 10 is using UEFI so you will need to install Ubuntu UEFI also.  

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

You will need to verify that you are or are not using UEFI, probably are.  Check the link below for some info or just do an online search for dual boot windows 10/ubuntu uefi.

[http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook)

---

### Post by grahammechanical on 2015-09-28
If you only want Ubuntu on that machine then simply select Erase disk and install Ubuntu at the Installation Type dialog

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

You will be surprised at the number of people who select that option and then get a surprise that Windows has been removed. But that is exactly what you want to do. 

Regards.

---

