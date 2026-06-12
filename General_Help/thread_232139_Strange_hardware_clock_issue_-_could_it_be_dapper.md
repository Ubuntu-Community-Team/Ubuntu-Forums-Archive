---
title: "Strange hardware clock issue - could it be dapper?"
date: 2006-08-08
forum: General Help
---

### Post by scubasau on 2006-08-08
I very recently built a new system (amd4600x2 - dapper - custom 2.6.16-ck12 kernel (32bit)) and have been experiencing some strange behavior w/ my BIOS clock: every once in a while the system will alert me that the date/time is not set after it posts - whcih I then set back to the proper UTC time.

My first thought was a bad CMOS battery which i promptly replaced. No luck. In hindsight, this probably wasn't a possibility since 1) the power-supply was plugged in and 2) no other BIOS settings are ever lost - just the date time which is reset to 1/1/2002.

After some googling and forum searching, I found a [thread]("http://www.ubuntuforums.org/showthread.php?t=149565") discussing a similar issue where the problem was corrected with the '--directisa' parameter passed to hwclock. I tried this, but the issue continued. (I've since removed this parameter.)

Next, i looked at the hwclock init script (/etc/init.d/hwclock.sh) and saw that if it finds some invalid parameter, it sets the date to 1/1/2002. This got my hopes up, but this logic in the 'start' case and I've never seen KDE show me a date of 1/1/2002; plus if it sync'd correctly at shutdown, the motherboard shouldn't think the date/time needs setting (or maybe it thinks any date before the BIOS timestamp is invalid? Mobo is an MSI K9N Platinum)

So I added some (hacky) debugging output to hwclock.sh last night to capture the actual syncs: gave the hwclock the --debug param and sent its output to /var/log/hwclock.log. This morning when I powered up (didn't check bios time) - the debugging output reported grabbing a BIOS date of *April* 8, 2006 with the correct time. The previous log entry though shows a correct sync of *August* 8 to the BIOS from the kernel.

My next plan is to remove the CMOS battery and unplug the system to see what the BIOS resets the date to. If it's something other than 1/1/2002, I can be fairly certain this is hwclock; if it is 1/1/2002, I'll change the hwclock script to use a different distinguishable date.

Does anyone have any other suggestions? Thanks for reading this long-winded support request! :)

---

