---
title: "Ubuntu 14.04.1 LTS on Hyper-V"
date: 2014-11-08
forum: General Help
---

### Post by Aaron91234 on 2014-11-08
Hello.

I am having an issue where /etc/acpi/powerbtn.sh isn't being ran at all when pressing the Shutdown Button in hyper-v.  I already read this thread [http://ubuntuforums.org/showthread.php?t=2218671](http://ubuntuforums.org/showthread.php?t=2218671) about logind conflicting with powerbtn.sh, but this doesn't seem to be the problem.  I followed the steps and added HandlePowerKey=ignore to my /etc/systemd/logind.conf file, but the VERY first line in powerbtn.sh is echo testing >> /var/log/powerbtn.log and it doesn't ever run.

Any thoughts as to why this would be?

Thanks!

Aaron

---

