---
title: "getting a warning when i start to boot"
date: 2007-04-26
forum: General Help
---

### Post by linducky on 2007-04-26
Hey guys i was getting this after i installed 7.04 and then i went back to 6.06 and i'm getting it again...

when i boot when the system is checking all file systems i get a message that reads that my boot sector backup does not match the record present
IT LOOKS SOMETHING LIKE THIS:

offset: original/backup
67:0e/4b, 68:18a6 

where can i get the log to give the exact error and how can i stop this?

---

### Post by ubuntufan on 2007-05-09
I had the same problem, and I found a solution that worked for me at: [https://bugs.launchpad.net/ubuntu/+bug/47382](https://bugs.launchpad.net/ubuntu/+bug/47382)           I just had to change "hda1" to "sda1." I hope this helps if other people have the same problem.



"Don't worry.
There is a simply soltion to solve this "error"message.

Subject the system ist bootable and you can have acces to your ubuntu, just do the following :

In Ubuntu open a terminal window. become either root by typing su + root password or type

sudo dosfsck -r /dev/hda1

Once you try to run fsck in recovery mode, nothing will happen, whatever option you choose.
Obviously dosfsck will be invoked by fsck and when the options choices appear on the screen dosfsck is already terminated.
And fsck has no glue how to handle the typed in figures ( 1, 2 oder 3 (no action).

On the first run of dosfsck the same errormessage will appear and it offers the 3 options (copy backup to original, origianl to backup, no action)
Choose "copy original to backup" and - after an while - confirm the "perform changes" with y for yes.
Thats it. For a test you may feel free to run fsck or dosfsck again.
The message "there are differeces bettween boot sector and his backup"has gone, as well as the also printed offsets and difference bytes.

Reboot and the message has been dessappeared to.

I had the same little problem under Feisty and solved it that way."

---

