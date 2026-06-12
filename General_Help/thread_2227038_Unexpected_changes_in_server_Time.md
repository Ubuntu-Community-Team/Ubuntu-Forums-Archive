---
title: "Unexpected changes in server Time"
date: 2014-05-30
forum: General Help
---

### Post by vivek15 on 2014-05-30
Team ,

             Here i am using Ubuntu 12.04 LTS. It is in EST Time Zone . NTP is not configured on this server because of time sync error with apache and my customized application.

We had an unexpected time changes in our server . the time has rolled one hour back.  we cant able to find the reason .

Where can i get the log for this time changes ?

What is the reason for this automatic time change ?


Thanks

Vivek Kannan

---

### Post by tgalati4 on 2014-05-30
Have you performed updates on this computer in the past 6 months?  It sounds like a Daylight Savings Time change.  Each location has a slightly different time of the year when this occurs and the updates typically affect the timezone file.

It's hard to imagine why ntp would interfere with a web application.  ntp is used to keep servers syncronized so that web applications display the correct time.

Log files are in /var/log, but if a computer was rebooted, the time will get set from the real time clock (rtc) and there may be a problem with your computer's rtc.

---

