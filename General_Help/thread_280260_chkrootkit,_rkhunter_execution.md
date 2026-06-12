---
title: "chkrootkit, rkhunter execution"
date: 2006-10-19
forum: General Help
---

### Post by RikoW on 2006-10-19
dear all,

I installed chkrootkit and rkhunter from the Ubuntu repos. Naturally, I want them to be executed regularly and automatically. I saw, that corresponding scripts are placed in the /etc/cron.daily and cron.weekly directories, which are then run by the cron damon at the specified times just after 6 in the morning. 
Since all this is happening on a laptop, this machine is rarely on that early in the morning. Checking the /etc/anacrontab file, it seems to me (not being an expert in this) that the cron.daily etc scripts are executed by anacron also.

If I understand this nested calling structure of anacron and cron correctly, the chkrootkit and rkhunter scripts should be called every day the machine is running, right?

Thanks for a conformation or correction of my assumptions! :)

            Cheers,

                   Riko

---

### Post by PriceChild on 2006-10-19
I'm reasonably sure that if the machine isn't on when the cron should be run... it is run at the next availiable opportunity without waiting for its next slot.

---

### Post by Oceola on 2006-10-26
You should also be able to run both programs from a terminal
For Chkrootkit:
**sudo chkrootkit**
This should give you a read immediately and should be verbose in the terminal

For Rkhunter:
**sudo rkhunter -c --createlogfile --display-logfile**
This will also give you an immediate read.

Time calls can be configured in the /etc/cron.d/anacron file
use **sudo gedit /etc/cron.d/anacron**
This will open the file for edit
You can then modify the time configuration which by default would probably read 30 7 ..... you can change the 7 to a larger or smaller number to move when the programs are run.

You should read the anacron and cron stuff in Yelp
:D

---

### Post by floke on 2006-11-14
Ah! Was wondering where they disappeared to after download.
However - when running I received a warning to check the following:

 /dev/.static (directory)  /dev/.udev (directory)  /dev/.initramfs (directory) 

Can anyone tell me what this means? And how to check them?

Thanks,

Steve

---

### Post by ChristosG on 2008-02-17
> 
[22:29:59]   Checking for hidden files and directories       [ Warning ]
[22:29:59] Warning: Hidden directory found: /etc/.java
[22:29:59] Warning: Hidden directory found: /dev/.static
[22:29:59] Warning: Hidden directory found: /dev/.udev
[22:29:59] Warning: Hidden directory found: /dev/.initramfs
[22:30:00] Warning: Hidden file found: /dev/.tmp-2-0: block special (2/0)


after executing rkhunter. what is wrong?

---

### Post by ChristosG on 2008-02-17
anybody? :(

---

### Post by darkworld on 2008-02-19
my guess is that nothing is wrong.

This is my output:

> [08:46:02] Warning: Hidden directory found: /etc/.java
[08:46:02] Warning: Hidden directory found: /dev/.static
[08:46:02] Warning: Hidden directory found: /dev/.udev
[08:46:02] Warning: Hidden directory found: /dev/.initramfs
[08:46:02] Warning: Hidden file found: /dev/.tmp-2-0: block special (2/0)


Snap! :lolflag: I have a hunch nothing is wrong.

Check out the [http://sourceforge.net/docman/display_doc.php?docid=35179&group_id=155034]("http://sourceforge.net/docman/display_doc.php?docid=35179&group_id=155034")

Thats what im doing now. Let me know if you discover the answers first.

---

### Post by openheart on 2008-03-16
I noticed your post about the hidden file warning that rkhunter was providing.. I believe this may be due to some configuration files stored when you boot an os from a cd. They remind me of save files made by some knoppix or dsl installations I have done.. the file name suggests initializing a file system in ram .initramfs.. just wondering what you found out about it..

---

