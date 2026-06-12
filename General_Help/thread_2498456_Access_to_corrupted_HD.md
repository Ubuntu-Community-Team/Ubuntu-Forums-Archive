---
title: "Access to corrupted HD"
date: 2024-06-14
forum: General Help
---

### Post by mikeyphi2 on 2024-06-14
Hi, my normal Ubuntu 22.04.4 on a 1.5TB hard drive has some corruption whilst updating OS. All 7 partitions are unacessable
I've installed a copy of Ubuntu 22.04 on another HD which is OK.
I want to rescue the 1.5TB drive: Live Install doesn't see the Drive; GParted, on the new install, doesn't see the Drive (it's not listed in fstab)
However Disks sees the Drive as /dev/sb1 but can't Edit or Format (udisks error-quark)
Finally BIOS sees the Disk but returns an error when asked to take any action

Can I use some way to access the Drive to fschk or just reformat? Don't necessarily need the data as all is backed up.
Thanks in advance

---

### Post by ajgreeny on 2024-06-14
Have you tried running a filesystem check using **Disks**?

Click on the partition where your root partition is and then click the two small cog-wheel icon. You will see options to check the filesystem and also to repair the filesystem. I have never needed to do either of those and seldom use **Disks** for anything else preferring terminal so have no useful experience to pass on.

There will be warning messages shown about the long time taken to do this and also about backing up data first but if you can't even do that from a live system I'm not sure where to suggest you go.

---

### Post by oldfred on 2024-06-14
If you can see all 7 partitions you can run e2fsck on each partition.
But do not run on the drive.

Does testdisk shows partitions?

---

### Post by mikeyphi2 on 2024-06-14
Unfortunately Disks does not give the option to check/repair filesystem

---

### Post by mikeyphi2 on 2024-06-14
How do I do that? There is no way to mount the drive so I can't CD into it to action any commands

Please advise how to run e2fsck or testdisk.  The Disk app shows the partitions but only returns an u-disks error for available actions

---

### Post by oldfred on 2024-06-14
Does this show partitions?
sudo parted -l
If partitions shown:
man e2fsck
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdXY to your drive,partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters. If some other format, then you have to run the tools for that format.
sudo e2fsck -C0 -p -f -v /dev/sdXY 
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdXY
Where the XY is drive X and partition(s) y as shown with parted.

If not shown what does testdisk show. You need to know if gpt or old MBR(msdos).
Testdisk Instructions, new versions use sectors, old ones were CHS
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by mikeyphi2 on 2024-06-15
No joy with parted -l

testdisk doesn't appear to work, description says it's for ext2,ext3 -does it work on ext4?

---

### Post by oldfred on 2024-06-15
What version of testdisk.
I have used it years ago on ext4.

If drive damaged, you may want to test with Smart Status.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
In Disks alias gnome-disks you can click on icon in upper right corner and see Smart Status
[https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1](https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1)
or:
[https://ubuntuforums.org/showthread.php?t=2445397&p=13965854#post13965854](https://ubuntuforums.org/showthread.php?t=2445397&p=13965854#post13965854)
sudo apt-get install smartmontools

If drive broken, then only recourse is new drive & restore from backups.

---

### Post by mikeyphi2 on 2024-06-16
testdisk can't access the Drive and Smart status won't report.

Thanks for the advice I guess I'll just install a new Drive.

---

