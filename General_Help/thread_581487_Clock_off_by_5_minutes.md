---
title: "Clock off by 5 minutes"
date: 2007-10-19
forum: General Help
---

### Post by sancho panza on 2007-10-19
I noticed today morning that my system clock is off by 5 mins(!) even though I have set the time to be synchronized with internet servers. I have not changed any settings or applied any updates in the past few days, and today is the first time I'm seeing this problem. The CMOS battery should not be the issue as this is a new machine. So what could be the problem?

Secondly, why does the clock settings not synchronize promptly when I select the option of internet servers?

---

### Post by pointone on 2007-10-19
Could be a problem with the NTP server you're trying to connect to.

The change isn't instant because the default behaviour is to slew the clock to the correct value (i.e., slow down or speed up the clock until it matches the server's time).

---

### Post by sancho panza on 2007-10-19
I have setup 3 ntp servers to synchronize with. And my other question was how the system lost 5 mins in the first place?

Thanks,

---

### Post by wastedfluid on 2007-10-19
You should remove all your servers and replace them with

us.pool.ntp.org

Or whatever country you're from.  

I wish I knew why certain computers do that.  Some of the vps machines I have lose 5-10 seconds a day by time.. and it adds up over a week, or two.

Best thing I can tell you is probably make a root crontab to ntpdate us.pool.ntp.org.. that's what I do on most of the computers where I have time issues.  

Is it a desktop?  Try replacing the CMOS battery.. try resetting BIOS.. that's all about all I know of to tell you.

---

### Post by tester321 on 2008-02-26
*I realize that this was posted some months ago now.*

Is there any more info on this?

It does NOT matter what NTP server in the World you try -- the time is always off by 5 minutes (in my case it is 5 minutes behind actual time).  And it is not a time creep problem (ie., the time stays rock solid accurate but just is always 5 minutes behind from the moment it talks to the NTP servers).

Gutsy Gibbon/7.10
Toshiba Satellite A135-S4527
(Pentium Dual Core)
All NTP servers (US Eastern Timezone), including us.pool.ntp.org

Numerous other PCs on the same network running same distro do not exhibit the same issue.

Thanks

---

### Post by ebelog on 2008-04-22
I recently had a similar issue on a fedora 6 machine, and it turned out that the time difference (3 minutes in my case) was beyond the threshold that ntp would correct. Even stopping and starting ntpd and rebooting the server didn't correct the issue. 

Here's what fixed it in my case:
1. stop the ntpd process
2. run "ntpd -q" which forces an immediate synchronization of the current time
3. restart the ntpd process.

---

### Post by tester321 on 2008-04-25
ebelog, you are a genius :popcorn: -- this worked perfectly to correct the problem!  Still scratching my head over this because I just thought NTP would correct any time gap -- guess I was wrong.

Thank you!

> **ebelog said:**
> I recently had a similar issue on a fedora 6 machine, and it turned out that the time difference (3 minutes in my case) was beyond the threshold that ntp would correct. Even stopping and starting ntpd and rebooting the server didn't correct the issue. 

Here's what fixed it in my case:
1. stop the ntpd process
2. run "ntpd -q" which forces an immediate synchronization of the current time
3. restart the ntpd process.

---

