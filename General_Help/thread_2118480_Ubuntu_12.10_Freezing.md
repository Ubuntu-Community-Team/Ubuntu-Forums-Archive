---
title: "Ubuntu 12.10 Freezing"
date: 2013-02-21
forum: General Help
---

### Post by ohcheezburgers on 2013-02-21
First time Linux user, Using 12.10 on a HP NC6400 laptop. I am experiencing a complete lockup of the system in which the only way to recover is to power off the system. I can't establish any kind of pattern, it just happens, when the computer is idle, when I'm using eclipse, when I'm browsing the internet, etc. It can also not happen for days and then lock up three times in 5 minutes. So far I've tried 32bit and 64bit versions of 12.10 and 12.04, I've tried upgrading the kernel from 3.5 in sequential order up to 3.8. Thought I had fixed it at 3.8 as it worked for around 5 days but has now just locked up several times.

How can I get to the bottom of this?

[http://h10010.www1.hp.com/wwpc/ca/en/sm/WF06b/12139188-12139280-12139280-12139280-12434660-12401288-77983407.html?dnr=1](http://h10010.www1.hp.com/wwpc/ca/en/sm/WF06b/12139188-12139280-12139280-12139280-12434660-12401288-77983407.html?dnr=1)

---

### Post by TheFu on 2013-02-21
> **ohcheezburgers said:**
> First time Linux user, Using 12.10 on a HP NC6400 laptop. I am experiencing a complete lockup of the system in which the only way to recover is to power off the system. I can't establish any kind of pattern, it just happens, when the computer is idle, when I'm using eclipse, when I'm browsing the internet, etc. It can also not happen for days and then lock up three times in 5 minutes. So far I've tried 32bit and 64bit versions of 12.10 and 12.04, I've tried upgrading the kernel from 3.5 in sequential order up to 3.8. Thought I had fixed it at 3.8 as it worked for around 5 days but has now just locked up several times.

How can I get to the bottom of this?

[http://h10010.www1.hp.com/wwpc/ca/en/sm/WF06b/12139188-12139280-12139280-12139280-12434660-12401288-77983407.html?dnr=1](http://h10010.www1.hp.com/wwpc/ca/en/sm/WF06b/12139188-12139280-12139280-12139280-12434660-12401288-77983407.html?dnr=1)

What do the log files show? Any errors or warnings?  [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

IMHO, 12.10 is not stable enough for new users.  12.04 LTS is the best answer unless some specific feature only in 12.10 is required - like secure boot.

After a crash, boot using a liveCD/live-Flash and mount which ever partition contains /var/log. Inside there are the log files that have what we need. Find the warnings and errors, then use those to help figure out what the issue is.  If there isn't anything in the logs - start suspecting hardware failures of some type - heating, power supply, GPU and failing RAM.  The heating issue is often a problem on laptops.

---

### Post by ohcheezburgers on 2013-02-21
Great stuff :-), will check the log when I get home. Memtested the life out of it, SuperPied it too, showing no errors, checked temps too; idling at mid-50's never goes over 75 when under heavy use.

---

### Post by ohcheezburgers on 2013-02-23
Hello here is the output, there does seem to be a theme.

```
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 on...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
/var/log/syslog:Feb 23 14:00:15 luke-HP-Compaq-nc6400-RM100AW-ABU kernel: [   14.951865] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/syslog:Feb 23 14:00:15 luke-HP-Compaq-nc6400-RM100AW-ABU kernel: [   15.815537] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \_SB_.C002.C003.C0BA 1 (20121018/utaddress-251)
/var/log/syslog:Feb 23 14:00:15 luke-HP-Compaq-nc6400-RM100AW-ABU kernel: [   15.815553] ACPI Warning: 0x00001130-0x0000113f SystemIO conflicts with Region \_SB_.C002.C003.C0CC 1 (20121018/utaddress-251)
/var/log/syslog:Feb 23 14:00:15 luke-HP-Compaq-nc6400-RM100AW-ABU kernel: [   15.815561] ACPI Warning: 0x00001100-0x0000112f SystemIO conflicts with Region \_SB_.C002.C003.C0CC 1 (20121018/utaddress-251)
/var/log/syslog:Feb 23 14:00:33 luke-HP-Compaq-nc6400-RM100AW-ABU NetworkManager[1069]: <error> [1361628033.697590] [nm-dns-dnsmasq.c:390] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:Feb 23 14:00:33 luke-HP-Compaq-nc6400-RM100AW-ABU NetworkManager[1069]: <error> [1361628033.697632] [nm-dns-dnsmasq.c:392] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
/var/log/syslog:Feb 23 14:00:34 luke-HP-Compaq-nc6400-RM100AW-ABU dnsmasq[1391]: warning: no upstream servers configured
/var/log/syslog:Feb 23 14:00:37 luke-HP-Compaq-nc6400-RM100AW-ABU gdm-simple-slave[1281]: WARNING: Failed to give slave programs access to the display. Trying to proceed.
/var/log/syslog:Feb 23 14:01:08 luke-HP-Compaq-nc6400-RM100AW-ABU gdm-simple-slave[1281]: WARNING: Failed to remove slave program access to the display. Trying to proceed.
/var/log/syslog:Feb 23 14:01:16 luke-HP-Compaq-nc6400-RM100AW-ABU gnome-session[2034]: WARNING: Failed to start app: Unable to start application: Failed to execute child process "gm-notify" (No such file or directory)
/var/log/Xorg.0.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.1.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.2.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.3.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.4.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/Xorg.5.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

```

---

### Post by TheFu on 2013-02-23
The wireless is unlikely to be the issue. Forget about that.  Plug in the laptop using CAT5 ethernet.  The kernel stuff is interesting. What did google say about those messages?

The X/Windows errors could make a desktop OS appear to be locked up, when it is just the GUI with issues.  Can you remote in from a different machine?  This may just be a GUI lock up, not a whole machine lock up. That differentiation is critical.

---

### Post by ohcheezburgers on 2013-02-23
I think you may be right as the laptop spends a significant amount of time plugged into ethernet and the problem still persists. However the wireless adapter is not disabled during this time so I can't completely rule it out, I'll disable it and see if it freezes just to make sure.
 
Google surprisingly doesn't bring any info transposable to my situation. I'll try your suggestion and go from there.

---

### Post by alexfish on 2013-02-23
> **ohcheezburgers said:**
> First time Linux user, Using 12.10 on a HP NC6400 laptop. I am experiencing a complete lockup of the system in which the only way to recover is to power off the system. I can't establish any kind of pattern, it just happens, when the computer is idle, when I'm using eclipse, when I'm browsing the internet, etc. It can also not happen for days and then lock up three times in 5 minutes. So far I've tried 32bit and 64bit versions of 12.10 and 12.04, I've tried upgrading the kernel from 3.5 in sequential order up to 3.8. Thought I had fixed it at 3.8 as it worked for around 5 days but has now just locked up several times.

How can I get to the bottom of this?

[http://h10010.www1.hp.com/wwpc/ca/en/sm/WF06b/12139188-12139280-12139280-12139280-12434660-12401288-77983407.html?dnr=1](http://h10010.www1.hp.com/wwpc/ca/en/sm/WF06b/12139188-12139280-12139280-12139280-12434660-12401288-77983407.html?dnr=1)


Have you been downloading files , or saving any specific files , prior to these lock ups


BR

Alex

---

### Post by ohcheezburgers on 2013-02-24
Not downloading any files prior to lockup. I can't pin the crashes to any particular behaviour. Sometimes I can be coding in eclipse and it will lock up constantly and then coding the same project it will be fine for 5 days or more. It seems to be unrepeatable.

---

### Post by alexfish on 2013-02-24
can have a look at where these coding files are saved , use the file browser

see if there are any files locking up , there will be a watch face over the file , showing still active, also if this be the case then the file browser may also freeze , in which case will have to open the file with the application or gedit  , sometimes drastic action is necessary , IE deleting some or all of the contents to break the link,

Thought I would mention this , as  it be a problem I had came across , Strange as it may seem ,this happened  whilst coding or saving graphics files / or Links. 

can also keep the update manager out of the way  whilst coding.

other than that I can't help.

Alex

---

### Post by TheFu on 2013-02-24
> **ohcheezburgers said:**
> Not downloading any files prior to lockup. I can't pin the crashes to any particular behaviour. Sometimes I can be coding in eclipse and it will lock up constantly and then coding the same project it will be fine for 5 days or more. It seems to be unrepeatable.

There is the answer - Eclipse.  Eclipse can make the beefiest computer drop to the knees and beg for help.

Did you try remote login to the system after a perceived lock up? 
Every time I've seen this, it was just the GUI, not the OS, that stopped responding.  A complicated GUI like Eclipse running under slow-poke Java would have that visual effect too.

There are also certain network cards that will lock up if certain, highly odd, packets traverse them in a specific order.   Sorry I can't find the reference link.  The card model is a 82574L - certain SIP hardware is known to cause this issue on the network. It is very repeatable.

Found it! [https://isc.sans.edu/diary/Intel+Network+Card+82574L+Packet+of+Death/15109](https://isc.sans.edu/diary/Intel+Network+Card+82574L+Packet+of+Death/15109)

---

### Post by ohcheezburgers on 2013-02-24
I can say with confidence that it's not eclipse. It will lock up just being on the desktop with no open programs. Nice find on the bug! I will try to SSH into it but it still hasn't locked up yet, which is unusual.

---

### Post by ohcheezburgers on 2013-02-24
It's a total lock up, I can't SSH into it.

---

### Post by TheFu on 2013-02-24
> **ohcheezburgers said:**
> It's a total lock up, I can't SSH into it.

Ok, power it off, boot up off different media - like a LIVECD - and look at the log files after you mount the /var partition on the HDD.  Any different errors or warnings?  We don't need to see 20-500 of the same messages.

Ignore the wifi-related ones.

Those will be the only leads for a solution.

---

### Post by ohcheezburgers on 2013-02-27
Ok so booted with a liveCD and /var mounted I get this 

```

auth.log:Feb 27 19:42:55 ubuntu sudo:   ubuntu : TTY=pts/1 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
auth.log:Feb 27 19:53:18 ubuntu sudo:   ubuntu : TTY=pts/6 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
boot.log:/usr/lib/python2.7/dist-packages/LanguageSelector/LocaleInfo.py:256: UserWarning: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
boot.log:  warnings.warn(msg.args[0].encode('UTF-8'))
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4 package 'dpkg':
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4 package 'dpkg':
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4 package 'dpkg':
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 53 package 'dpkg':
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 53 package 'dpkg':
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 53 package 'dpkg':
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
casper.log:/usr/lib/python2.7/dist-packages/LanguageSelector/LocaleInfo.py:256: UserWarning: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
casper.log:  warnings.warn(msg.args[0].encode('UTF-8'))
jockey.log:2013-02-27 19:41:11,538 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl
jockey.log:2013-02-27 19:41:11,567 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx
jockey.log:2013-02-27 19:41:11,746 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates
jockey.log:2013-02-27 19:41:11,759 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9
jockey.log:2013-02-27 19:41:11,788 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
jockey.log:2013-02-27 19:41:11,800 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci
jockey.log:2013-02-27 19:41:11,819 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96
jockey.log:2013-02-27 19:41:11,830 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current
jockey.log:2013-02-27 19:41:11,842 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates
jockey.log:2013-02-27 19:41:11,857 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates
jockey.log:2013-02-27 19:41:11,875 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates
jockey.log:2013-02-27 19:41:11,888 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173
jockey.log:2013-02-27 19:41:11,900 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310
jockey.log:2013-02-27 19:41:11,936 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304
jockey.log:2013-02-27 19:41:12,201 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr
jockey.log:2013-02-27 19:41:12,685 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet
jockey.log:Warning: The home dir /var/log/slmodemd you specified can't be accessed: No such file or directory
kern.log:Feb 27 19:36:39 ubuntu kernel: [  115.397397] ACPI Warning: 0x0000000000001060-0x000000000000107f SystemIO conflicts with Region \_SB_.C002.C003.C0C4 1 (20120320/utaddress-251)
kern.log:Feb 27 19:36:39 ubuntu kernel: [  115.397414] ACPI Warning: 0x0000000000001028-0x000000000000102f SystemIO conflicts with Region \_SB_.C002.C003.C0BA 1 (20120320/utaddress-251)
kern.log:Feb 27 19:36:39 ubuntu kernel: [  115.397424] ACPI Warning: 0x0000000000001100-0x000000000000113f SystemIO conflicts with Region \_SB_.C002.C003.C0CC 1 (20120320/utaddress-251)
syslog:Feb 27 19:36:39 ubuntu kernel: [  115.397397] ACPI Warning: 0x0000000000001060-0x000000000000107f SystemIO conflicts with Region \_SB_.C002.C003.C0C4 1 (20120320/utaddress-251)
syslog:Feb 27 19:36:39 ubuntu kernel: [  115.397414] ACPI Warning: 0x0000000000001028-0x000000000000102f SystemIO conflicts with Region \_SB_.C002.C003.C0BA 1 (20120320/utaddress-251)
syslog:Feb 27 19:36:39 ubuntu kernel: [  115.397424] ACPI Warning: 0x0000000000001100-0x000000000000113f SystemIO conflicts with Region \_SB_.C002.C003.C0CC 1 (20120320/utaddress-251)
Xorg.0.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
ubuntu@ubuntu:/var/log$ sudo grep -i 'warning|error' *log
auth.log:Feb 27 19:54:14 ubuntu sudo:   ubuntu : TTY=pts/6 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning|error alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
ubuntu@ubuntu:/var/log$ sudo grep -i 'warning | error' *log
auth.log:Feb 27 19:54:24 ubuntu sudo:   ubuntu : TTY=pts/6 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning | error alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
ubuntu@ubuntu:/var/log$ sudo grep -i 'warning' *log
auth.log:Feb 27 19:42:55 ubuntu sudo:   ubuntu : TTY=pts/1 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
auth.log:Feb 27 19:53:18 ubuntu sudo:   ubuntu : TTY=pts/6 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
auth.log:Feb 27 19:54:14 ubuntu sudo:   ubuntu : TTY=pts/6 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning|error alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
auth.log:Feb 27 19:54:24 ubuntu sudo:   ubuntu : TTY=pts/6 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning | error alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
auth.log:Feb 27 19:54:31 ubuntu sudo:   ubuntu : TTY=pts/6 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
boot.log:/usr/lib/python2.7/dist-packages/LanguageSelector/LocaleInfo.py:256: UserWarning: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
boot.log:  warnings.warn(msg.args[0].encode('UTF-8'))
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4 package 'dpkg':
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4 package 'dpkg':
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4 package 'dpkg':
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 53 package 'dpkg':
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 53 package 'dpkg':
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 53 package 'dpkg':
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
casper.log:/usr/lib/python2.7/dist-packages/LanguageSelector/LocaleInfo.py:256: UserWarning: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
casper.log:  warnings.warn(msg.args[0].encode('UTF-8'))
jockey.log:2013-02-27 19:41:11,538 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl
jockey.log:2013-02-27 19:41:11,567 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx
jockey.log:2013-02-27 19:41:11,746 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates
jockey.log:2013-02-27 19:41:11,759 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9
jockey.log:2013-02-27 19:41:11,788 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
jockey.log:2013-02-27 19:41:11,800 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci
jockey.log:2013-02-27 19:41:11,819 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96
jockey.log:2013-02-27 19:41:11,830 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current
jockey.log:2013-02-27 19:41:11,842 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates
jockey.log:2013-02-27 19:41:11,857 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates
jockey.log:2013-02-27 19:41:11,875 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates
jockey.log:2013-02-27 19:41:11,888 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173
jockey.log:2013-02-27 19:41:11,900 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310
jockey.log:2013-02-27 19:41:11,936 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304
jockey.log:2013-02-27 19:41:12,201 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr
jockey.log:2013-02-27 19:41:12,685 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet
jockey.log:Warning: The home dir /var/log/slmodemd you specified can't be accessed: No such file or directory
kern.log:Feb 27 19:36:39 ubuntu kernel: [  115.397397] ACPI Warning: 0x0000000000001060-0x000000000000107f SystemIO conflicts with Region \_SB_.C002.C003.C0C4 1 (20120320/utaddress-251)
kern.log:Feb 27 19:36:39 ubuntu kernel: [  115.397414] ACPI Warning: 0x0000000000001028-0x000000000000102f SystemIO conflicts with Region \_SB_.C002.C003.C0BA 1 (20120320/utaddress-251)
kern.log:Feb 27 19:36:39 ubuntu kernel: [  115.397424] ACPI Warning: 0x0000000000001100-0x000000000000113f SystemIO conflicts with Region \_SB_.C002.C003.C0CC 1 (20120320/utaddress-251)
syslog:Feb 27 19:36:39 ubuntu kernel: [  115.397397] ACPI Warning: 0x0000000000001060-0x000000000000107f SystemIO conflicts with Region \_SB_.C002.C003.C0C4 1 (20120320/utaddress-251)
syslog:Feb 27 19:36:39 ubuntu kernel: [  115.397414] ACPI Warning: 0x0000000000001028-0x000000000000102f SystemIO conflicts with Region \_SB_.C002.C003.C0BA 1 (20120320/utaddress-251)
syslog:Feb 27 19:36:39 ubuntu kernel: [  115.397424] ACPI Warning: 0x0000000000001100-0x000000000000113f SystemIO conflicts with Region \_SB_.C002.C003.C0CC 1 (20120320/utaddress-251)
Xorg.0.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
ubuntu@ubuntu:/var/log$ clear

ubuntu@ubuntu:/var/log$ sudo grep -i 'warning' *log
auth.log:Feb 27 19:42:55 ubuntu sudo:   ubuntu : TTY=pts/1 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
auth.log:Feb 27 19:53:18 ubuntu sudo:   ubuntu : TTY=pts/6 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
auth.log:Feb 27 19:54:14 ubuntu sudo:   ubuntu : TTY=pts/6 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning|error alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
auth.log:Feb 27 19:54:24 ubuntu sudo:   ubuntu : TTY=pts/6 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning | error alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
auth.log:Feb 27 19:54:31 ubuntu sudo:   ubuntu : TTY=pts/6 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
auth.log:Feb 27 19:54:56 ubuntu sudo:   ubuntu : TTY=pts/6 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
boot.log:/usr/lib/python2.7/dist-packages/LanguageSelector/LocaleInfo.py:256: UserWarning: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
boot.log:  warnings.warn(msg.args[0].encode('UTF-8'))
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4 package 'dpkg':
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4 package 'dpkg':
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 4 package 'dpkg':
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 53 package 'dpkg':
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 53 package 'dpkg':
bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 53 package 'dpkg':
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
bootstrap.log:dpkg: warning: ignoring pre-dependency problem!
casper.log:/usr/lib/python2.7/dist-packages/LanguageSelector/LocaleInfo.py:256: UserWarning: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
casper.log:  warnings.warn(msg.args[0].encode('UTF-8'))
jockey.log:2013-02-27 19:41:11,538 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl
jockey.log:2013-02-27 19:41:11,567 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx
jockey.log:2013-02-27 19:41:11,746 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates
jockey.log:2013-02-27 19:41:11,759 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9
jockey.log:2013-02-27 19:41:11,788 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
jockey.log:2013-02-27 19:41:11,800 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci
jockey.log:2013-02-27 19:41:11,819 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96
jockey.log:2013-02-27 19:41:11,830 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current
jockey.log:2013-02-27 19:41:11,842 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates
jockey.log:2013-02-27 19:41:11,857 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates
jockey.log:2013-02-27 19:41:11,875 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates
jockey.log:2013-02-27 19:41:11,888 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173
jockey.log:2013-02-27 19:41:11,900 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310
jockey.log:2013-02-27 19:41:11,936 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304
jockey.log:2013-02-27 19:41:12,201 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr
jockey.log:2013-02-27 19:41:12,685 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet
jockey.log:Warning: The home dir /var/log/slmodemd you specified can't be accessed: No such file or directory
kern.log:Feb 27 19:36:39 ubuntu kernel: [  115.397397] ACPI Warning: 0x0000000000001060-0x000000000000107f SystemIO conflicts with Region \_SB_.C002.C003.C0C4 1 (20120320/utaddress-251)
kern.log:Feb 27 19:36:39 ubuntu kernel: [  115.397414] ACPI Warning: 0x0000000000001028-0x000000000000102f SystemIO conflicts with Region \_SB_.C002.C003.C0BA 1 (20120320/utaddress-251)
kern.log:Feb 27 19:36:39 ubuntu kernel: [  115.397424] ACPI Warning: 0x0000000000001100-0x000000000000113f SystemIO conflicts with Region \_SB_.C002.C003.C0CC 1 (20120320/utaddress-251)
syslog:Feb 27 19:36:39 ubuntu kernel: [  115.397397] ACPI Warning: 0x0000000000001060-0x000000000000107f SystemIO conflicts with Region \_SB_.C002.C003.C0C4 1 (20120320/utaddress-251)
syslog:Feb 27 19:36:39 ubuntu kernel: [  115.397414] ACPI Warning: 0x0000000000001028-0x000000000000102f SystemIO conflicts with Region \_SB_.C002.C003.C0BA 1 (20120320/utaddress-251)
syslog:Feb 27 19:36:39 ubuntu kernel: [  115.397424] ACPI Warning: 0x0000000000001100-0x000000000000113f SystemIO conflicts with Region \_SB_.C002.C003.C0CC 1 (20120320/utaddress-251)
Xorg.0.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
ubuntu@ubuntu:~$ cd mnt
ubuntu@ubuntu:~/mnt$ cd /var
ubuntu@ubuntu:/var$ cd /log
bash: cd: /log: No such file or directory
ubuntu@ubuntu:/var$ ls
backups  cache  crash  games  lib  local  lock  log  mail  opt  run  spool  tmp
ubuntu@ubuntu:/var$ cd /log
bash: cd: /log: No such file or directory
ubuntu@ubuntu:/var$ cd log
ubuntu@ubuntu:/var/log$ ls
alternatives.log  dist-upgrade    kern.log           syslog
apt               dmesg           lastlog            udev
auth.log          dmesg.0         lightdm            ufw.log
boot              dpkg.log        mail.err           unattended-upgrades
boot.log          faillog         mail.log           upstart
bootstrap.log     fontconfig.log  news               wtmp
btmp              fsck            pm-powersave.log   Xorg.0.log
casper.log        hp              samba              Xorg.0.log.old
ConsoleKit        installer       slmodemd
cups              jockey.log      speech-dispatcher
ubuntu@ubuntu:/var/log$ sudo gre p 'error' 
sudo: gre: command not found
ubuntu@ubuntu:/var/log$ sudo grep -i 'error' *log 
auth.log:Feb 27 19:40:38 ubuntu dbus[1330]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.70" (uid=999 pid=5422 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.12" (uid=0 pid=2082 comm="/usr/sbin/console-kit-daemon --no-daemon ")
auth.log:Feb 27 19:43:55 ubuntu sudo:   ubuntu : TTY=pts/1 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i error alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
auth.log:Feb 27 19:45:08 ubuntu dbus[1330]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.2" (uid=0 pid=1345 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.82" (uid=999 pid=5275 comm="bluetooth-applet ")
auth.log:Feb 27 19:54:14 ubuntu sudo:   ubuntu : TTY=pts/6 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning|error alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
auth.log:Feb 27 19:54:24 ubuntu sudo:   ubuntu : TTY=pts/6 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i warning | error alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
auth.log:Feb 27 20:01:16 ubuntu sudo:   ubuntu : TTY=pts/1 ; PWD=/var/log ; USER=root ; COMMAND=/bin/grep -i error alternatives.log auth.log boot.log bootstrap.log casper.log dpkg.log faillog fontconfig.log jockey.log kern.log lastlog mail.log pm-powersave.log syslog ufw.log Xorg.0.log
boot.log:stdin: error 0
bootstrap.log:update-rc.d: error: insserv rejected the script header
casper.log:stdin: error 0
dpkg.log:2013-02-13 22:08:07 install libgpg-error0 <none> 1.10-2ubuntu1
dpkg.log:2013-02-13 22:08:07 status half-installed libgpg-error0 1.10-2ubuntu1
dpkg.log:2013-02-13 22:08:07 status unpacked libgpg-error0 1.10-2ubuntu1
dpkg.log:2013-02-13 22:08:07 status unpacked libgpg-error0 1.10-2ubuntu1
dpkg.log:2013-02-13 22:09:31 configure libgpg-error0 1.10-2ubuntu1 <none>
dpkg.log:2013-02-13 22:09:31 status unpacked libgpg-error0 1.10-2ubuntu1
dpkg.log:2013-02-13 22:09:31 status half-configured libgpg-error0 1.10-2ubuntu1
dpkg.log:2013-02-13 22:09:31 status installed libgpg-error0 1.10-2ubuntu1
jockey.log:2013-02-27 19:41:11,538 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl
jockey.log:2013-02-27 19:41:11,567 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx
jockey.log:    raise ValueError('package %s does not exist' % package)
jockey.log:ValueError: package linux-firmware-nonfree does not exist
jockey.log:2013-02-27 19:41:11,746 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates
jockey.log:2013-02-27 19:41:11,759 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9
jockey.log:    raise ValueError('package %s does not exist' % package)
jockey.log:ValueError: package fglrx-experimental-9 does not exist
jockey.log:2013-02-27 19:41:11,788 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
jockey.log:2013-02-27 19:41:11,800 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci
jockey.log:2013-02-27 19:41:11,819 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96
jockey.log:2013-02-27 19:41:11,830 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current
jockey.log:2013-02-27 19:41:11,842 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates
jockey.log:2013-02-27 19:41:11,857 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates
jockey.log:2013-02-27 19:41:11,875 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates
jockey.log:2013-02-27 19:41:11,888 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173
jockey.log:2013-02-27 19:41:11,900 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310
jockey.log:    raise ValueError('package %s does not exist' % package)
jockey.log:ValueError: package nvidia-experimental-310 does not exist
jockey.log:2013-02-27 19:41:11,936 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304
jockey.log:    raise ValueError('package %s does not exist' % package)
jockey.log:ValueError: package nvidia-experimental-304 does not exist
jockey.log:2013-02-27 19:41:12,201 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr
jockey.log:2013-02-27 19:41:12,685 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet
kern.log:Feb 27 19:48:45 ubuntu kernel: [  842.739282] Sense Key : Medium Error [current] 
kern.log:Feb 27 19:48:45 ubuntu kernel: [  842.739321] end_request: I/O error, dev sr0, sector 192400
kern.log:Feb 27 19:52:01 ubuntu kernel: [ 1038.168096] Sense Key : Medium Error [current] 
kern.log:Feb 27 19:52:01 ubuntu kernel: [ 1038.168136] end_request: I/O error, dev sr0, sector 1139576
kern.log:Feb 27 19:53:54 ubuntu kernel: [ 1151.451185] Sense Key : Medium Error [current] 
kern.log:Feb 27 19:53:54 ubuntu kernel: [ 1151.451225] end_request: I/O error, dev sr0, sector 1050984
kern.log:Feb 27 19:56:25 ubuntu kernel: [ 1302.583141] Sense Key : Medium Error [current] 
kern.log:Feb 27 19:56:25 ubuntu kernel: [ 1302.583180] end_request: I/O error, dev sr0, sector 1125040
pm-powersave.log:Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
syslog:Feb 27 19:41:38 ubuntu NetworkManager[1754]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
syslog:Feb 27 19:48:45 ubuntu kernel: [  842.739282] Sense Key : Medium Error [current] 
syslog:Feb 27 19:48:45 ubuntu kernel: [  842.739321] end_request: I/O error, dev sr0, sector 192400
syslog:Feb 27 19:52:01 ubuntu kernel: [ 1038.168096] Sense Key : Medium Error [current] 
syslog:Feb 27 19:52:01 ubuntu kernel: [ 1038.168136] end_request: I/O error, dev sr0, sector 1139576
syslog:Feb 27 19:53:54 ubuntu kernel: [ 1151.451185] Sense Key : Medium Error [current] 
syslog:Feb 27 19:53:54 ubuntu kernel: [ 1151.451225] end_request: I/O error, dev sr0, sector 1050984
syslog:Feb 27 19:56:25 ubuntu kernel: [ 1302.583141] Sense Key : Medium Error [current] 
syslog:Feb 27 19:56:25 ubuntu kernel: [ 1302.583180] end_request: I/O error, dev sr0, sector 1125040
Xorg.0.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
ubuntu@ubuntu:/var/log$ 

```

---

### Post by ZootHornRollo on 2013-03-31
i also have issues with an NC6400 freezing and have stopped using ubuntu and other linux distros (back to XP!) after failing to find a linux OS that would run without these issues and/or one i could get along with.

OpenSuse worked, Fedora didn't.

Would be keen to find a solution if one exists.

p.s. i don't run eclipse.

---

