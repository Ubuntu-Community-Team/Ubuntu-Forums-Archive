---
title: "Re-Use Hard Drive with bootable OS as 2nd drive for data only"
date: 2018-12-12
forum: General Help
---

### Post by macsociety on 2018-12-12
Been using Ubuntu since the version 12 or maybe 14 days.  Been always using the update feature and moving from 16.04 to 18.04 made my system very unstable.  Figured it was time to slap a new cheap 1TB drive into my PC and start fresh, but I would like to keep that older drive for all its data.

I am up and running on a new fresh OS now but have not reinstalled the 1st drive yet as I did not want to have any issues with new drive and its install.

Is there a way I can install the original drive back in and remove just the OS part so it does not try to boot and have access to all my data?

Or an easy way to make dual boot and select which hard drive OS to boot from?

Would prefer just having the old drive as data if I can do that.

TJ

---

### Post by Bashing-om on 2018-12-12
macsociety; Hello -

Sure ! There are many options to consider what best meets your needs.

Dual booting:
my present system of 2 drives enabled:
> 
sysop@x1804mini:~$ sudo blkid
/dev/sda1: LABEL="x1604" UUID="d9c2a8e6-d014-42a6-846f-7e7892f4aef5" TYPE="ext4" PARTUUID="b6a9f0ca-01"
/dev/sda5: UUID="8d4743bc-8e47-4650-b5fd-1ea904d4ecda" TYPE="swap" PARTUUID="b6a9f0ca-05"
/dev/sda6: LABEL="x1904" UUID="49de038e-9807-469b-9009-540f2989f913" TYPE="ext4" PARTUUID="b6a9f0ca-06"
/dev/sdb1: LABEL="x1804root" UUID="1460de17-30e4-4566-b181-18c17b62887a" TYPE="ext4" PARTUUID="c6c4079f-01"
/dev/sdb2: LABEL="x1804home" UUID="5cd50446-1330-4130-a521-1ea936c9fc2a" TYPE="ext4" PARTUUID="c6c4079f-02"
/dev/sdb3: LABEL="x1804var" UUID="69b1f02a-5e00-415e-ab75-78fdd63f72a3" TYPE="ext4" PARTUUID="c6c4079f-03"
/dev/sdb5: LABEL="u1804" UUID="0b89d785-9ba8-4bd5-a41a-43462459c230" TYPE="ext4" PARTUUID="c6c4079f-05"
/dev/sdb6: LABEL="bups" UUID="a0c6dc1f-51d3-4824-b770-ce42d777277a" TYPE="ext4" PARTUUID="c6c4079f-06"
/dev/sdb7: LABEL="data" UUID="fe9cee2e-6812-46e1-b0a0-b03d5094763a" TYPE="ext4" PARTUUID="c6c4079f-07"
sysop@x1804mini:~$


Now note that I have 2 partitions set up for for storage -  bups and data -. You might consider this  for your use case.

Create the new partition(s), and copy the data you want to keep - and then delete the partitions containing the old operating system. Depending on how adventuresome you are, might be good however to keep a backup bootable system . 

Me I highly value my data, and I do maintain 3 backups of my personal files. Additional to my paranoia I only mount these "data' partitions as on-demand - your use case may vary and the system supports mounting partitions upon booting.

[INDENT][INDENT]all in what you want to do
[/INDENT][/INDENT]

---

### Post by yancek on 2018-12-12
Verify in your BIOS that the current drive with the new OS is set to first boot priority.  When it is, attach the second (old) drive and boot the new system.  You can then get info on the old drive or maybe you already know which partitions are data and which are the old OS.  After booting the new system with the old drive attached, if you have an OS on the old drive run:  sudo update-grub from the new drive and you should see an entry in the output for the old drive OS.

---

### Post by CatKiller on 2018-12-12
> **yancek said:**
> Verify in your BIOS that the current drive with the new OS is set to first boot priority.  When it is, attach the second (old) drive and boot the new system.  You can then get info on the old drive or maybe you already know which partitions are data and which are the old OS.  After booting the new system with the old drive attached, if you have an OS on the old drive run:  sudo update-grub from the new drive and you should see an entry in the output for the old drive OS.

I believe the OP specifically *doesn't* want an entry in the GRUB menu for the old drive as a preferred outcome. Just have it be dumb storage.

---

### Post by Autodave on 2018-12-12
Remove the drive with 16.04 on it.  Install new drive and install 18.04 on it.  Now, install old drive.  It will appear as an icon.  Mount it and then you will able to get to all your files on there.

---

### Post by yancek on 2018-12-12
> I believe the OP specifically *doesn't* want an entry in the GRUB menu for the old drive as a preferred outcome.

My thoughts when I first read the post but the statement quoted below from his original post makes it unclear.

> Or an easy way to make dual boot and select which hard drive OS to boot from?

---

### Post by missmoondog on 2018-12-13
> **Autodave said:**
> Remove the drive with 16.04 on it.  Install new drive and install 18.04 on it.  Now, install old drive.  It will appear as an icon.  Mount it and then you will able to get to all your files on there.


yep, simple as that! all done. no boot menu or grub or anything like that showing up. just use 2nd drive as storage.

if need be, just back up stuff on 2nd drive to 1st drive, format second drive and put backed up stuff back on 2nd drive.

---

### Post by oldfred on 2018-12-14
I like to have an install of Ubuntu on every device including larger flash drives which I use for backup. On flash drive I keep / smaller as I will not be adding a lot of software, mostly some repair or configuration applications.

But then I turn off os-prober so it does not find my other installs. I also now have some obsolete ones on my sdb drive that I will eventually overwrite, but do not want them in my grub menu. So I only add to 40_custom the versions of Ubuntu that I want to boot.

       sudo -H gedit /etc/default/grub:
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

