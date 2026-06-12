---
title: "gparted - Can't create new partition table on a pendrive"
date: 2014-09-06
forum: General Help
---

### Post by Ashfaqur Rahman on 2014-09-06
I have a 16GB transcend pendrive, suddenly which got a peculiar issue. Every time it became write protected after transferring 7GB to it. So I thought of reformatting it. When I tried to format It gparted freezed . I waited for sometimes but got no response. So I unplugged the pendrive.

Now gparted is showing the pendrive with 14.96GB of unallocated data. If I try to create new partition it says " **No partition table found on device /dev/sdd** ". OK, I tried to create a new **msdos** partition table. But the problem is it's showing an error saying " **Input/output error during write on /dev/sdd** "

Is there any way to recover this pendrive? ( At least it is still alive, showing its blue tiny light, even gparted can detect it! )

---

### Post by gedakc on 2014-09-08
The error message indicates a hardware problem.  If the device is securely plugged in, then it is possible that the device is beginning to fail.

You might try some actions with the device, and when an error occurs, open a terminal window and enter the **dmesg** command.  A search through the last few lines might provide additional insight into the problem.

---

