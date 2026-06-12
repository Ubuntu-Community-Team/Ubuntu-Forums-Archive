---
title: "Grub Rescue Stops Reboot Every Time"
date: 2016-02-20
forum: General Help
---

### Post by Gremlin! on 2016-02-20
Active@KillDisk 10 is screwed up, won't work, and using Windows Manage/Storage/Delete Volume/Reformat is equally useless: I had Linux on a discrete physical volume, and later decided that I didn't need it screwing up my boot process every time...now, every time I reboot with that drive connected, Grub Rescue STOPS everything. It's not supposed to **_BE_** there! That disk was REFORMATTED, WIPED, KILLED...yet, it's still looking for a viable Linux operating system. How do I get RID of that stupid thing? Other than simply throwing the drive away on the trash heap.

---

### Post by yancek on 2016-02-20
Did you just format the various partitions?  Did you overwrite the master boot record, that is if you are using an MBR boot on whichever version of windows you are using?  It seems you still have code in the MBR and not partition with Grub.  The first link below explains how to backup/copy the MBR and the second explains deleting it.  As the warning says on the page, if you get the wrong device you will not be able to boot the other drive so read carefully before doing anything.

Also, if you have a newer windows (8 or 10) installed using UEFI, ignore this as it won't work.  You didn't post any info on which windows you are using.

[http://www.cyberciti.biz/faq/howto-copy-mbr/](http://www.cyberciti.biz/faq/howto-copy-mbr/)

[http://www.cyberciti.biz/faq/linux-clearing-out-master-boot-record-dd-command/](http://www.cyberciti.biz/faq/linux-clearing-out-master-boot-record-dd-command/)

---

### Post by ajgreeny on 2016-02-20
The best way may shown at [http://askubuntu.com/questions/131168/how-do-i-uninstall-grub](http://askubuntu.com/questions/131168/how-do-i-uninstall-grub)

However, tell us more in detail.

Is that disk a USB device?
When you installed Ubuntu(?) to it did you also ensure that grub was installed on the MBR of that disk?
Is the disk now completely empty (apart from grub, perhaps)?
Have you tried creating a new partition table on it with gparted or similar application?  I'm not sure if that removes what is on the first few bytes of the disk but it is worth a try.

---

