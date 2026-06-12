---
title: "run script on (shutdown &amp;&amp; suspend )/(boot &amp;&amp; wakeup)"
date: 2012-11-09
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-11-09
i assume there is a way to use /etc/init.d/ and or /etc/rc.local
i want to run this at shutdown/suspend
```
backlightx --get current > /var/backlightx
```and i want to run this at boot/wakeup
```
if [ -f /var/log/backlightx ];then backlightx --set $(cat /var/log/backlightx);fi
```my laptop like to forget the brightness

also how to the brightness key work, i want to mod the command they run to, since however it does it, it does not show up in [FONT=Courier New]/sys/class/backlight/acpi_video0/brightness[/FONT]
[FONT=Courier New]backlightx --set +1[/FONT] and [FONT=Courier New]backlightx --set -1[/FONT] 
they keys do alter brightness, the file is just not updated, so i want to remap them to run the script

to thoes who end up here looking for a backlight fix here is a download link
[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1064117/+attachment/3388158/+files/backlightx.tar.bz2](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/1064117/+attachment/3388158/+files/backlightx.tar.bz2)
it is a script i made to act as a script friendly api for the backlight

Edit: running at suspend/resume/wake is not required, as long as [FONT=Courier New]/sys/class/backlight/acpi_video0/brightness[/FONT] is updated

---

