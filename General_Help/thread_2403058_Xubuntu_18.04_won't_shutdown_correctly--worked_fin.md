---
title: "Xubuntu 18.04 won't shutdown correctly--worked fine under 16.04"
date: 2018-10-07
forum: General Help
---

### Post by Ralph L on 2018-10-07
I installed a new disk partition and put xubuntu 18.04 on it.  I kept my 16.04 and my 14.04.  When I select Reboot or Shutdown from the menu, the system hangs. My log is very similar to the one in [https://www.queryxchange.com/q/3_1080529/ubuntu-18-04-hangs-on-shutdown-or-restart/](https://www.queryxchange.com/q/3_1080529/ubuntu-18-04-hangs-on-shutdown-or-restart/) with the last two items being:```
Reached target Final Step.
Starting Power-Off...
```I did not have this problem on xubuntu 14.04 and 16.04.  The computer also will not resume from a suspend (started by closing the lid), when the lid is opened.  Resume worked fine under 14.04 and under 16.04 until some update in the past 6 months or so.  I am very suspicious that my problem is caused by an update to make uefi work, since I have an old bios.
My hardware is an old computer Toshiba Satellite A215-S4697. I tried a lot of suggestions by other people who have had shutdown hangs, but none of them worked for me.
Any help is appreciated. I really don't want to go back to Xubuntu 14.04.

Note:  This problem (and the "unable to resume with lid opening problem" were solved by installing Kernel 4.4.97 into Xubuntu 18.04 using Uukk from ppa:teejee2008/ppa.  Surprisingly, everything seems to run.  There may be a somewhat newer Kernel that will still work, but I haven't searched for it yet.

---

