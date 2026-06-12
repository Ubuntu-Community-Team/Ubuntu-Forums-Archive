---
title: "Hard disk smart check"
date: 2013-02-14
forum: General Help
---

### Post by bibi1213 on 2013-02-14
Hi all,

Thanks for the advice on the SMART HDD health checker! I got this out put after running the long check:

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%       611         269776520

------------------------------------
But what does it mean? I don't even understand whether it finished the test or not. Is it completed or 90% ready? Did it fail? And if so what was wrong?

Thanks again for all your help.

BB.

---

### Post by Bufeu on 2013-02-14
[http://askubuntu.com/questions/20180/hard-disk-failure-error-on-smart-status-how-can-i-fix-it](http://askubuntu.com/questions/20180/hard-disk-failure-error-on-smart-status-how-can-i-fix-it)

---

### Post by tgalati4 on 2013-02-14
Your hard disk experienced a read error at 611 hours of use (new drive) at the 90% section of the drive, which is logical block address (LBA) 269776520.

What to do about it?  Back up your data and run a long test. Shut down all applications.  Review your disk drive assignments--write them down!

```
sudo fdisk -l
sudo smartctl -t long /dev/sda
```

Review the results after the time indicated (could be 1-2 hours):

```
sudo smartctl -a /dev/sda
sudo badblocks /dev/sda5
```

Cut and paste the list of badblocks that you find and compare the list over time.  Be sure to use the correct drive and partition from your fdisk command above.

If badblocks are found, then mark them in software, so that they are not used again:

```
sudo fsck -cc /dev/sda5
```

Drives that have a history of increasing badblocks are prone to failure.  Some badblocks are OK for large drives.  Most folks have a fit if their drive has one badblock.  Mark your calendar and perform either the *short* or *long* test every few months.

---

### Post by oldos2er on 2013-02-14
Posts moved to their own thread.

---

