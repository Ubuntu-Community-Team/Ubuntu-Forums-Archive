---
title: "Clearing all system logs"
date: 2015-03-30
forum: General Help
---

### Post by lyf on 2015-03-30
Hi Experts,

How to clear all the system logs in the Ubuntu 14.04 ?

Like dmesg,/dev/kmsg, etc

Regards,
Lyf

---

### Post by dino99 on 2015-03-30
why such a wish ?
logs are usefull to know about warnings/errors and used by the system itself via whoopsie
and they are automatically rotated and compressed when needed

---

### Post by slickymaster on 2015-03-30
Hi lyf, welcome to the forums.

Can we ask you the reason why you'd want to clean all the logs?

Even though it is generally safe to delete log files, most of them are deleted automatically after being rotated by compression and renaming, and kept in that archived format.

You have to bare in mind that once you delete them, and if you need to troubleshoot some other problem later, you'll have nothing to recur to.

If you have logs that are growing faster than your system is able to delete them, then something very strange is happening, and it would be worthwhile to investigate that.

---

### Post by kerry_s on 2015-03-30
> **lyf said:**
> Hi Experts,

How to clear all the system logs in the Ubuntu 14.04 ?

Like dmesg,/dev/kmsg, etc

Regards,
Lyf


sudo rm -rf /var/log/*

i clean mine out all the time when i'm checking them, less logs to comb through. there created at every boot so you only have the logs that matter.

---

### Post by oldfred on 2015-03-30
This command just deletes the compressed ones.

 # empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

      
 RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by lyf on 2015-03-30
Hi All,

Thanks for the response.

For security reasons I don't want the system to be logged with any of my activity  in the PC.

It would be great if there are few provisions to stop the logs by all means.

Regards,
Lyf

---

### Post by kjohri on 2015-03-31
You can manage log files with [logrotate]("http://www.softprayog.in/tutorials/logrotate"). There are options like how often logs should be rotated (daily, weekly, monthly etc.). The "maxage count" option tells all logs older than "count" should be removed.

---

